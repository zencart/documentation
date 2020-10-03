---
title: Webserver Tuning Tips 
description: Improving MySQL database performance
category: speed
weight: 10
---

If your server is performing poorly you may want to consider the following PHP and MySQL tuning suggestions.

First, review the [Zen Cart Server Requirements](/user/first_steps/server_requirements/) document for the essentials.

# PHP Tuning

- `memory_limit` should be set to 32M or higher. Nowadays it's very common to see it set somewhere between 128M-512M. Set it to as much as you need, but not higher, otherwise you're wasting RAM resources on your server.
- `max_execution_time` is commonly set to 60 seconds, which should be fine  
- `max_input_time` is commonly set to 60 seconds, which is normally fine, except if you're doing large uploads such as huge photos or large input files with plugins like [EasyPopulate](/user/products/easypopulate/)
- `file_uploads` must be set to "On" if you expect to be able to upload files either via your admin interface or receive files from your customers  
- `post_max_size` should be set to something that matches the size of files you will allow to be uploaded, whether by customers or by yourself as an administrator. Start with at least 8M, or even 32M or larger if you're uploading large images or large attachments or doing large data-imports.
- `upload_max_filesize` should be set to the same as `post_max_size`
- `gzip` compression should be enabled: `zlib` extension should be loaded and `zlib.output_compression` should be set to a non-zero value


## MySQL Tuning

In MySQL, the server's `my.cnf` file contains the configuration settings for the database engine operation.  The default settings are typically inadequate for optimal use, and thus require tuning for your database to run smoothly.

Tuning MySQL is a carefully-guarded skill by industry professionals since the knowledge is specialized and the expertise of professionals skilled in this topic commands a high price because it typically affords the benefactor a competitive edge.

Here are some tips with which you can experiment if you have control over the MySQL configuration (most storeowners will not have this level of access, and must rely on their hosting company's server administrator to do this sort of tweaking because it affects EVERYONE running on that server).

The following points talk about settings in `my.cnf` vs statistics on running processes which can be found in your phpMyAdmin screen.

### MySQL Server RAM

Note that the more RAM you have available to MySQL, the more room you have to play when tweaking. It's important to give a careful balance between MySQL and other services (especially Apache and PHP).

### MySQL Memory Model

The default memory allocations for MySQL are not adequate for a live server. You need to increase the memory allocations beyond the standard settings.

The sum of all `read/sort/join buffer size` settings, and total `tmp tables` multiplied by `tmp table sizes`, and `cache size` settings plus `memory per connection` multiplied by `max number of connections` should be no more than 90% of available memory allocated to MySQL

### MySQL Caching

`table_cache` should be large enough to handle the number of `open_tables` at any given time, plus 5-10% room to spare  

`table_definition_cache` should be set similarly

`thread_cache_size` needs to be large enough to support the number of `threads_created` and `threads_cached` per second

### Buffers

`key_buffer` size should be set to a level which suits the amount of index usage occurring on your server. Using 15-20% of system memory is common. But if this value is too large you're wasting resources that could be used better elsewhere.

`read_buffer_size` should be under 8M, and usually more than 2M. Increase it depending on the number of table scans happening on an ongoing basis.

`read_rnd_buffer_size` might benefit from being 2M or larger

`join_buffer_size` and `sort_buffer_size` often do well at 1M but sometimes increasing this to 2M may be beneficial

`tmp_table_size` needs to be large enough to handle the memory demands of any temporary-tables created by query joins. Poorly written joins on improperly indexed tables will create higher demands on this setting

### Connections

`max_connections` vs `max_used_connections` -- Don't set `max_connections` way too high, else you're wasting resources. Your `max_used_connections` should be more than 10% of your `max_connections`.

`max_open_files` vs `open_files` -- you should be using less than 75% of your `max_open_files` setting

### Processes

You'll need to refine the number of child processes to be spawned before they are killed by the server. You do NOT want to have excess numbers of idle processes in MySQL, as this wastes resources. This is a combination of `max_connections` and `connect_timeout`, `wait_timeout`, `max_connect_errors`.

### Slow Query Log

It may be useful to enable `log-slow-queries` so that someone skilled in understanding the logs and altering queries for performance can review them for tweaking.  

When using this feature, setting `long_query_time` to a value short enough to catch slow-running queries will help. This number may need adjusting over time. `2` might be a good starting value.  

Be aware that this log can grow VERY large very quickly if there are many problems and slow queries. Beware. Best to use this only temporarily from time to time.

### General Advice

You can find many articles online regarding MySQL tweaking or optimization. There are many opinions, and it is really a balancing act. Determine what works best for you based on your actual site performance ... especially when it is busiest.
