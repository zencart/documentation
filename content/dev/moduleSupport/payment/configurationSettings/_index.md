---
title: Configuration Settings
description: 
weight: 100 
layout: docs
---

{{% alert title="Warning" color="warning" %}}
The documentation in this section is Work in progress and relates to features that might not be available yet.
{{% /alert %}}

The default configuration settings for a payment module are :-

``` php 
    protected function setCommonConfigurationKeys(): array
    {
        $configKeys = [];
        $key = $this->buildDefine('STATUS');
        $configKeys[$key] = [
            'configuration_value' => 'False',
            'configuration_title' => 'Enable this module',
            'configuration_description' => 'Do you want to accept payments using this module',
            'configuration_group_id' => 6,
            'sort_order' => 1,
            'set_function' => "zen_cfg_select_option(array('True', 'False'), ",
        ];
        $key = $this->buildDefine('SORT_ORDER');
        $configKeys[$key] = [
            'configuration_value' => 0,
            'configuration_title' => 'Sort order of display.',
            'configuration_description' => 'Sort order of display. Lowest is displayed first.',
            'configuration_group_id' => 6,
            'sort_order' => 1,
        ];
        $key = $this->buildDefine('ZONE');
        $configKeys[$key] = [
            'configuration_value' => 0,
            'configuration_title' => 'Payment Zone',
            'configuration_description' => 'If a zone is selected, only enable this payment method for that zone.',
            'configuration_group_id' => 6,
            'sort_order' => 1,
            'set_function' => "zen_cfg_pull_down_zone_classes(",
        ];
        $key = $this->buildDefine('DEBUG_MODE');
        $configKeys[$key] = [
            'configuration_value' => '--none--',
            'configuration_title' => 'Use debug mode',
            'configuration_description' => 'Debug Mode adds extra logging to file, email and console output',
            'configuration_group_id' => 6,
            'sort_order' => 1,
            'set_function' => "zen_cfg_select_multioption(array('File', 'Email', 'BrowserConsole'), ",
        ];
        return $configKeys;
    }
```
