---
title: Bootstrap in Zen Cart 
description: Developer information on the use of the Bootstrap library 
category: libraries
weight: 10
type: codepage
---

## Bootstrap in the Bootstrap Template 

Bootstrap template version 3.X is based on [Bootstrap 4](https://getbootstrap.com/docs/4.6/getting-started/introduction/).  You can find the exact version of Bootstrap (`major.minor.patch`) in use by looking at the file `includes/templates/bootstrap/common/html_header.php`, which pulls in the Bootstrap javascript and css.

The Bootstrap template is described in more detail in the [storefront documentation on Bootstrap template](/user/template/bootstrap/).

Bootstrap Version| Storefront Bootstrap Template
-----------|--------------
BS 4.6.2 | Template Version 3.X

## Bootstrap in Zen Cart Admin

Bootstrap has been used in the Zen Cart admin since Zen Cart version 1.5.5.
The following chart shows the association between Bootstrap and Zen Cart versions. 

Bootstrap Version| Zen Cart Admin 
-----------|--------------
BS 3.4.1 | ZC 1.5.6-2.1.0
BS 3.3.7 | ZC 1.5.5

There is work underway to move the Zen Cart admin to Bootstrap 5. 
You may follow this effort by monitoring [this PR](https://github.com/zencart/zencart/pull/6173).

## Bootstrap in zc_install

Bootstrap has been used in the Zen Cart upgrader (`zc_install`) since Zen Cart version 2.1.0. 
The following chart shows the association between Bootstrap and Zen Cart versions. 

Bootstrap Version| Zen Cart zc_install 
-----------|--------------
BS 5.3.3 | ZC 2.1.0

## Help on Bootstrap

- [Bootstrap 5](https://getbootstrap.com/docs/5.0/)
- [Bootstrap 4](https://getbootstrap.com/docs/4.6/)
- [Bootstrap 3](https://getbootstrap.com/docs/3.3/)

