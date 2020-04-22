---
title: Developer Environment
description: Zen Cart Developer Environment
description: Setting up your development environment
weight: 1
---

## Writing PHP code for Zen Cart requires no particularly special environment.

1. A PHP-aware IDE is useful. We use PhpStorm.
2. A LAMP stack is useful for running a local dev store. Common options for this include XAMPP, WAMP/MAMP, and even Laravel Valet.

## Code Formatting

Zen Cart uses [PSR-2 formatting](https://www.php-fig.org/psr/psr-2/) standards for "new" code. Older code uses a "modified" PSR-2 which embraces "2 spaces" for indentation, and often left the "opening curly brace" on the prior line, instead of starting on a new line.

See [Coding Standards](/dev/contributing/coding_standards) for more details.

## Version Control

We encourage you to read the [section on Git](/dev/contributing/github_workflow/)
to learn about the workflow that the project uses.

## Preserving Directory Structure

To preserve you .git repository without the override warnings, create a file called `admin/includes/extra_configures/dev-skip_admin_rename.php`.  add the following 2 overrides:
```php
    define('ADMIN_BLOCK_WARNING_OVERRIDE', 'true');
    define('WARN_INSTALL_EXISTENCE', '0');
```
and your test/developer environment can now preserve the repository structure.


