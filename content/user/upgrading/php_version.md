---
title: Updating your PHP Version 
description: Moving to a higher PHP version after an upgrade
category: upgrading 
weight: 10
---

After you go live with an upgrade, you will likely want to update your PHP Version.  For example, if you were running Zen Cart 1.5.1, you were probably using PHP 5.6 or 7.1.  After deploying Zen Cart 1.5.7, you will want to update your PHP version to PHP 7.4. 

You will want to run the latest PHP version which is appropriate for your Zen Cart version.  See  [Server Requirements for running Zen Cart](/user/first_steps/server_requirements/#php-version).

The process of changing your PHP is server-specific, depending on whether your hoster uses PHP Selector, MultiPHP Manager or some other utility. See [PHP Configuration](/user/upgrading/php_configuration/) for more information. 

Your hoster likely provides a knowledge base with instructions.  Contact your hoster if you are unsure how to proceed. 

**Note:** In some environments, changing your PHP version can reset your memory_limit setting.  Be sure to go to the [version page](/user/admin_pages/tools/server_info/) after updating PHP to verify the setting of your PHP Memory Limit.  For more details, see [memory_limit](/user/running/memory_limit/). 

## Watch out for new PHP warnings after updating PHP

- [Understanding problems that occur after upgrading PHP versions](/user/troubleshooting/php_debug_logs/) explains *why* PHP warnings can suddenly start occurring.  
- An explanation of *how to fix them* is provided in [PHP Warnings and Deprecated messages after upgrading](/user/upgrading/php_warnings/).
- If you are suddenly seeing "out of memory" PHP notices, your memory_limit setting has likely been reset. Go to the [version page](/user/admin_pages/tools/server_info/) to verify the setting of your PHP Memory Limit, and update it if required - see [PHP memory_limit](/user/running/memory_limit/). 

