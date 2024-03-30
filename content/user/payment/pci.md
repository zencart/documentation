---
title: PCI 
description: What is PCI and how does it affect me?
category: payment
weight: 2
---

Please note: the following article is only opinion, and should not be relied upon as "official". Official PCI DSS information should be obtained from the PCI Security Council directly or from one of their authorized Assessors.

## What is PCI? 

The PCI Data Security Standards (PCI DSS, or sometimes just PCI) are a set of best practices designed to protect cardholder data and prevent fraud.  Any retailer who accepts credit cards must uphold the PCI rules as part of their account agreement.

You can read the full [PCI Agreements](https://docs-prv.pcisecuritystandards.org/PCI%20DSS/Standard/PCI-DSS-v4_0.pdf) by providing your name and company name, or you can read a [summary of PCI DSS](https://en.wikipedia.org/wiki/Payment_Card_Industry_Data_Security_Standard) on Wikipedia. 

## What is PCI DSS 4.0? 
PCI DSS 4.0 is the latest version of the standard, which came into effect March 31, 2004. 

## Am I subject to PCI DSS rules? 

If you process credit cards, you are subject to PCI rules. 

## How do I reduce my exposure to PCI DSS risk? 

As a general rule, the less handling of credit cards your site does, the better.  Payment by [PayPal Express](/user/payment/paypal_express_checkout/), for example, happens completely off your site.  Modules like [PayPal RESTful](/user/payment/paypal_restful/) handle card data but use modern techniques to minimize the transmission of this data.  Modules like [Authorize.net AIM](/user/payment/authorizenet_aim/) handle and transmit credit card data, and their use may necessitate a PCI compliance scan if your processor requests one. 

## What is a PCI Compliance Scan? 

A PCI Compliance Scan is a probe of your website that looks for potential issues that could create security vulnerabilities.  If your payment processor wants you to do a PCI Scan, they will tell you the specifics they want, and typically refer you to one or two specific services.  

Be cautious about unsolicited email from PCI Scan providers telling you your site is not secure and that you need their services.  Again, let the requirements of your payment processor guide you.

Even the selected service providers of payment processors are not perfect, and their scans may turn up a [false positive](https://en.wikipedia.org/wiki/False_positives_and_false_negatives) - something that appears to be a problem but is not.  You will need to work with your hoster and your developer to resolve such misunderstandings when they occur. 

## What are my responsibilities?  

The PCI DSS standards are large, complex and subject to interpretation.  Only a qualified assessor can tell you if you're doing *everything* you need to do.  But some basic requirements can be stated easily: 

- Be sure your software is up to date.  [Upgrading](/user/upgrading/) is part of your responsibility  so that you are running the latest versions of PHP and Zen Cart. 
- Don't disable any of the PCI related configuration items provided by Zen Cart.  For example, don't disable [strong password requirements](/user/admin_pages/configuration/all/#padss_strong_password_rules_enforced).
- Don't store credit card numbers in your database.  The old [manual card](/user/payment/why_not_manual/) modules should no longer be used, and any stored card numbers should be deleted.

