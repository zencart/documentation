---
title: Class Methods
description: 
weight: 140
layout: docs
---

{{% wip %}}

Shipping modules `must` define the following method.

## public function quote(string $method): array;

An example from the `flat` shipping module would be 

``` php 
    function quote($method = ''): array
    {
        global $order;

        $this->quotes = [
            'id' => $this->code,
            'module' => MODULE_SHIPPING_FLAT_TEXT_TITLE,
            'methods' => [
                [
                    'id' => $this->code,
                    'title' => MODULE_SHIPPING_FLAT_TEXT_WAY,
                    'cost' => MODULE_SHIPPING_FLAT_COST,
                ],
            ],
        ];
        if ($this->tax_class > 0) {
            $this->quotes['tax'] = zen_get_tax_rate($this->tax_class, $order->delivery['country']['id'], $order->delivery['zone_id']);
        }

        if (!empty($this->icon)) {
            $this->quotes['icon'] = zen_image($this->icon, $this->title);
        }

        return $this->quotes;
    }
```

