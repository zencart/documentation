---
title: Configuration Errors
description: 
weight: 100
layout: docs
---

{{% wip %}}

# Introduction

The new module support infrastructure allows you to define methods to capture errors in the configuration of a module 
and display these errors in the admin title for the module.

If the errors are considered `fatal` the system will also ensure that the module cannot be enabled until the errors are fixed.

Two methods are used which you can add to your module.

`checkNonFatalConfigureStatus` and `checkFatalConfigureStatus`

some examples. 

The moneyorder payment module defines a `checkNonFatalConfigureStatus` method

``` php 
    protected function checkNonFatalConfigureStatus(): void
    {
        if ($this->getDefine('PAYTO') == 'the Store Owner/Website Name' || $this->getDefine('PAYTO') == '') {
            $this->configureErrors[] = '(not configured - needs pay-to)';
        }
    }
```

The Stripe Pay module defines a `checkFatalConfigureStatus` method


```php 
    protected function checkFatalConfigureStatus(): bool
    {
        $configureStatus = true;
        $toCheck = 'LIVE';
        if ($this->getDefine('MODE') == 'Test') {
            $toCheck = 'TEST';
        }
        if ($this->getDefine($toCheck . 'PUB_KEY') == '' || $this->getDefine($toCheck . '_SECRET_KEY') == '') {
            $this->configureErrors[] = sprintf('(not configured - needs %s publishable and secret key)', $toCheck);
            $configureStatus = false;
        }
        return $configureStatus;
    }
```


