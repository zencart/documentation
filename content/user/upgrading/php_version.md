---
title: Updating your PHP Version 
description: Moving to a higher PHP version after an upgrade
category: upgrading 
weight: 10
---

Before you begin your upgrade, you may wish to check [which PHP versions are available](/user/upgrading/check_php_version).

After you go live with an upgrade, you will likely want to update your PHP Version.  For example, if you were running Zen Cart 1.5.1, you were probably using PHP 5.6 or 7.1.  After deploying Zen Cart 1.5.7, you will want to update your PHP version to PHP 7.4. And after deploying Zen Cart 1.5.8, you will want to update your PHP version to 8.0 or 8.1.  

In extreme cases, such as upgrades from much older versions (1.5.1 to 1.5.8a, for example), you may have to change the PHP version prior to even running `zc_install`.   But if your site only one version behind, typically the new version will work with the highest version (or even second highest version) of PHP supported by the old version.  For example, Zen Cart 2.0.0 works with PHP 8.1, which is one of the higher versions recommended for Zen Cart 1.5.8, the prior release. 

You will want to run the latest PHP version which is appropriate for your Zen Cart version.  See  [Server Requirements for running Zen Cart](/user/first_steps/server_requirements/#php-version).

The process of changing your PHP is server-specific, depending on whether your hoster uses PHP Selector, MultiPHP Manager or some other utility. See [PHP Configuration](/user/upgrading/php_configuration/) for more information. 

Your hoster likely provides a knowledge base with instructions.  Contact your hoster if you are unsure how to proceed. 

**Note:** In some environments, changing your PHP version can reset your memory_limit setting.  Be sure to go to the [version page](/user/admin_pages/tools/server_info/) after updating PHP to verify the setting of your PHP Memory Limit.  For more details, see [memory_limit](/user/running/memory_limit/). 

## Watch out for new PHP warnings after updating PHP

- [Understanding problems that occur after upgrading PHP versions](/user/troubleshooting/php_debug_logs/) explains *why* PHP warnings can suddenly start occurring.  
- An explanation of *how to fix them* is provided in [PHP Warnings and Deprecated messages after upgrading](/user/upgrading/php_warnings/).
- If you are suddenly seeing "out of memory" PHP notices, your memory_limit setting has likely been reset. Go to the [version page](/user/admin_pages/tools/server_info/) to verify the setting of your PHP Memory Limit, and update it if required - see [PHP memory_limit](/user/running/memory_limit/). 

