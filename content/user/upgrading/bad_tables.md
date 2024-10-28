---
title: Incorrectly defined tables
description: Updating older table definitions 
category: Upgrading
weight: 10
---

Older versions of some Zen Cart plugins created tables that are no longer valid.  For example: 

```
CREATE TABLE `admin_files` (
  `id` int(11) NOT NULL,
  `page` varchar(64) NOT NULL DEFAULT '',
  `header` tinyint(4) NOT NULL DEFAULT 0,
  `submenu` tinyint(1) NOT NULL DEFAULT 0
) ENGINE=MyISAM;

ALTER TABLE `admin_files`
  ADD UNIQUE KEY `id` (`id`);
```

The problem with this is that it won't work when you [convert to UTF8MB4](/user/upgrading/convert_to_utf8/). 

You will get the message: 

```
ALTER TABLE `admin_files` DROP INDEX `id`
1075: Incorrect table definition; there can be only one auto column and it must be defined as a key
```

Issues like this must be fixed manually in phpMyAdmin. 

```
ALTER TABLE admin_files ADD PRIMARY KEY (id);
ALTER TABLE admin_files DROP KEY id;
```

