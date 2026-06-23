---
title: Class Methods
description: 
weight: 140
layout: docs
---

{{% wip %}}

A basic order total module `must` define the following method 

## public function process(): void;

An example from the `ot_total` order total module would be 

``` php
     public function process(): void
     {
      global $order, $currencies;
      $this->output[] = array('title' => $this->title . ':',
                              'text' => $currencies->format($order->info['total'], true, $order->info['currency'], $order->info['currency_value']),
                              'value' => $order->info['total']);
    }
```
