---
title: Configuration Settings
description: 
weight: 100 
layout: docs
---

{{% wip %}}

The default configuration settings for a basic order total module are :-

``` php 
    protected function setCommonConfigurationKeys(): array
    {
        $configKeys = parent::setCommonConfigurationKeys();
        $key = $this->buildDefine('INC_SHIPPIMG');
        $configKeys[$key] = [
            'configuration_value' => 'false',
            'configuration_title' => 'Include Shipping',
            'configuration_description' => 'Include Shipping value in amount before discount calculation?',
            'configuration_group_id' => 6,
            'sort_order' => 1,
            'set_function' => 'zen_cfg_select_option(array(\'true\', \'false\'), ',
        ];
        $key = $this->buildDefine('INC_TAX');
        $configKeys[$key] = [
            'configuration_value' => 'true',
            'configuration_title' => 'Include Tax',
            'configuration_description' => 'Include Tax value in amount before discount calculation?',
            'configuration_group_id' => 6,
            'sort_order' => 1,
            'set_function' => 'zen_cfg_select_option(array(\'true\', \'false\'), ',
        ];
        $key = $this->buildDefine('CALC_TAX');
        $configKeys[$key] = [
            'configuration_value' => 'Standard',
            'configuration_title' => 'Re-calculate Tax',
            'configuration_description' => 'How to Re-calculate Tax',
            'configuration_group_id' => 6,
            'sort_order' => 1,
            'set_function' => 'zen_cfg_select_option(array(\'None\', \'Standard\', \'Credit Note\'), ',
        ];
        $key = $this->buildDefine('TAX_CLASS');
        $configKeys[$key] = [
            'configuration_value' => '0',
            'configuration_title' => 'Tax Class',
            'configuration_description' => 'Use the following tax class when treating module as a Credit Note.',
            'configuration_group_id' => 6,
            'sort_order' => 1,
            'use_function' => 'zen_get_tax_class_title',
            'set_function' => 'zen_cfg_pull_down_tax_classes(',
        ];
        return $configKeys;
    }
```

