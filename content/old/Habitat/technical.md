---
title: Tech Specs
weight: 10
---

# Technical Specs.

##Software Installed in Habitat

- Ubuntu 14.04.2 LTS trusty64 x86

- Apache 2.4.12 with SSL along with the following modules

  - mod_access_compat
  - mod_alias
  - mod_auth_basic
  - mod_authn_core
  - mod_authn_file
  - mod_authz_core
  - mod_authz_host
  - mod_authz_user
  - mod_autoindex
  - mod_deflate
  - mod_dir
  - mod_env
  - mod_filter
  - mod_mime
  - mod_mpm_prefork
  - mod_negotiation
  - mod_php5
  - mod_rewrite
  - mod_setenvif
  - mod_socache_shmcb
  - mod_ssl
  - mod_status

- MySQL 5.5.43

- phpMyAdmin 4.0.10

- PHP 5.6.10, with customized PHP configurations:
    - `error_reporting` = E_ALL
    - `display_errors` = On
    - `memory_limit` = 512M
    - `date.timezone` = UTC
    - `post_max_size` = 512M
    - `upload_max_filesize` = 512M
    - `html_errors` = Off
    - `error_log` = `\home\vagrant\habitat\php_errors.log` (Thus the `error_log` is mapped to the host machine for easy reference)

- git 1.9.1

- Composer 1.0-dev 2015-06-26

  _You can update `composer` to the latest version from the Habitat console (via `vagrant ssh`) by running `composer self-update`_

- Other tools installed via Composer

  - phpunit
  - phpmd
  - php_codesniffer
  - php-coveralls
  - vfsStream
  - phpdocumentor


###Updating

From time to time updates will be published for the Habitat VM.

But in the meantime if you need to apply updates, use `vagrant ssh` and run `sudo apt-get update && apt-get upgrade`




### Source
The Habitat Virtual Machine is built using [zencart/pioneer](https://github.com/zencart/pioneer)
