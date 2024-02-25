---
title: Can Zen Cart do this?  
description: Miscellaneous FAQs about Zen Cart
category: miscellaneous
weight: -1
---

--- 

### Can Zen Cart be integrated with Accounting Packages such as QuickBooks or Sage?
Although Zen Cart does not come with built-in accounting package integration, community members have contributed add-ons for specific packages. These may be found in the [Admin Tools](https://www.zen-cart.com/downloads.php?do=cat&id=1) section of this site's [Plugins Library](https://www.zen-cart.com/downloads.php).

If you are looking for integration with a specific package, it's always worth searching the main forum as you may find references to packages which are not in the Plugins Library. 

---

### Can customers purchase from my Zen Cart shop without creating an account?

At this time all customers must register with their full name, address and other information before going to the checkout. 

However, the [One Page Checkout](https://www.zen-cart.com/downloads.php?do=file&id=2095) plugin has a built-in guest checkout feature which might meet your needs.

---

### Can products be in multiple categories? 

Yes.  See [Linked Products](/user/products/linked_product/).

---

### Does Zen Cart support my preferred shipper? 

Zen Cart supports UPS, USPS, Canada Post, and [many other shippers](/user/shipping/). 

---

### Can I set my own shipping rates with Zen Cart? 

You may offer [free shipping](/user/shipping/free_shipping/) or price shipping according to a variety of factors, such as the number or weight of items in an order.  See [Available Shipping Modules](/user/shipping/shipping/#available-shipping-modules) for more details.

---
### Can Zen Cart create shipping labels? 

No, but Zen Cart is supported by [ShipStation](https://www.shipstation.com), which is a popular postage and label creation solution.  Some other options are discussed in the [shipping labels FAQ](/user/shipping/labels/).

---

### Does Zen Cart support my preferred payment provider? 
Zen Cart supports PayPal, Authorize, Square, and [many other payment processors](/user/payment/). 

---
### Can Zen Cart discount products?

Zen Cart supports a number of discounting mechanisms: 

- per product discounts called [Specials](/user/admin_pages/catalog/specials/)
- per category discounts called [Sales](/user/admin_pages/catalog/salemaker/)
- [Coupons](/user/order_total/coupons/)
- [Group Discounts](/user/order_total/group_pricing/)
- [per-product Quantity Discounts](/user/products/quantity_discounts/) 
- and [other discounting methods](/user/order_total/). 

---
### Can Zen Cart offer tiered, customer specific or bundled pricing? 

- Tiered pricing is available on a per product basis using [Quantity Discounts](/user/products/quantity_discounts/) 
- Customer specific pricing is not available natively but can be performed with plugins.
- Bundled pricing (sometimes called kit or package pricing) is not available natively but can be performed with plugins.

---

### Can Zen Cart add fees to an order? 

Zen Cart can add a fee line item on the basis of a variety of factors:

- A Low Order Fee can be assessed on orders below a certain value. 
- A Payment module fee/discount can be added to an order based on the payment method chosen using the [Ceon Payment Surcharges/Discounts](https://www.zen-cart.com/downloads.php?do=file&id=1279) plugin. 
- You can also add fees when you assign attributes to products.  See [Admin > Catalog > Attributes Controller](/user/admin_pages/catalog/attributes_controller/). 

See [Order Total Modules](/user/order_total/order_total/) for more details. 

---
### Can Zen Cart track my inventory? 

Zen Cart offers basic inventory management (quantity in stock), with related settings like whether to allow checkout when stock is not sufficient to fill an order.  See [tracking inventory](/user/running/stock/) for more details.

Note that full cost-of-goods sold (COGS) tracking is not part of Zen  Cart, and would require an external system, such as an [Enterprise Resource Planning (or ERP) tool](/user/running/erp/). 

---
### Can Zen Cart sell products with variants? 
Zen Cart supports variants through the [attributes system](/user/products/attributes/).  You can add
color, size, or any other product variant to your products with no limitations.

---

### Can Zen Cart track the stock of products with variants? 

At the current time, Zen Cart does not track the stock of individual product variants (a t-shirt's stock of large versus medium, for example).  There are commercial modifications that address this requirement however, such as 
the [Products' Options' Stock Manager (POSM)](https://vinosdefrutastropicales.com/product_extra_files/options_stock/readme.html). 

Note that this plugin is sometimes called Products Options Stock Manager (without the apostrophes). 

There are also open source plugins which provide this capability; search for "Stock by Attributes." 

---

### Can Zen Cart configure products with dependent attributes? 

Dependent attributes describes a situation where the options for one attribute can only be determined when a prior attribute has been set to a specific value.  For example, the values for Car Model depend on the value of Car Make.

The POSM plugin referenced above also does this. 

---

### Can Zen Cart allow me to create restricted admin accounts? 
Yes - you can limit admin users to a subset of the superuser capabilities using
[Admin Profiles](/user/admin_pages/admins/admin_profiles/). 

---

### Can Zen Cart create SEO friendly URLs? 
Not by default, but plugins are available.  Please see [SEO URLs](/user/seo/other_topics/#seo-urls).

--- 
### Can Zen Cart allow me to edit an order after it was placed? 
Editing orders may be performed using the plugin 
[Edit Orders](/user/orders/edit_orders).

---

### Can I login to a customer's account? 
Yes you can.  See [Master Password capabilities](/user/admin/master_password/). 

---

### Can I add a new page to my cart easily? 

Yes, there are several ways you can [add a new page](/user/customizing/add_pages/). 

--- 
### Does Zen Cart come with demo data? 

Yes, and many of the product's features can be seen by installing with the demo data.  See [demo data](/user/first_steps/demo_data/) for details. 

--- 
<!-- please keep this at the end --> 
### Is there a list of features that Zen Cart currently offers? 
Yes - see [What features does Zen Cart offer?](/user/about_us/features/)

--- 

### Is there a roadmap of Zen Cart features planned for the future? 
There is a subforum called [Development Road Map](https://www.zen-cart.com/forumdisplay.php?4-Development-Road-Map).


