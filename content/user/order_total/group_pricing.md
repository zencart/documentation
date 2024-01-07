---
title: Group Pricing
description: Discounts for select customers
category: order_total
weight: 10
---

Group Pricing allows you to offer a percent-off discount to specific customers.  Customers are organized into groups according to their discount. 

If you want to offer a group discount, you need to first enable group pricing

Go to: [Admin > Modules > Order Total](/user/admin_pages/modules/order_total/) and select Group Pricing (ot_group_pricing).   
If it's not already installed, click Install to enable it.  

Note that for users of [wholesale pricing](/user/products/wholesale_pricing/): customers may be assigned to wholesale levels or group pricing groups but not both. 

## Group Pricing

Go to [Admin > Customers > Group Pricing](/user/admin_pages/customers/group_pricing/). 

Next, you create a pricing group by clicking *Insert*.  (Or *Edit* to edit an existing pricing group.)  
Fill in the details.  

## Assigning Customers to Pricing Groups 

Go to [Admin > Customers > Customers](/user/admin_pages/customers/customers/) and find the customer you want to 
add to a group.  Edit the customer, and set the *Discount Pricing Group*
field at the bottom of the screen.  Press *Update*.

The customer will now be entitled to the Group Discount you have configured.  The discount will be shown as a line item under the Subtotal at checkout time. 

## Other Uses for Pricing Groups 
While not ideal, there is the possibility that custom code can use customer pricing groups for other purposes as well.  For example, the [Invoice Payment Method plugin](https://www.zen-cart.com/downloads.php?do=file&id=131) checks the customer's group and only becomes visible if their group name begins with the string "invoice_". 

## Display of Group Discounts 
Group Discounts are shown in the order summary on the checkout payment and
 checkout confirmation pages.  See [price reductions](/user/products/price_reductions/) for details. 
