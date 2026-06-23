---
title: Class Methods
description: 
weight: 140
layout: docs
---

{{% wip %}}

order total credit class  modules can define a number of methods to interact with the checkout/order flow.

While the contract for these modules enforces that you must define all of these methods, the `OrderTotalCCConcerns` trait

ensures that stubs for these methods are added to you module and you only need to override methods in you module that are actually used.


## public function process(): void;
## public function credit_selection(): false|array;
## public function update_credit_account($i): void;
## public function collect_posts(): void;
## public function pre_confirmation_check(bool $returnOrderTotalOnly = false): void;
## public function apply_credit(): void;
## public function clear_posts(): void;

