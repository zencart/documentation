---
title: Cloudflare 
description: Using Cloudflare with Zen Cart 
category: security
weight: 10
---

## Pros and Cons
Cloudflare offers several benefits for an e-commerce business, but there are also some potential drawbacks to consider.

**Pros:**

1. **Website Performance:** Cloudflare’s global network of servers helps improve website loading times by caching static content and delivering it from the nearest server to the user.

2. **DDoS Protection:** Cloudflare provides robust protection against Distributed Denial of Service (DDoS) attacks, helping ensure that your e-commerce site remains accessible even during cyber attacks.

3. **SSL/TLS Encryption:** Cloudflare offers SSL/TLS encryption, securing the connection between your website and your customers’ browsers, which is crucial for protecting sensitive information such as credit card details.

4. **Content Delivery Network (CDN):** Cloudflare operates a large CDN, which can distribute your website’s content across multiple servers worldwide, reducing latency and improving overall performance.

5. **Scalability:** Cloudflare can easily scale to accommodate traffic spikes and growing demand, ensuring that your e-commerce site remains accessible and responsive even during peak times.

**Cons:**

1. **Cost:** While Cloudflare offers a free plan, more advanced features such as DDoS protection and advanced security options are available at a cost. For larger e-commerce businesses requiring these features, the cost can add up.

2. **Learning Curve:** Implementing Cloudflare and configuring its features may require some technical expertise. This could be a challenge for e-commerce businesses without dedicated IT staff or resources.

3. **Limited Control:** Some users may find that Cloudflare’s control panel lacks certain advanced features or customization options compared to other CDN providers.

4. **Dependency Risk:** Relying heavily on Cloudflare means that your e-commerce business is somewhat dependent on their services. Any downtime or issues on Cloudflare’s end could potentially impact your website’s availability and performance.  https://downforeveryoneorjustme.com/cloudflare shows daily "Inaccessible" and "Error Received" for the last three days.  62% of complaiints are "Inaccessible".

5. **Privacy Concerns:** Cloudflare intercepts and caches website traffic, which may raise privacy concerns for some users. While Cloudflare claims to prioritize user privacy, businesses should carefully review their privacy policies and consider any potential implications.

6. **Caching** While caching delivers content more quickly, it also means that changes you make to your site aren't presented immediately.  This can be frustrating if you're making changes and want to see how they look.

7. **Email**.  If you are using `smtpauth` with the `EMAIL_SMTPAUTH_MAIL_SERVER` set to your domain (and not a subdomain), you may not be able to get email to work and may need to switch to an [external SMTP server](/user/email/external_smtp_servers/) for your email. 

## Example Use Cases

### 1. Mitigating Attacks
Store is having problems with huge spikes of traffic from certain IP addresses and ranges.  Investigation showed IPs were from Singapore, Russia and Pakistan. 

Cloudflare facilitates blocking of an entire country.  
Go to Your Website > Security > WAF, and set up a custom rule for specific countries. 
You may either challenge them with a CAPTCHA or outright block them:

![Cloudflare Rule](/images/cloudflare_rule.jpg)

To find our exactly what countries you may be getting attacked from, it is worth looking at either the website logs if any are being created, the server logs including access logs.  These will detail the IPs that are most often connecting to the website. Check these IPs via a whois checker online, and you will know what countries they are from. 

