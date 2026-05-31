---
title: Advanced Topics in site security
description: Crafting your site's Header and CSP
category: security
weight: 10
---

Zen Cart can provide some guidance on creating a content security 
policy, but it can't be both overly strict and for general use, 
because payment gateways, analytics, tag managers, hosted checkout widgets, iframe-based 3-D Secure, CAPTCHA, chat widgets, and shipping integrations vary by store.

## Recommended baseline headers for most ecommerce sites
These are safe, broadly applicable starting points:

```
Strict-Transport-Security: max-age=31536000
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
Content-Security-Policy: frame-ancestors 'self'
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: camera=(), microphone=(), geolocation=(), payment=(), usb=(), bluetooth=(), accelerometer=(), gyroscope=(), magnetometer=()
```

Notes on each:

### Strict-Transport-Security
Use only when the site is fully HTTPS and HTTP redirects cleanly to HTTPS. Start with:
```
Strict-Transport-Security: max-age=31536000
```

We do not generically recommend `includeSubDomains` or `preload` unless the merchant knows every subdomain is HTTPS-ready now and will remain so. HSTS preload requires at least one year of max-age and includeSubDomains; once preloaded, undoing mistakes is slow and painful. (MDN Web Docs)

For confident stores:
```
Strict-Transport-Security: max-age=31536000; includeSubDomainsFor highly confident stores that understand preload consequences:
Strict-Transport-Security: max-age=63072000; includeSubDomains; preload
```

### X-Frame-Options / CSP frame-ancestors
For Zen Cart storefronts/admins, clickjacking protection is appropriate. X-Frame-Options: SAMEORIGIN is broadly compatible. Modern CSP’s frame-ancestors is more flexible and is effectively the modern replacement, but including both is still common for compatibility. frame-ancestors controls who may embed your page; this is different from frame-src, which controls what your page may embed. (MDN Web Docs)

Recommended:

```
X-Frame-Options: SAMEORIGIN
Content-Security-Policy: frame-ancestors 'self'
```

Use 'none' only if the store never needs to be framed even by itself:

```
Content-Security-Policy: frame-ancestors 'none'
X-Frame-Options: DENY
```

We don't recommend DENY as the generic ecommerce default because some admin tools, preview tools, checkout integrations, or site-builder environments can break.

### Content-Security-Policy

This is the one that should be treated carefully. A strict CSP can improve XSS resilience, but a universal ecommerce CSP often breaks checkout, payment widgets, analytics, hosted fields, CAPTCHA, fraud detection, maps, chat, tracking pixels, and tag managers.

For generic recommendations, the safe minimum CSP would be:
```
Content-Security-Policy: frame-ancestors 'self'; upgrade-insecure-requests
```

`frame-ancestors` helps against clickjacking, and `upgrade-insecure-requests` helps clean up mixed-content HTTP asset references. For a stronger per-store CSP, the merchant or developer should inventory real third-party domains first.

A more complete template, not universal copy/paste:

```
Content-Security-Policy: default-src 'self'; base-uri 'self'; object-src 'none'; frame-ancestors 'self'; form-action 'self' https://PAYMENT-GATEWAY.example; script-src 'self' 'unsafe-inline' https://TRUSTED-SCRIPTS.example; style-src 'self' 'unsafe-inline'; img-src 'self' data: https:; font-src 'self' data: https:; connect-src 'self' https://TRUSTED-API.example; frame-src 'self' https://TRUSTED-FRAMES.example; upgrade-insecure-requests
```

For legacy Zen Cart themes/plugins, script-src `unsafe-inline` and style-src `unsafe-inline` may be necessary at first. That is not ideal, but it is often realistic for older ecommerce templates. The better path is to test with `Content-Security-Policy-Report-Only` first, then tighten.

### X-Content-Type-Options
Use this almost everywhere:
```
X-Content-Type-Options: nosniff
```

It tells browsers to respect declared MIME types rather than guessing. This is a standard security hardening header and is commonly expected by scanners. (MDN Web Docs)

### Referrer-Policy
A good ecommerce default:
```
Referrer-Policy: strict-origin-when-cross-origin
```

This preserves useful same-origin referrer detail, sends only the origin to HTTPS cross-origin destinations, and avoids leaking full paths/query strings to other sites in many cases. (MDN Web Docs)

More private, but can reduce analytics/affiliate attribution detail:

```
Referrer-Policy: same-origin
```

Very private:

```
Referrer-Policy: no-referrer
```

For generic Zen Cart recommendations, `strict-origin-when-cross-origin` is the best balance.

### Permissions-Policy
This is safe to recommend, but keep it conservative. It controls access to browser features like camera, microphone, geolocation, etc. (MDN Web Docs)

Recommended generic ecommerce baseline:

```
Permissions-Policy: camera=(), microphone=(), geolocation=(), usb=(), bluetooth=(), accelerometer=(), gyroscope=(), magnetometer=()
```

Be cautious with:
```
payment=()
```

Most regular Zen Cart stores do not use the browser Payment Request API, so disabling it is usually fine. But if a store uses Apple Pay / Google Pay / Payment Request integrations, payment=() could interfere. Safer generic baseline:
```
Permissions-Policy: camera=(), microphone=(), geolocation=(), usb=(), bluetooth=(), accelerometer=(), gyroscope=(), magnetometer=()
```

Optional stricter version:
```
Permissions-Policy: camera=(), microphone=(), geolocation=(), payment=(), usb=(), bluetooth=(), accelerometer=(), gyroscope=(), magnetometer=()
```

### Apache / .htaccess
Works if Apache has `mod_headers` enabled and the hosting account permits `Header` directives in `.htaccess`.

```
<IfModule mod_headers.c>
    Header always set Strict-Transport-Security "max-age=31536000" "expr=%{HTTPS} == 'on'"
    Header always set X-Content-Type-Options "nosniff"
    Header always set X-Frame-Options "SAMEORIGIN"
    Header always set Content-Security-Policy "frame-ancestors 'self'; upgrade-insecure-requests"
    Header always set Referrer-Policy "strict-origin-when-cross-origin"
    Header always set Permissions-Policy "camera=(), microphone=(), geolocation=(), usb=(), bluetooth=(), accelerometer=(), gyroscope=(), magnetometer=()"
</IfModule>
```

If the host does not allow this in `.htaccess`, it must be placed in the Apache vhost config, global config, hosting control panel, or reverse proxy/CDN.

Optional: For older Apache versions where the expr= syntax is unsupported, use the HTTPS vhost only:

```
<VirtualHost *:443>
    Header always set Strict-Transport-Security "max-age=31536000"
    Header always set X-Content-Type-Options "nosniff"
    Header always set X-Frame-Options "SAMEORIGIN"
    Header always set Content-Security-Policy "frame-ancestors 'self'; upgrade-insecure-requests"
    Header always set Referrer-Policy "strict-origin-when-cross-origin"
    Header always set Permissions-Policy "camera=(), microphone=(), geolocation=(), usb=(), bluetooth=(), accelerometer=(), gyroscope=(), magnetometer=()"
</VirtualHost>
```

### Nginx
Nginx headers must be set in server/location config by someone with server/admin access. They cannot be set through `.htaccess.`

Inside the HTTPS server {} block:

```
add_header Strict-Transport-Security "max-age=31536000" always;
add_header X-Content-Type-Options "nosniff" always;
add_header X-Frame-Options "SAMEORIGIN" always;
add_header Content-Security-Policy "frame-ancestors 'self'; upgrade-insecure-requests" always;
add_header Referrer-Policy "strict-origin-when-cross-origin" always;
add_header Permissions-Policy "camera=(), microphone=(), geolocation=(), usb=(), bluetooth=(), accelerometer=(), gyroscope=(), magnetometer=()" always;
```

Do not put the HSTS header in the port 80 HTTP server block. HSTS is only honored over HTTPS, and it should represent the HTTPS site’s policy.

### LiteSpeed / OpenLiteSpeed

LiteSpeed generally supports Apache-style directives in .htaccess, including Header, depending on edition/configuration and hosting provider settings.

Try the Apache .htaccess version:
```
<IfModule mod_headers.c>
    Header always set Strict-Transport-Security "max-age=31536000" "expr=%{HTTPS} == 'on'"
    Header always set X-Content-Type-Options "nosniff"
    Header always set X-Frame-Options "SAMEORIGIN"
    Header always set Content-Security-Policy "frame-ancestors 'self'; upgrade-insecure-requests"
    Header always set Referrer-Policy "strict-origin-when-cross-origin"
    Header always set Permissions-Policy "camera=(), microphone=(), geolocation=(), usb=(), bluetooth=(), accelerometer=(), gyroscope=(), magnetometer=()"
</IfModule>
```

If that does not work, the hosting company may need to set equivalent response headers in the LiteSpeed WebAdmin console, vhost config, hosting control panel, or CDN layer.


### PHP fallback
PHP can set response headers, but this is a fallback, not the primary recommendation.
Example:
```
header("X-Content-Type-Options: nosniff");
header("X-Frame-Options: SAMEORIGIN");
header("Content-Security-Policy: frame-ancestors 'self'; upgrade-insecure-requests");
header("Referrer-Policy: strict-origin-when-cross-origin");
header("Permissions-Policy: camera=(), microphone=(), geolocation=(), usb=(), bluetooth=(), accelerometer=(), gyroscope=(), magnetometer=()");

if (!empty($_SERVER['HTTPS']) && $_SERVER['HTTPS'] !== 'off') {
    header("Strict-Transport-Security: max-age=31536000");
}
```
Limitations:

PHP only affects responses handled by PHP. It may not cover static assets, redirects, error pages, images, CSS, JS, PDFs, CDN-served files, or server-generated responses. Server/CDN-level headers are cleaner.

--------------------
### What merchants can do themselves vs hosting/admin
Usually merchant-accessible:
- .htaccess on Apache/LiteSpeed, if allowed
- hosting control panel security headers tool, if provided
- Cloudflare/CDN transform rules or response header rules, if available
- Zen Cart/PHP bootstrap code, as fallback

These usually require hosting/server admin intervention:
- Nginx config
- Apache vhost/global config
- LiteSpeed vhost/global config
- TLS protocol/cipher configuration
- HTTP/2/HTTP/3 config
- server_tokens / ServerSignature / ServerTokens
- WAF/rate limiting
- ModSecurity/OWASP CRS tuning
- firewall/fail2ban
- PHP-FPM pool settings

### Headers I would NOT recommend generically
Avoid these as blanket ecommerce recommendations:
- Cross-Origin-Embedder-Policy: require-corp
- Cross-Origin-Opener-Policy: same-origin
- Cross-Origin-Resource-Policy: same-origin

They can be useful, but they are much more likely to break third-party scripts, payment widgets, externally hosted assets, embedded content, or integrations. COEP in particular restricts loading cross-origin resources unless those resources explicitly grant permission. (MDN Web Docs)

Also avoid recommending X-XSS-Protection

It is obsolete and should not be relied on. Modern guidance focuses on CSP and correct output escaping rather than the old browser XSS filter.

---------
Ecommerce-specific hardening guidance
For a Zen Cart audience, I would add these non-header recommendations:
1. Force HTTPS everywhere
Storefront, admin, checkout, login, account pages, images, CSS, JS, and canonical URLs should all use HTTPS.
2. Keep admin renamed/protected
Zen Cart’s admin directory should not be left at a predictable path. Add hosting-level protection where practical.
3. Use correct file permissions
Configuration files should not be writable by the web server after installation unless specifically required.
4. Remove install/upgrade leftovers
Delete installer directories, old backups, SQL dumps, zip files, test scripts, phpinfo files, and abandoned plugin files.
5. Protect sensitive file types
Deny public access to .sql, .bak, .old, .zip, .tar, .gz, .env, .log, .ini, .yml, .yaml, .config, and similar files.
6. Use modern PHP and patched Zen Cart/plugins
Headers help, but they do not compensate for vulnerable PHP code, abandoned plugins, or outdated payment modules.
7. Disable directory listing
On Apache/LiteSpeed:
Options -IndexesOn Nginx:
autoindex off;8. Set secure cookies where possible
Session cookies should use Secure, HttpOnly, and an appropriate SameSite value. For ecommerce, SameSite=Lax is often safer than Strict because payment/checkout redirects may need to preserve session behavior.
9. Test after enabling headers
Use browser dev tools, checkout test orders, admin login, payment redirects, 3-D Secure flows, CAPTCHA, analytics, and any iframe/payment widgets. Mozilla Observatory is useful for scanning header posture. (MDN Web Docs)

The “safe starter recommendation”:

Apache (.htaccess)
```
<IfModule mod_headers.c>
    Header always set Strict-Transport-Security "max-age=31536000" "expr=%{HTTPS} == 'on'"
    Header always set X-Content-Type-Options "nosniff"
    Header always set X-Frame-Options "SAMEORIGIN"
    Header always set Content-Security-Policy "frame-ancestors 'self'; upgrade-insecure-requests"
    Header always set Referrer-Policy "strict-origin-when-cross-origin"
    Header always set Permissions-Policy "camera=(), microphone=(), geolocation=(), usb=(), bluetooth=(), accelerometer=(), gyroscope=(), magnetometer=()"
</IfModule>
```

And for Nginx:

```
add_header Strict-Transport-Security "max-age=31536000" always;
add_header X-Content-Type-Options "nosniff" always;
add_header X-Frame-Options "SAMEORIGIN" always;
add_header Content-Security-Policy "frame-ancestors 'self'; upgrade-insecure-requests" always;
add_header Referrer-Policy "strict-origin-when-cross-origin" always;
add_header Permissions-Policy "camera=(), microphone=(), geolocation=(), usb=(), bluetooth=(), accelerometer=(), gyroscope=(), magnetometer=()" always;
```

These are conservative starter headers. Stores using embedded payment fields, third-party checkout, CAPTCHA, analytics, chat widgets, maps, or tag managers should test carefully before adding a stricter Content-Security-Policy.

