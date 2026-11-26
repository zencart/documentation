---
title: Cloudflare Transition 
description: Steps to move your Zen Cart to Cloudflare 
category: security
weight: 10
---

This is a store owner's guide to putting Zen Cart behind Cloudflare, from signup and basic settings through the rules that stop bots, card testers, and scanners.  If you are unfamiliar with Cloudflare, please read [Cloudflare Pros and Cons](/user/security/cloudflare) first.

Written for Zen Cart 1.5.8 through 3.0.0 on a typical cPanel/Apache or LiteSpeed host. Last reviewed 2026-09-14.

> **About Cloudflare menu names and plan limits.** Cloudflare renames and rearranges its dashboard often (Page Rules became Cache/Configuration/Redirect Rules, "WAF" is turning into "Security rules", Auto Minify was removed). If a menu name here doesn't match what you see, search the dashboard for the setting name. Plan limits change too, so check the numbers in the rule editor before you design around them. The plan limits, bot behavior, rate-limiting fields, leaked-credential fields, Configuration Rule settings, and Cloudflare IP ranges in this guide were checked against Cloudflare's own docs and IP pages on 2026-09-14.

Throughout this guide:

| Placeholder | Replace with |
|---|---|
| `example.com` / `www.example.com` | your store's domain |
| `ADMIN_DIR` | your renamed Zen Cart admin folder |
| `ORIGIN_IP` | your hosting server's IP address |
| paths starting with `/` | if the store lives in a subfolder (`/shop/`), put that prefix in front of every path |

---

## Contents

1. Before you start
2. Pick a plan
3. Add the site and review DNS
4. Switch nameservers
5. SSL/TLS settings
6. Zen Cart changes
7. Get the visitor's real IP into Zen Cart (don't skip this)
8. Speed and caching settings that are safe for a store
9. Lock down the origin server
10. Security baseline
11. Bot settings
12. Custom rules for Zen Cart
13. Rate limiting: card testing, credential stuffing, form spam
14. Protecting the admin
15. Payment callbacks and webhooks
16. Testing checklist
17. Ongoing maintenance
18. When you're under attack
19. Troubleshooting
20. Quick reference

---

## 1. Before you start

Gather all of this before you touch anything. Most Cloudflare problems on Zen Cart come from something on this list being missed.

- [ ] **A full backup.** Files and database, downloaded off the server.
- [ ] **Registrar login.** You'll change nameservers there, and possibly DNSSEC.
- [ ] **Hosting control panel login** (cPanel/WHM, Plesk, etc.).
- [ ] **A copy of your current DNS zone.** Export it from cPanel → Zone Editor, or screenshot every record. Cloudflare's import scan misses records.
- [ ] **Zen Cart version.** Look at `includes/version.php`. Section 7 depends on it.
- [ ] **Admin folder name.** It's `DIR_WS_ADMIN` in `admin/includes/configure.php`.
- [ ] **Every inbound callback URL** your payment and shipping modules use (PayPal IPN, PayPal webhooks, Square, Stripe, Authorize.Net, and so on). Section 15.
- [ ] **Every automated thing that calls your site:** cron jobs that hit URLs, Google Merchant or marketplace feeds, uptime monitors, sitemap pingers.
- [ ] **A working SSL certificate on the server itself** (AutoSSL / Let's Encrypt is fine). Check with `https://ORIGIN_IP`-style testing in section 16, or just confirm the padlock works today.
- [ ] **A quiet time window.** Do the nameserver switch when orders are lowest.

---

## 2. Pick a plan

| Feature | Free | Pro | Business |
|---|---|---|---|
| Proxy, CDN, automatic DDoS protection | Yes | Yes | Yes |
| Universal SSL, Full (strict), Authenticated Origin Pulls | Yes | Yes | Yes |
| WAF custom rules | 5 | 20 | 100 |
| Rate limiting rules | 1 (10-second window, 10-second block, matches on **path only**) | 2 (up to 1-minute window, 1-hour block, matches on path and query but **not** method) | 5 (up to 10-minute window, 1-day block, adds method, source IP, user agent) |
| Managed rulesets | Free Managed Ruleset | + Cloudflare Managed Ruleset + OWASP Core Ruleset | same |
| Bot protection | Bot Fight Mode (can't be skipped by rules) | Super Bot Fight Mode (can be skipped) | + "likely automated" tier |
| Regex (`matches`) in rules | No | No | Yes |
| Log action in custom rules | No | No | No (Enterprise only) |
| Leaked-credential rule fields | password leaked | + username-and-password pair leaked | same |
| Zero Trust Access (admin login gate) | Free up to 50 users | same | same |
| Turnstile (CAPTCHA replacement) | Free | Free | Free |

**Recommendation:** a store taking real money should be on **Pro**. The two things that matter most for Zen Cart are the Cloudflare Managed Ruleset and Super Bot Fight Mode, because Free's Bot Fight Mode can't be exempted for your payment callbacks (section 11). Free works, and everything below has a Free-plan path, but you'll have fewer rules to work with.

---

## 3. Add the site and review DNS

1. Sign up at cloudflare.com, then **Add a domain** and enter the bare domain (`example.com`, not `www`).
2. Choose the plan.
3. Let Cloudflare scan DNS. **Don't trust the scan.** Compare it line by line with the zone you exported and add anything missing.

### Proxied (orange cloud) vs DNS only (gray cloud)

| Record | Proxy status | Why |
|---|---|---|
| `example.com` (A/AAAA) | **Proxied** | the store |
| `www` (A/CNAME) | **Proxied** | the store |
| `mail`, `smtp`, `imap`, `pop` | **DNS only** | Cloudflare doesn't proxy mail |
| `MX` records | n/a (can't be proxied) | point them at a DNS-only hostname |
| `webmail`, `cpanel`, `whm`, `webdisk`, `cpcalendars`, `cpcontacts`, `autodiscover`, `autoconfig` | **DNS only** | control panel ports don't pass through the proxy |
| `ftp`, `ssh` | **DNS only** | not HTTP |
| TXT (SPF, DKIM, DMARC, verification) | n/a | copy exactly |
| CAA | n/a | see below |

> **Heads-up about DNS-only records:** any gray-cloud record that points at `ORIGIN_IP` tells the world your server's real address. On shared hosting that's unavoidable for mail. It's why section 9 (origin lockdown) matters.

**SPF records:** check your SPF TXT record for `a` or `mx` mechanisms (for example `v=spf1 a mx include:... ~all`). Once the store's A record is proxied, `a` resolves to Cloudflare's IPs instead of your server, so order confirmations and other mail sent by Zen Cart fail SPF and go to spam. Replace `a` with your server's address explicitly (`ip4:ORIGIN_IP`, plus `ip6:` if the server sends over IPv6). `mx` is fine as long as the MX hostname is DNS only. This does publish `ORIGIN_IP`, which is one more reason for section 9.

**CAA records:** if your zone has CAA records, they must allow the certificate authorities Cloudflare uses, or Cloudflare can't issue your edge certificate. Cloudflare adds the needed CAA entries automatically when Universal SSL is on, but check they survived if you edit CAA by hand later.

---

## 4. Switch nameservers

> **Don't switch yet.** Cloudflare lets you configure a site while it is still pending, before any traffic flows through it. Complete **sections 5 through 8 first**, then come back here. If you switch first, every order placed until section 7 is done reaches your payment gateway with a Cloudflare IP, and gateway velocity filters (which count orders per IP) can start holding or declining real customers because they appear to share a handful of addresses. Paid downloads can also be cached before the section 8.3 bypass exists.
>
> The section 7 server and PHP changes are safe to install before the switch: they only trust forwarded headers from Cloudflare's own IP ranges, so direct traffic is unaffected. Section 9 is the exception. Options A and B refuse non-Cloudflare traffic, so do them **after** the site is active.

1. **DNSSEC first.** If DNSSEC is on at your registrar, **turn it off** and wait for the DS record to expire (up to 24–48 hours). Switching nameservers with DNSSEC still on takes the whole domain offline.
2. At the registrar, replace the nameservers with the two Cloudflare gives you.
3. Wait for Cloudflare to email "your site is active" (often minutes, sometimes hours).
4. Once active, go to **DNS → Settings → DNSSEC**, enable it, and add the DS record Cloudflare shows you at the registrar.

Check propagation:

```bash
nslookup -type=NS example.com
```

---

## 5. SSL/TLS settings

Go to **SSL/TLS**.

| Setting | Value | Notes |
|---|---|---|
| Encryption mode | **Full (strict)** | If the dashboard offers "Automatic", switch to Custom → Full (strict). **Never use Flexible with Zen Cart** (see below). |
| Edge Certificates → Always Use HTTPS | **On** | |
| Edge Certificates → Minimum TLS Version | **TLS 1.2** | |
| Edge Certificates → TLS 1.3 | **On** | |
| Edge Certificates → Automatic HTTPS Rewrites | **On** | fixes stray `http://` image links in old product descriptions |
| Edge Certificates → Opportunistic Encryption | On | |
| Edge Certificates → HSTS | **Wait a week**, then On | see below |
| Origin Server → Authenticated Origin Pulls | see section 9 | |

**Why not Flexible:** in Flexible mode Cloudflare talks to your server over plain HTTP. Most hosts (and many `.htaccess` files) redirect HTTP to HTTPS, so the server sends the request back to HTTPS, Cloudflare fetches over HTTP again, and you get `ERR_TOO_MANY_REDIRECTS`. Even without a loop, everything a customer submits, including login passwords and checkout forms, travels unencrypted between Cloudflare and your server. Full (strict) avoids both.

**Origin certificate choice:**

- **Keep your host's AutoSSL / Let's Encrypt certificate** (recommended). It's publicly trusted, so if you ever gray-cloud the site in an emergency, visitors don't get certificate errors. AutoSSL renewals work through the proxy.
- **Or install a Cloudflare Origin CA certificate** (SSL/TLS → Origin Server → Create Certificate, valid up to 15 years). It's only trusted by Cloudflare, so turning the proxy off breaks HTTPS for visitors.

**HSTS:** only turn it on after a week of everything working over HTTPS.

- Max-Age: start at 6 months.
- Include subdomains: **only** if every subdomain (`webmail`, `cpanel`, `mail`, etc.) serves valid HTTPS.
- Preload: skip it unless you're sure. It's very hard to undo.

---

## 6. Zen Cart changes

### 6.1 configure.php files

Make both files writable, edit, then set them back to read-only (444).

`includes/configure.php`:

```php
define('HTTP_SERVER', 'https://www.example.com');
define('HTTPS_SERVER', 'https://www.example.com');
define('ENABLE_SSL', 'true');
```

`ADMIN_DIR/includes/configure.php`:

```php
define('HTTP_SERVER', 'https://www.example.com');
define('HTTP_CATALOG_SERVER', 'https://www.example.com');
define('HTTPS_CATALOG_SERVER', 'https://www.example.com');
define('ENABLE_SSL_CATALOG', 'true');
```

Pick **one** hostname (`www` or bare) and use it everywhere. Section 8.4 redirects the other one to it.

### 6.2 Admin settings

**Configuration → Sessions**

| Setting | Value | Why |
|---|---|---|
| Check IP Address | **False** | mobile shoppers change IPs mid-session; true logs people out at checkout |
| Check User Agent | False | |
| Prevent Spider Sessions | **True** | bots don't get sessions or carts |
| Recreate Session | **True** | new session ID at login (session-fixation protection) |
| IP to Host Conversion Status | false | a reverse DNS lookup on every new session slows the first page load and adds nothing behind a proxy |

**Configuration → Website Maintenance → Down For Maintenance (exclude this IP-Address)**

This compares against the visitor's IP. Until section 7 is done, Zen Cart sees a Cloudflare IP instead of yours, so this setting won't recognize you. Fix section 7 first, then enter your IP.


---

## 7. Get the visitor's real IP into Zen Cart (don't skip this)

Behind Cloudflare, every request reaches your server from a Cloudflare IP. Zen Cart uses the visitor IP in lots of places:

- the IP address saved on every order
- the customer IP sent to your payment gateway's fraud filter (a Cloudflare IP makes the filter useless)
- Who's Online
- the maintenance-mode exclusion
- IP-based blocks in plugins
- your server's own logs and firewall

### 7.1 The trap in Zen Cart 1.5.8 – 2.2.x

In these versions, `zen_get_ip_address()` (in `includes/functions/functions_traffic.php`) reads the **leftmost** value of the `X-Forwarded-For` header before it ever looks at the real connection address.

Cloudflare **adds** the visitor's IP to the end of any `X-Forwarded-For` header the visitor sent, and keeps whatever they sent at the front. So anyone can send `X-Forwarded-For: 1.2.3.4` and Zen Cart records `1.2.3.4` as their address on orders, in fraud checks, and in logs.

Fixing this takes two steps:

1. **Restore the real IP at the server level** (section 7.2).
2. **Stop Zen Cart from trusting forwarded headers** (section 7.3), or on newer versions, configure `TRUSTED_PROXIES` (section 7.4).

### 7.2 Server level: restore REMOTE_ADDR

Do whichever matches your server. All three check that the request really came from Cloudflare before trusting the header.

**Apache with mod_remoteip** (WHM → EasyApache 4 → enable `mod_remoteip`, then add to a global include such as *Apache Configuration → Include Editor → Pre VirtualHost Include*):

```apache
RemoteIPHeader CF-Connecting-IP
# Current list: https://www.cloudflare.com/ips/
RemoteIPTrustedProxy 173.245.48.0/20
RemoteIPTrustedProxy 103.21.244.0/22
RemoteIPTrustedProxy 103.22.200.0/22
RemoteIPTrustedProxy 103.31.4.0/22
RemoteIPTrustedProxy 141.101.64.0/18
RemoteIPTrustedProxy 108.162.192.0/18
RemoteIPTrustedProxy 190.93.240.0/20
RemoteIPTrustedProxy 188.114.96.0/20
RemoteIPTrustedProxy 197.234.240.0/22
RemoteIPTrustedProxy 198.41.128.0/17
RemoteIPTrustedProxy 162.158.0.0/15
RemoteIPTrustedProxy 104.16.0.0/13
RemoteIPTrustedProxy 104.24.0.0/14
RemoteIPTrustedProxy 172.64.0.0/13
RemoteIPTrustedProxy 131.0.72.0/22
RemoteIPTrustedProxy 2400:cb00::/32
RemoteIPTrustedProxy 2606:4700::/32
RemoteIPTrustedProxy 2803:f800::/32
RemoteIPTrustedProxy 2405:b500::/32
RemoteIPTrustedProxy 2405:8100::/32
RemoteIPTrustedProxy 2a06:98c0::/29
RemoteIPTrustedProxy 2c0f:f248::/32
```

> Check that list against https://www.cloudflare.com/ips/ before you paste it, and again every few months.

Also change the access log format to use `%a` instead of `%h` so your logs show real visitor IPs.

**LiteSpeed:** WebAdmin → Server → General → **Use Client IP in Header: Trusted IP Only**, and add the Cloudflare ranges to the trusted list (Security → Access Control → Allowed List, marked with a trailing `T`). Many LiteSpeed hosts already ship with Cloudflare trusted, so ask your host.

**nginx:**

```nginx
real_ip_header CF-Connecting-IP;
set_real_ip_from 173.245.48.0/20;
# ...one set_real_ip_from line per Cloudflare range...
```

**Shared hosting where you can't change the server:** ask your host to enable Cloudflare real-IP restoration. Most will. If they won't, use the PHP alternative at the end of 7.3.

### 7.3 Zen Cart 1.5.8 – 2.2.x: stop trusting forwarded headers

Once REMOTE_ADDR is correct, remove the headers visitors can fake so Zen Cart falls through to REMOTE_ADDR. Zen Cart loads `extra_configures` files before it works out the IP, in both the storefront and the admin.

Create **`includes/extra_configures/cloudflare_real_ip.php`**:

```php
<?php
/**
 * The server has already restored REMOTE_ADDR from Cloudflare (mod_remoteip / LiteSpeed / nginx),
 * so drop the client-suppliable forwarded headers that zen_get_ip_address() would otherwise
 * trust ahead of REMOTE_ADDR.
 */
foreach (['HTTP_X_FORWARDED_FOR', 'HTTP_CLIENT_IP', 'HTTP_X_FORWARDED', 'HTTP_X_CLUSTER_CLIENT_IP', 'HTTP_FORWARDED_FOR', 'HTTP_FORWARDED'] as $cfHeader) {
    unset($_SERVER[$cfHeader]);
}
unset($cfHeader);
```

Copy the same file to **`ADMIN_DIR/includes/extra_configures/cloudflare_real_ip.php`**.

**PHP-only alternative (no server access).** Use this **instead of** the file above. It checks that the request came from a Cloudflare range before it trusts `CF-Connecting-IP`:

```php
<?php
/**
 * No server-level real-IP support: trust CF-Connecting-IP only when the TCP peer is Cloudflare.
 * Keep $cfRanges in step with https://www.cloudflare.com/ips/
 */
if (!function_exists('cf_ip_in_cidr')) {
    function cf_ip_in_cidr(string $ip, string $cidr): bool
    {
        [$subnet, $bits] = explode('/', $cidr);
        $ipBin = @inet_pton($ip);
        $subnetBin = @inet_pton($subnet);
        if ($ipBin === false || $subnetBin === false || strlen($ipBin) !== strlen($subnetBin)) {
            return false;
        }
        $bytes = intdiv((int)$bits, 8);
        $remainder = (int)$bits % 8;
        if ($bytes > 0 && strncmp($ipBin, $subnetBin, $bytes) !== 0) {
            return false;
        }
        if ($remainder === 0) {
            return true;
        }
        $mask = chr((0xFF << (8 - $remainder)) & 0xFF);
        return ($ipBin[$bytes] & $mask) === ($subnetBin[$bytes] & $mask);
    }
}

$cfRanges = [
    '173.245.48.0/20', '103.21.244.0/22', '103.22.200.0/22', '103.31.4.0/22', '141.101.64.0/18',
    '108.162.192.0/18', '190.93.240.0/20', '188.114.96.0/20', '197.234.240.0/22', '198.41.128.0/17',
    '162.158.0.0/15', '104.16.0.0/13', '104.24.0.0/14', '172.64.0.0/13', '131.0.72.0/22',
    '2400:cb00::/32', '2606:4700::/32', '2803:f800::/32', '2405:b500::/32', '2405:8100::/32',
    '2a06:98c0::/29', '2c0f:f248::/32',
];

$cfPeer = $_SERVER['REMOTE_ADDR'] ?? '';
$cfFromCloudflare = false;
foreach ($cfRanges as $cfRange) {
    if (cf_ip_in_cidr($cfPeer, $cfRange)) {
        $cfFromCloudflare = true;
        break;
    }
}

foreach (['HTTP_X_FORWARDED_FOR', 'HTTP_CLIENT_IP', 'HTTP_X_FORWARDED', 'HTTP_X_CLUSTER_CLIENT_IP', 'HTTP_FORWARDED_FOR', 'HTTP_FORWARDED'] as $cfHeader) {
    unset($_SERVER[$cfHeader]);
}
if ($cfFromCloudflare && filter_var($_SERVER['HTTP_CF_CONNECTING_IP'] ?? '', FILTER_VALIDATE_IP)) {
    $_SERVER['REMOTE_ADDR'] = $_SERVER['HTTP_CF_CONNECTING_IP'];
}
unset($cfRanges, $cfPeer, $cfFromCloudflare, $cfRange, $cfHeader);
```

The PHP version only fixes Zen Cart. Your server logs and firewall will still see Cloudflare IPs.

### 7.4 Zen Cart builds with `TRUSTED_PROXIES`

Newer Zen Cart code (the 2.3.0 line and 3.0.0) adds a `TRUSTED_PROXIES` setting to `configure.php` and reads forwarded headers only when the connection really comes from a listed proxy, working from the right-hand (trusted) end of the header. To check whether yours has it, search `includes/dist-configure.php` for `TRUSTED_PROXIES`.

- **If the server restores REMOTE_ADDR (7.2):** leave `TRUSTED_PROXIES` empty. Zen Cart already sees the real IP. **Don't** add the 7.3 file.
- **If it doesn't:** list the Cloudflare ranges in **both** configure.php files:

```php
define('TRUSTED_PROXIES', [
    '173.245.48.0/20', '103.21.244.0/22', '103.22.200.0/22', '103.31.4.0/22', '141.101.64.0/18',
    '108.162.192.0/18', '190.93.240.0/20', '188.114.96.0/20', '197.234.240.0/22', '198.41.128.0/17',
    '162.158.0.0/15', '104.16.0.0/13', '104.24.0.0/14', '172.64.0.0/13', '131.0.72.0/22',
    '2400:cb00::/32', '2606:4700::/32', '2803:f800::/32', '2405:b500::/32', '2405:8100::/32',
    '2a06:98c0::/29', '2c0f:f248::/32',
]);
```

Section 16 includes a test that confirms the spoofing trick no longer works.

---

## 8. Speed and caching settings that are safe for a store

### 8.1 The golden rule

**Never cache Zen Cart's HTML pages.** Carts, account pages, prices for logged-in wholesale customers, and checkout are all built per visitor. Cloudflare doesn't cache HTML by default, so the danger is someone later adding a "Cache Everything" rule. Section 8.3 adds a bypass rule to guard against that.

### 8.2 Speed settings

| Setting | Value | Why |
|---|---|---|
| **Rocket Loader** | **Off** | rewrites script loading; breaks jQuery-dependent attribute pricing, checkout, and on-page payment forms (Square, Stripe, Accept.js, PayPal buttons) |
| Email Address Obfuscation (Scrape Shield) | Off, or off for the admin via a Configuration Rule | can mangle addresses in admin customer and order screens |
| Brotli / HTTP/2 / HTTP/3 | On | |
| 0-RTT Connection Resumption | Off | small gain, replay risk |
| Early Hints | On (fine) | |
| Polish (Pro) | Lossless or Lossy, WebP on | shrinks product images without touching Zen Cart |
| Mirage, Auto Minify | gone | Cloudflare retired them |
| Always Online | **Off** | shows old archived pages (old prices, sold-out items) when your server is down |
| Speed Brain | default | turn it off if you see odd cart or logoff behavior |
| Hotlink Protection | Optional | turn it off if marketplaces or feeds pull your product images |
| Browser Integrity Check | On (turn it off for webhooks, see 15) | |

### 8.3 Cache Rules (Caching → Cache Rules)

> **Order matters, and it's the opposite of custom rules.** Cache Rules stack: when several match the same request, Cloudflare applies all of them, and where they conflict the **later** rule wins. The bypass rule must therefore come **last**, or a `.png` in `/pub/` or a `.js` file in the admin would match the bypass and then be made cacheable again by a later rule.

**Rule A: Cache static assets longer**

```
(http.request.uri.path.extension in {"jpg" "jpeg" "png" "gif" "webp" "avif" "svg" "ico" "woff" "woff2"})
```

Action: Eligible for cache. Edge TTL: 1 month. Browser TTL: 1 week.

**Rule B: CSS and JavaScript**

```
(http.request.uri.path.extension in {"css" "js"})
```

Action: Eligible for cache. Edge TTL: 1 day. Browser TTL: 4 hours. Zen Cart templates don't add version numbers to CSS/JS filenames, so after editing the template, **purge** (Caching → Configuration → Custom Purge → by URL) and hard-refresh.

> When you replace a product image with a file of the **same name**, purge that URL. Purging clears Cloudflare's copy, but shoppers who already viewed the image keep it in their browser for up to a week (the Browser TTL above). If an image change must show immediately, upload it under a new filename.

**Rule C: Bypass cache for dynamic and private paths** (put it **last**)

```
(starts_with(http.request.uri.path, "/ADMIN_DIR"))
or (starts_with(http.request.uri.path, "/pub/"))
or (starts_with(http.request.uri.path, "/download/"))
or (http.request.uri.path eq "/ajax.php")
or (http.request.uri.path eq "/ipn_main_handler.php")
or (http.request.uri.path eq "/ppr_webhook.php")
```

Action: **Bypass cache**. When you create it, use the **Place at** dropdown to put it after Rules A and B, then check that it sits at the bottom of the Cache Rules list.

> **Why `/pub/` matters:** with *Download by Redirect* turned on, Zen Cart creates a temporary link in `/pub/` for each paid download. Cloudflare caches `.zip`, `.pdf`, `.mp3`, `.mp4` and similar files **by default** based on the file extension. Without this bypass, a customer's paid file can stay in Cloudflare's cache after Zen Cart deletes the temporary link, and anyone who has the URL can still download it.

If you add more Cache Rules later, keep this one at the bottom of the list.

### 8.4 Redirect Rules (Rules → Redirect Rules)

Send the bare domain to `www` (or the other way around), matching `configure.php`:

- When: Hostname equals `example.com`
- Then: Dynamic redirect, `concat("https://www.example.com", http.request.uri.path)`, status **301**, **preserve query string** checked

### 8.5 Configuration Rules (Rules → Configuration Rules)

**Admin:** `starts_with(http.request.uri.path, "/ADMIN_DIR")` → Rocket Loader Off, Email Obfuscation Off.

The webhook configuration rule is in section 15.

---

## 9. Lock down the origin server

Cloudflare only protects traffic that goes **through** it. If a bot finds `ORIGIN_IP`, it can skip every rule in this guide. Your IP leaks through mail records, email headers, SPF records, old DNS history sites, and gray-cloud subdomains, so assume it's known.

Do this section **after** Cloudflare shows the site as active. Options A and B refuse traffic that doesn't come through Cloudflare, so turning them on before the nameserver switch takes the store offline.

Pick at least one of these:

### Option A: Authenticated Origin Pulls (any plan, good for VPS/dedicated)

Cloudflare presents a client certificate on every connection, and your server refuses connections without it.

1. SSL/TLS → Origin Server → **Authenticated Origin Pulls: On** (zone-level).
2. Download Cloudflare's origin-pull CA certificate (linked from that page) to the server.
3. In the store's SSL virtual host (on cPanel, a userdata include such as `/etc/apache2/conf.d/userdata/ssl/2_4/USER/example.com/cf-aop.conf`):

```apache
SSLVerifyClient require
SSLVerifyDepth 1
SSLCACertificateFile /etc/ssl/cloudflare/authenticated_origin_pull_ca.pem
```

4. Rebuild the config and restart Apache. Direct HTTPS hits to the origin now fail the TLS handshake.

> This is per-vhost, so AutoSSL for gray-cloud subdomains keeps working. **Turn it off before** you ever gray-cloud the store.

### Option B: Firewall to Cloudflare ranges (VPS/dedicated)

Allow ports 80/443 **only** from Cloudflare's ranges plus your own IP. Keep SSH and control-panel ports as they are.

> On cPanel servers this blocks AutoSSL validation for gray-cloud names on the same IP (`mail.`, `cpanel.`) and breaks any other non-Cloudflare sites on the server. Option A avoids that.

### Option C: Cloudflare Tunnel

Run `cloudflared` on the server and close inbound 80/443 entirely. It's the strongest option but needs root and changes how the site is routed. Best suited to a VPS dedicated to the store.

### Shared hosting

You usually can't do A–C yourself. Ask your host whether they support Authenticated Origin Pulls or Cloudflare-only access. At minimum, do section 7 so a direct hit can't fake an IP.

---

## 10. Security baseline

**Security → Settings**

| Setting | Value |
|---|---|
| Security Level | nothing to set. Cloudflare retired Low/Medium/High; the old dashboard shows "Always protected" and the only remaining choice is Under Attack mode on or off. Leave it **off** except during an attack (section 18). |
| Challenge Passage | **30 minutes** (lets a shopper finish checkout without a second challenge) |
| Browser Integrity Check | On |
| Leaked Credentials Detection | **On** (flags logins using known-breached passwords; see 13.3) |
| HTTP DDoS attack protection | On by default, leave at defaults |

> Don't build rules on threat score (`cf.threat_score`). Cloudflare stopped filling it in, so it's always 0, and old forum advice that uses it does nothing.

**Managed rules** (Security → WAF → Managed rules)

- **Free:** the Free Managed Ruleset is on automatically. Leave it on.
- **Pro and up:**
  - **Cloudflare Managed Ruleset: Enable.**
  - **Cloudflare OWASP Core Ruleset: Enable, carefully.**
    - Paranoia level **PL1**.
    - Anomaly score threshold **Medium (40)** or **High (25)** only after a week of clean logs.
    - If your plan offers a **Log** action for the ruleset, run it in Log for the first week.
    - The OWASP ruleset **will** flag admin pages, because saving a product description, EZ-Page, or Define Page full of HTML looks like cross-site scripting. Section 14 exempts the admin for your own IPs.

---

## 11. Bot settings

**Security → Settings**, filtered by **Bot traffic** (older dashboards: Security → Bots)

### Free plan: Bot Fight Mode

- It **can't be skipped** by any rule. If it challenges your payment provider's server-to-server calls (PayPal IPN, webhooks) or your feed fetchers, those calls fail silently.
- **Recommendation:** turn it **On**, then check PayPal's IPN History and every gateway's webhook delivery log within 24 hours. If anything fails, **turn Bot Fight Mode off** and rely on the custom rules in section 12 instead.

### Pro plan: Super Bot Fight Mode

If you're upgrading from Free, turn Bot Fight Mode **off** first.

| Setting | Value |
|---|---|
| Definitely automated | **Managed Challenge** (move to Block after a clean week) |
| Likely automated (Business+) | Managed Challenge |
| Verified bots | **Allow** (Googlebot, Bingbot, Google Merchant, and similar) |
| Static resource protection | Off (don't challenge images and CSS) |
| JavaScript detections | On |

Skip it for webhooks with the rule in section 12 (Rule 1).

### AI crawlers

Security → Bots (or **AI Crawl Control**) offers **Block AI bots** and a managed `robots.txt`. It's a business choice:

- **Allow** if you want AI shopping assistants and answer engines to find and recommend your products.
- **Block** if you don't want your catalog used for AI training, or crawlers are eating server resources.

A middle path is to allow search/assistant crawlers and block training-only crawlers, if your dashboard lets you choose per crawler.

---

## 12. Custom rules for Zen Cart

**Security → WAF → Custom rules** (newer dashboard: **Security rules**). Rules run top to bottom, so **order matters**. These five fit the Free plan's limit. Paste each expression with **Edit expression**.

**Before you start:** create an IP list at **Manage Account → Configurations → Lists**, named `zc_admin_ips`, and add your office/home IPs.

### Rule 1: Skip trusted traffic (FIRST)

Lets payment callbacks and your own admin work through without being challenged or blocked.

```
(http.request.uri.path in {"/ipn_main_handler.php" "/ppr_webhook.php"})
or (starts_with(http.request.uri.path, "/ADMIN_DIR") and ip.src in $zc_admin_ips)
```

Action: **Skip**. Tick: *All remaining custom rules*, *Rate limiting rules*, *All managed rules*, and *Super Bot Fight Mode* (Pro). Turn on **Log matching requests** so you can audit it. Free-plan Bot Fight Mode runs outside the rules engine and ignores Skip entirely, so this rule can't protect callbacks from it (section 11).

Add the callback paths for any other payment or shipping module you use (section 15).

### Rule 2: Block the admin for everyone else

Skip this rule if you use Cloudflare Access (section 14.1) instead.

```
starts_with(http.request.uri.path, "/ADMIN_DIR") and not ip.src in $zc_admin_ips
```

Action: **Block**.

### Rule 3: Block scanners and junk probes

A Zen Cart store has no WordPress, no `.env`, and no reason to answer `PUT` or `DELETE`.

```
(starts_with(http.request.uri.path, "/wp-"))
or (http.request.uri.path contains "xmlrpc.php")
or (starts_with(http.request.uri.path, "/zc_install"))
or (starts_with(http.request.uri.path, "/extras/"))
or (starts_with(http.request.uri.path, "/not_for_release/"))
or (starts_with(http.request.uri.path, "/logs/"))
or (starts_with(http.request.uri.path, "/cache/"))
or (http.request.uri.path contains "/.git")
or (http.request.uri.path contains "/.env")
or (lower(http.request.uri.path) contains "phpmyadmin")
or (ends_with(lower(http.request.uri.path), ".sql"))
or (ends_with(lower(http.request.uri.path), ".bak"))
or (ends_with(lower(http.request.uri.path), ".old"))
or (ends_with(lower(http.request.uri.path), ".log"))
or (not http.request.method in {"GET" "HEAD" "POST" "OPTIONS"})
```

Action: **Block**.

> **Don't** block `/zc_plugins/`. Zen Cart 2.x serves plugin CSS, JavaScript, and images from there.

### Rule 4: Bad or empty user agents

```
(
  http.user_agent eq ""
  or lower(http.user_agent) contains "sqlmap"
  or lower(http.user_agent) contains "nikto"
  or lower(http.user_agent) contains "masscan"
  or lower(http.user_agent) contains "zgrab"
  or lower(http.user_agent) contains "nuclei"
  or lower(http.user_agent) contains "wpscan"
)
and not cf.client.bot
```

Action: **Block** (or Managed Challenge if you're cautious).

Rule 1 has already let webhooks through, so a payment server with a bare user agent isn't caught here.

### Rule 5: Challenge risky pages from countries you don't sell to

Don't geo-block the whole store. Search engines and legitimate travelers need it. Challenge only the pages bots abuse.

```
(ip.src.country in {"XX" "YY" "ZZ"})
and (
  http.request.uri.query contains "main_page=create_account"
  or http.request.uri.query contains "main_page=login"
  or http.request.uri.query contains "main_page=password_forgotten"
  or http.request.uri.query contains "main_page=contact_us"
  or http.request.uri.query contains "main_page=checkout"
)
and not cf.client.bot
```

Replace `XX YY ZZ` with two-letter country codes. Action: **Managed Challenge**.

Shoppers get challenged when they first open the page, so their form submission already carries the pass. Bots posting straight to the form fail.

> **SEO URL add-ons** (Ceon URI Mapping, Simple SEO URLs, etc.) change what the URL looks like, so `main_page=` may not appear. Match on your rewritten paths instead, and keep in mind that form **submissions** usually still post to `index.php?main_page=...`.

### Pro plan: extra rules worth adding

- **Hosting-provider traffic on sensitive pages.** Real shoppers rarely browse from data centers. Add `ip.src.asnum in {...}` (well-known cloud/VPS ASNs taken from your Security Events) to Rule 5's page list, with Managed Challenge.
- **Obvious spam in reviews and Ask a Question.** Challenge `main_page=product_reviews_write` and `main_page=ask_a_question` from outside your shipping countries.
- **Admin exposure alert.** A copy of Rule 2 with action **Log** isn't available below Enterprise, so review the Rule 2 block counts in Security Events instead.

---

## 13. Rate limiting: card testing, credential stuffing, form spam

**Card testing** is the attack most likely to cost a Zen Cart owner real money. Bots push hundreds of stolen cards through checkout, and your gateway charges a fee for every attempt and may shut your account down.

### 13.1 The rule (Security → WAF → Rate limiting rules)

**Pro plan.** Pro rate limiting can match on the query string but **not** on the request method, so this rule matches the exact URLs Zen Cart's forms submit to:

```
(http.request.uri.query contains "main_page=checkout_process")
or (http.request.uri.query contains "main_page=login" and http.request.uri.query contains "action=process")
or (http.request.uri.query contains "main_page=password_forgotten" and http.request.uri.query contains "action=process")
or (http.request.uri.query contains "main_page=contact_us" and http.request.uri.query contains "action=send")
or (http.request.uri.query contains "main_page=create_account")
```

- Characteristics: **IP** (the only choice below Business)
- Period: **1 minute** (Pro's maximum)
- Requests: **10**
- Action: **Managed Challenge** (or Block), duration **1 hour** (Pro's maximum)

Where those URLs come from (stock Zen Cart templates):

| Form | Submits to |
|---|---|
| Log in | `index.php?main_page=login&action=process` |
| Forgotten password | `index.php?main_page=password_forgotten&action=process` |
| Contact Us | `index.php?main_page=contact_us&action=send` |
| Create account | `index.php?main_page=create_account` (its `action=process` flag travels inside the form, not the URL, so this line also counts ordinary visits to the page; 10 a minute is still far more than a person does) |
| Place order | `index.php?main_page=checkout_process` |

If your template overrides any of these forms, view the page source and check the form's `action` URL.

**Business plan:** wrap the expression as `http.request.method eq "POST" and (...)` and stretch the period up to 10 minutes.

**Free plan:** the window is fixed at 10 seconds and the rule can only match on the **path**. Zen Cart pages are served from `/index.php` or the bare `/` (the home page and any `/?main_page=...` link), so match both:

- Expression: `http.request.uri.path in {"/" "/index.php"}`
- Rate: **30 requests per 10 seconds** per IP
- Action: Block, 10 seconds (Free's only duration)

Real shoppers never load 30 pages in 10 seconds (images and CSS are separate paths and don't count).

**Be clear about what this does and doesn't do.** It stops a single IP from flooding the store. It does **not** stop card testing: a bot submitting one card every few seconds never reaches 30 requests in 10 seconds, and card testers usually rotate IPs anyway. On Free, your real defenses against card testing are the gateway's fraud tools, Turnstile, and the Rule 5 challenge (section 13.2 and section 12). If you use an SEO URL add-on, your product and category pages have other paths and aren't counted at all. That's acceptable, because form submissions still post to `/index.php`.

### 13.2 Layers that aren't Cloudflare

Rate limiting slows card testers but won't stop a patient one on its own. Add these:

- **Gateway fraud tools:** Authorize.Net Advanced Fraud Detection Suite (velocity and hourly filters), Square risk settings, Stripe Radar. They only work well once section 7 is done, since they need the real shopper IP.
- **Turnstile** (free CAPTCHA replacement) on login, create account, contact, and checkout, through a Zen Cart plugin or template edit.
- **Zen Cart's built-in honeypot fields** on contact, create account, reviews, and ask-a-question. Keep them in any template overrides.
- **Minimum order amount** or disabling guest checkout during an attack.

### 13.3 Leaked credentials

With Leaked Credentials Detection on (section 10), Cloudflare checks login submissions against databases of breached credentials and fills in fields you can use in rules:

- `cf.waf.credential_check.password_leaked`: all plans
- `cf.waf.credential_check.username_and_password_leaked`: Pro and up

Cloudflare's scan recognizes WordPress, Magento, Joomla, Drupal and a few others by name, but **not Zen Cart**. For everything else it relies on generic login patterns. Before building a rule, watch Security → Analytics for a few days and confirm that posts to `main_page=login` actually show leaked-credential results.

If they do, this rule challenges likely credential stuffing:

```
http.request.uri.query contains "main_page=login"
and cf.waf.credential_check.username_and_password_leaked
```

Action: **Managed Challenge**. On Free, use `cf.waf.credential_check.password_leaked` instead. It also catches real customers who reuse old passwords, but a challenge only costs them a few seconds. Free's five custom rules are already used in section 12, so add it to Rule 5 with `or (...)`, since that rule is also a Managed Challenge.

---

## 14. Protecting the admin

Zen Cart's admin should never be reachable by the public. Use **both** layers:

1. A renamed admin folder (Zen Cart requires this) plus a strong password and Zen Cart's admin lockout.
2. **One** of the Cloudflare gates below.

### 14.1 Cloudflare Access (best, free up to 50 users)

Works even if your home IP changes.

1. Zero Trust → Access → Applications → **Add → Self-hosted**.
2. Domain: `www.example.com`, path `ADMIN_DIR`.
3. Policy: **Allow**, Include → Emails → your address(es).
4. Login method: **One-time PIN**, or Google/Microsoft if you use them.
5. Session duration: 24 hours.

Anyone opening `/ADMIN_DIR` now has to prove their email before Zen Cart's login page even loads. Test that in a private browser window before going on: you should get the Access login page, not Zen Cart's.

Then update the section 12 rules:

- **Delete Rule 2.** Access does its job.
- **Drop the IP condition from Rule 1's admin line.** The IP list is the thing Access replaces, and if you keep it, saving a product description from any other IP gets blocked by the managed rules (section 10). Change Rule 1 to:

```
(http.request.uri.path in {"/ipn_main_handler.php" "/ppr_webhook.php"})
or (starts_with(http.request.uri.path, "/ADMIN_DIR"))
```

This is safe **only because Access is in place**. A WAF Skip doesn't bypass Access, so a visitor who hasn't passed the Access login is still stopped before reaching Zen Cart. If you ever remove the Access application, put the `ip.src in $zc_admin_ips` condition and Rule 2 back first.

> Cron jobs that call admin URLs (currency updates, feed builders) get stopped by Access. Use an Access **service token**, or run them from the command line.

### 14.2 IP allow list (simpler)

Rules 1 and 2 in section 12. Update the `zc_admin_ips` list when your IP changes.

### 14.3 Long-running admin jobs

On Free and Pro, Cloudflare gives up waiting for your server after **100 seconds** and shows **Error 524**. Admin tasks that can run longer include database backups, big Easy Populate imports, image regeneration, and sitemap builds.

- Split imports into smaller files.
- Run backups from cPanel or cron, not the admin page.
- If you must, use a separate DNS-only admin hostname. That exposes `ORIGIN_IP`, so it's a last resort.

---

## 15. Payment callbacks and webhooks

Payment providers call your store **server to server**. No browser, often no normal user agent, and they can't solve challenges. If Cloudflare challenges them, orders go missing or never change status.

### 15.1 Know your callback URLs

| Module | Callback path (from store root) |
|---|---|
| PayPal Website Payments Standard / Express (IPN) | `/ipn_main_handler.php` |
| PayPal RESTful (Zen Cart 2.x) | `/ppr_webhook.php` |
| Square, Stripe, Authorize.Net, Braintree, shipping, and ERP plugins | check each module's docs or settings page, and the webhook list in each provider's dashboard |

Add every path to **Rule 1** (section 12) and to the rule below.

### 15.2 Configuration Rule for callbacks

Rules → Configuration Rules:

```
http.request.uri.path in {"/ipn_main_handler.php" "/ppr_webhook.php"}
```

Set:

- **Browser Integrity Check: Off**
- **I'm Under Attack: Off** (so turning on Under Attack mode during an attack doesn't break them)
- **Rocket Loader: Off**

These endpoints check each message with the provider themselves, so exempting them from Cloudflare's challenges is safe.

### 15.3 Verify

- **PayPal:** PayPal account → IPN History. Look for HTTP 200 on recent messages.
- **Everything else:** each provider's webhook or event delivery log.
- **Cloudflare:** Security → Events, filtered to the callback path. You should see only "Skip" actions.

---

## 16. Testing checklist

Do these right after activation and again after every rule change.

**Cloudflare is in front:**

```bash
curl -sI https://www.example.com/
```

Look for `server: cloudflare` and a `cf-ray` header.

**Redirects are clean (one hop to https://www...):**

```bash
curl -sIL http://example.com/
```

**Probes are blocked (expect 403):**

```bash
curl -s -o /dev/null -w "%{http_code}\n" https://www.example.com/wp-login.php
```

```bash
curl -s -o /dev/null -w "%{http_code}\n" https://www.example.com/zc_install/
```

**Paid-download paths aren't cached** (`cf-cache-status` should be `DYNAMIC` or `BYPASS`, never `MISS`, `HIT` or `EXPIRED`):

```bash
curl -sI https://www.example.com/pub/test.zip
```

```bash
curl -sI https://www.example.com/pub/test.png
```

The `.png` check also confirms the Cache Rules are in the right order. If it shows `MISS`, `HIT` or `EXPIRED`, Rule A is overriding the bypass, so move Rule C to the bottom of the list.

**Origin lockdown works** (after section 9, expect a failure or timeout, not your store):

```bash
curl -sk -o /dev/null -w "%{http_code}\n" --resolve www.example.com:443:ORIGIN_IP https://www.example.com/
```

**The IP spoofing trick is dead** (section 7). Send a fake IP:

```bash
curl -s -o /dev/null -H "X-Forwarded-For: 203.0.113.99" -A "Mozilla/5.0" "https://www.example.com/index.php?main_page=index"
```

Then open **Admin → Customers/Reports → Who's Online**. You should see **your real IP**, never `203.0.113.99`.

**In a real browser:**

- [ ] Browse categories and products; attribute prices update
- [ ] Add to cart, update quantities, remove items
- [ ] Create an account, log out, log in, reset a password
- [ ] Complete checkout with each payment method (sandbox or a small real order you refund)
- [ ] The order shows the **correct customer IP** in admin
- [ ] PayPal IPN / gateway webhooks show successful delivery
- [ ] Order confirmation email arrives (mail is DNS-only)
- [ ] Admin: log in, edit and **save** a product description with HTML (tests the WAF exemption)
- [ ] Admin: upload a product image
- [ ] A digital download works for a test customer
- [ ] Contact Us sends
- [ ] Google Search Console → URL Inspection → live test passes (Googlebot isn't blocked)
- [ ] Google Merchant Center / marketplace feeds still fetch

---

## 17. Ongoing maintenance

**Weekly (first month), then monthly:**

- **Security → Events / Analytics.** Look at top blocked paths, countries, and ASNs. Anything legitimate being blocked? Anything new hammering you?
- Webhook and IPN delivery logs.
- **Rule 1 skip log.** Only expected traffic?

**Every few months:**

- Compare Cloudflare's IP list (https://www.cloudflare.com/ips/) with your mod_remoteip / LiteSpeed / `TRUSTED_PROXIES` / PHP list.
- Review your `zc_admin_ips` list and Access users.
- Consider moving challenge rules to **Block** once they've been clean.

**Always:**

- **Keep Zen Cart and plugins patched.** Cloudflare filters attacks but doesn't fix vulnerable code.
- Keep off-server backups.
- **Notifications** (Manage Account → Notifications): turn on HTTP DDoS attack alerts, SSL/TLS certificate alerts, and origin error rate alerts where your plan offers them.
- After changing CSS, JS, or images, purge those URLs.

---

## 18. When you're under attack

Signs: a flood of failed card declines, hundreds of new junk accounts, the server load spiking, or Cloudflare DDoS alerts.

1. **Look first.** Security → Events: which path, which countries, which ASNs, which user agents?
2. **Card testing on checkout:**
   - tighten the rate limit (for example 3 per minute, block 1 hour)
   - add a Managed Challenge rule for `main_page=checkout` from **every** country except your main market
   - turn on the gateway's velocity filters
   - temporarily disable guest checkout
3. **Account or contact spam:** Managed Challenge on `create_account` and `contact_us` for all visitors (`not cf.client.bot`) until it passes.
4. **Site-wide flood:** turn on **Under Attack mode** (a toggle in the old dashboard; the new security dashboard calls it the security level). Your callbacks keep working because of the section 15.2 Configuration Rule. Real shoppers see a short check page, which is acceptable for a few hours.
5. **Single network:** block or challenge that `ip.src.asnum`.
6. **After it's over:** undo the temporary changes one at a time, and write down what worked.

---

## 19. Troubleshooting

| Symptom | Likely cause | Fix |
|---|---|---|
| `ERR_TOO_MANY_REDIRECTS` | SSL mode is Flexible | Full (strict), section 5 |
| Error 525/526 | origin certificate missing, expired, or wrong hostname | fix AutoSSL or install an Origin CA certificate |
| Error 524 in admin | job ran longer than 100 seconds | section 14.3 |
| Error 403 when saving a product/EZ-Page | managed rules flagged HTML | section 12 Rule 1 admin skip (or Access) |
| Attributes don't update price, checkout buttons dead, card form blank | Rocket Loader | off, section 8.2 |
| Customers logged out at checkout | "Check IP Address" = True | False, section 6.2 |
| All orders show the same few IPs | real IP not restored | section 7 |
| Orders stuck "Pending" / PayPal orders missing | IPN or webhook challenged | sections 11, 12 Rule 1, 15 |
| Old image or CSS after an update | edge cache | purge by URL, section 8.3 |
| Maintenance mode locks **you** out | Zen Cart sees a Cloudflare IP | section 7, then re-enter your IP |
| Mail stops | `mail` or MX host proxied | gray-cloud it, section 3 |
| Google stops crawling | Rule 4/5 or a bot setting catching Googlebot | keep `not cf.client.bot`; check Security Events for "Googlebot" |
| Cron job hitting a store URL fails | Bot Fight Mode / BIC / Access | Configuration Rule for that path or run via CLI |

**Emergency bypass:** Overview → **Pause Cloudflare on Site** sends traffic straight to your server while keeping DNS. Turn off Authenticated Origin Pulls first if you enabled it, or visitors get errors.

---

## 20. Quick reference

| Area | Setting |
|---|---|
| DNS | store = proxied; mail/cpanel/ftp = DNS only |
| DNSSEC | off at registrar before switching, on in Cloudflare after |
| SSL mode | **Full (strict)** |
| Always Use HTTPS / Auto HTTPS Rewrites | On / On |
| Min TLS | 1.2 |
| HSTS | after a week, 6 months, no preload |
| Zen Cart configure.php | https URLs, SSL flags true |
| Sessions | Check IP = False, Spider Sessions = True, Recreate = True |
| Real IP | server restore + drop forwarded headers (1.5.8–2.2.x) or `TRUSTED_PROXIES` (newer) |
| Rocket Loader | **Off** |
| Always Online | Off |
| Cache HTML | **Never** |
| Bypass cache | admin, `/pub/`, `/download/`, `ajax.php`, callbacks |
| Origin | Authenticated Origin Pulls / firewall / Tunnel |
| Managed rules | On (OWASP PL1 on Pro, watch the admin) |
| Bots | Free BFM with care; Pro SBFM challenge definitely automated, allow verified |
| Custom rules | 1 skip trusted, 2 block admin, 3 block probes, 4 bad UAs, 5 geo-challenge forms |
| Rate limit | form submissions to checkout_process, login, create_account, password_forgotten, contact_us (Free: all of /index.php) |
| Admin | Cloudflare Access (or IP list) + renamed folder |
| Callbacks | skip rule + Configuration Rule (BIC off, I'm Under Attack off) |
