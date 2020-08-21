---
title: Basics - Components of Zen Cart 
description: How the pieces fit together 
category: first_steps
weight: 10
---

Zen Cart is what's called a database-backed web application.  

This means it doesn't run on your computer, the way Microsoft Excel does - instead, it is set up on a [web host](/user/first_steps/hosting/) and uses web technologies like PHP, MySQL and Apache to create your store. 

### What is a database? 

The database is a collection of tables. Tables are like spreadsheets, storing data in rows and columns, related to whatever the structure of that table is for. For customers, it means email addresses, passwords, etc. For address books, it means all the address info for each customer. For orders, all the order details. For products, the details of each aspect of each product. And so on. You could look at a database as a multi-sheet spreadsheet, but way more optimized and efficient in how it automatically handles indexing and storage/retrieval.  

Unlike a file, which you view through an editor like Notepad++, a database must be viewed through a tool which provides a database interface.  One such tool is [phpMyAdmin](https://www.phpmyadmin.net/).  

Here's a screenshot of phpMyAdmin viewing the records in the specials table, which contains a list of all the products on special.

![Specials table](/images/phpmyadmin_specials.png)

You can view the [database schema for Zen Cart](/dev/schema/) to learn more about how the data is structured .

### What about all the files in Zen Cart? 

The files contain computer code that allows you to access the database, and code that displays the data that's in the database.   So for example, `admin/customers.php` is a file, which allows the administrator to access the `customers` table in the database. 

### How is the website broken up? 

The website created by Zen Cart has two parts: 

- Storefront - Visible to everyone.  The part of the website that allows products to be viewed and purchased.  Also called _the catalog_.  
- Admin - Only visible to the store administrator.  Provides the back-office functions of order processing and inventory management. 
 
### Is there a file that corresponds to each page in the storefront? 

Zen Cart pages are dynamically created, so there's no single file like (say) `specials.html` for the specials page.  Instead, the specials page

```
https://YOURSITE.com/index.php?main_page=specials 
```

is created on the fly by executing a number of PHP files.  One part of your [template](/user/template/what_is_a_template/) is the [template page](/user/template/template_pages/) for specials.  It controls how the specials are displayed, and you can modify it as you see fit.  

 
