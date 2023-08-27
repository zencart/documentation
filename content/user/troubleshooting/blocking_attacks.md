---
title: Blocking Attacks 
description: How do I keep these bots away from my site? 
category: troubleshooting 
weight: 10
---

## Determining an IP Address

IP Addresses may be viewed in the following locations: 

- Admin > Customers > Orders > Edit - the order details page shows the IP Address of the person who placed the order.  

- Admin > Customers > Customers - from the customer listing page, the registration IP address for that customer is shown (in Zen Cart 1.5.8 and above). 

- Admin > Tools > Who's Online - the address of each session is shown.

In each case, clicking the IP Address will show you more information about it. 

## Cloudflare

A free account on Cloudflare.com will let you manage your DNS through them, and set up IP-blocking from malicious visitors.

By default Cloudflare will then block all kinds of bad traffic automatically for you.

You can set up a firewall rule (one of five free rules available) to block a "list" of IP addresses that you manage. 
You can set up other firewall rules to block entire countries. (Be sure to only block countries you will actually never intend to sell to.)

In order for it to work, you must change your domain's Name Servers (in your domain registrar) to point to Cloudflare instead of to your hosting company.

## Config Server Firewall (CSF) and cPHulk
Both CSF and cPHulk are powerful tools for securing and protecting your server. However, they have different features and functionalities.

CSF is a comprehensive firewall tool that provides a wide range of features for protecting your server against various network threats, including brute-force attacks, DoS attacks, port scans, and more. Some of its key features include IP blocking, port filtering, email notifications, and log analysis. Additionally, CSF is highly configurable, allowing you to customize its settings to suit your specific security needs.

On the other hand, cPHulk is a security feature that is specifically designed to protect cPanel and WHM from brute-force attacks. It tracks login attempts and blocks IP addresses that have too many failed attempts, helping to prevent unauthorized access to your server. It also provides features such as email notifications and IP whitelisting.

In terms of features, CSF offers a broader range of functionalities for server security, while cPHulk is focused on protecting cPanel and WHM from brute-force attacks. However, cPHulk is integrated into cPanel/WHM, which may make it easier to use for those who are already familiar with the cPanel/WHM interface.

Overall, both CSF and cPHulk are powerful tools that can help to protect your server against various security threats. Which one is better for you depends on your specific security needs and preferences.

It is **not** recommended to run both at the same time.

### CSF
   1. To use CSF to block unwanted IP addresses, follow these steps:
      - Log in to your Linux server as the root user.
      - Download and install the latest version of CSF from the ConfigServer website.
      - Once installed, open the CSF configuration file (typically located at /etc/csf/csf.conf) and make any necessary adjustments to the settings.
      - To block an IP address, add the IP address to the "DENY_IP_LIMIT" or "DENY_TEMP_IP_LIMIT" field in the CSF configuration file.
      - Save the changes to the CSF configuration file and restart CSF using the command "csf -r".
      - You can also block an IP address temporarily using the command "csf -d [IP_ADDRESS]".
      - To unblock an IP address, remove the IP address from the "DENY_IP_LIMIT" or "DENY_TEMP_IP_LIMIT" field in the CSF configuration file and restart CSF.
  2. CSF also allows you to configure additional settings, such as allowing certain IP addresses to bypass the firewall or blocking IP addresses that repeatedly attempt to connect to specific ports. It is important to review the CSF logs regularly to ensure that legitimate users are not being blocked and to adjust the CSF settings accordingly.

### CSF with WHM
  1. To use CSF in a WHM environment, follow these steps:
     - Log in to WHM as the root user.
     - Navigate to the "Plugins" section and select "ConfigServer Security & Firewall".
     - Install and activate CSF by following the on-screen instructions.
     - Once installed, open the CSF configuration file by clicking on "Firewall Configuration" in the CSF plugin interface.
     - Make any necessary adjustments to the settings, such as enabling "SYNFLOOD" protection or setting custom port rules.
     - To block an IP address, add the IP address to the "csf.deny" file in the CSF directory (/etc/csf/csf.deny).
     - Save the changes to the CSF configuration file and restart CSF using the "Restart csf+lfd" button in the CSF plugin interface.
     - You can also block an IP address temporarily using the "Temporary IP Entries" section of the CSF plugin interface.
     - To unblock an IP address, remove the IP address from the "csf.deny" file and restart CSF using the "Restart csf+lfd" button in the CSF plugin interface.
  2. CSF also allows you to configure additional settings, such as allowing certain IP addresses to bypass the firewall or blocking IP addresses that repeatedly attempt to connect to specific ports. It is important to review the CSF logs regularly to ensure that legitimate users are not being blocked and to adjust the CSF settings accordingly.

### cPHulk
  To properly use cPHulk to block unwanted IP addresses, follow these steps:
  - Log in to WHM using your root credentials.
  - Navigate to the "Security Center" section and select "cPHulk Brute Force Protection".
  - Enable cPHulk by clicking the "Enable" button.
  - Configure the settings for cPHulk, such as the number of login attempts that trigger a block and the length of the block.
  - Set up cPHulk to email you notifications when an IP address is blocked.
  - Review the cPHulk logs regularly to ensure that legitimate users are not being blocked.
  - If you find that a legitimate IP address has been blocked, you can whitelist the IP address in cPHulk.
  - You can block entire countries in cPHulk if needed.
It is important to review the CSF or cPHulk logs regularly to ensure that legitimate users are not being inadvertently blocked and to adjust the CSF settings accordingly. Additionally, you can configure CSF to send email alerts when certain events occur, such as when an IP address is blocked or unblocked. This can help you stay informed about the activity on your server and ensure that your server is protected against various security threats.

## Access Blocker 
If you wish to block IP addresses independently from your store's Admin (whether you also use Cloudflare or not) you might consider installing the [Access Blocker plugin](https://www.zen-cart.com/downloads.php?do=file&id=2237)

## Related 

- [Abuse and Spam](/user/running/spam/)
- [Blocking probing activity](/user/security/block_probes/)

