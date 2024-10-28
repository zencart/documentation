---
title: Long field indexes 
description: Creating indexes on long fields 
category: Upgrading
weight: 10
---

Older versions of Zen Cart created indexes on fields that were very long, using the entire field.  For example, Zen Cart 1.5.1 did the following: 

```
CREATE TABLE media_manager (
  media_id int(11) NOT NULL auto_increment,
  media_name varchar(255) NOT NULL default '',
  ... 
  KEY idx_media_name_zen (media_name)
) ENGINE=MyISAM;
```

The problem with this is that it won't work when you [convert to UTF8MB4](/user/upgrading/convert_to_utf8/). 

Newer versions of Zen Cart create the index on a substring of media name.
To handle older databases, the upgrade process converts indexes to use a substring as well. 
However, the `DROP KEY` and subsequent `ADD KEY` operation fails on some hosters when run through Zen Cart.  This means your UTF8 conversion will also fail.  

You will get the message:

```
CREATE INDEX `idx_media_name_zen` ON `media_manager` (media_name)
1071: Specified key was too long; max key length is 1000 bytes
```

If this happens to you, the best resolution is to use phpMyAdmin to do these 
operations (not Install SQL Patches in admin).  Simply enter the commands above into the SQL tab of phpMyAdmin.

```
ALTER TABLE media_manager DROP KEY idx_media_name_zen;
ALTER TABLE media_manager ADD KEY idx_media_name_zen (media_name(191));
```

You must add your prefix if you use one.  For example, if your prefix is `zc`, you would enter 

```
ALTER TABLE zc_media_manager DROP KEY idx_media_name_zen;
ALTER TABLE zc_media_manager ADD KEY idx_media_name_zen (media_name(191));
```

Tables with this issue are the following: 

- `media_manager`
- `whos_online`

