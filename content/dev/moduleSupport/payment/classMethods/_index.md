---
title: Class Methods
description: 
weight: 140
layout: docs
---

{{% wip %}}


Payment modules can define a number of methods to interact with the checkout/order flow.

While the `contract` for payment modules enforces that you must define all of these methods, the `PaymentConcerns` trait 

ensures that stubs for these methods are added to you payment module and you only need to override method in you module that are actually used.


## public function update_status();
## public function javascript_validation(): string;
## public function selection(): array;
## public function pre_confirmation_check();
## public function confirmation();
## public function process_button();
## public function clear_payments();
## public function before_process();
## public function after_order_create($orderId);
## public function after_process();
## public function admin_notification($orderId);

