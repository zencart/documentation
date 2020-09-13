---
title: Testing PayPal Modules
description: 
weight: 10
---


## Testing PayPal Transactions

To test that PayPal is properly configured, you should test two methods:

1.  Test by paying for something using a PayPal account (not the same account as your store).
2.  Test by paying for something with a credit card WITHOUT creating or using a PayPal account for payment.

All of these tests are to be performed in "production" or "live" mode. Do NOT use a Sandbox for testing. _(If you don't know what this means, just proceed with testing.)_

### Testing using a PayPal account

1.  You need a second PayPal account to do this. PayPal allows you to have two accounts per person: one personal and one business. For this test, you will pay for your purchase using funds on account in your personal PayPal account. You will be paying money to your store account (and refunding it).
2.  Create or select a product which has a low price, such as $0.01 or maybe $1.00.
3.  Purchase that product.
4.  During checkout, choose the lowest-price shipping option.
5.  During checkout, choose PayPal.
6.  After the Checkout Confirmation screen, you'll be taken to the PayPal website to make payment.
7.  Enter your PERSONAL PayPal account username and password.
8.  Confirm the transaction.
9.  You will be returned to your store after completion.
10.  Verify that you received two or three emails: one from PayPal, one from the store to you as a customer, and one from the store to your _Admin_ address. If you did not receive the emails from the store within five minutes, then go to the Troubleshooting section of this document, above.
11.  Log in to your BUSINESS PayPal account and refund your test transaction.

### Testing without a PayPal account

To test payment by credit card without using a PayPal account, use these steps:

_(Before proceeding, find your credit cards, and select one that's not already associated with any PayPal account !!)_

1.  Create or select a product in your store which has a low price, such as $0.01 or maybe $1.00.
2.  Purchase that product.
3.  During checkout, choose the lowest-price shipping option.
4.  During checkout, choose PayPal.
5.  After the Checkout Confirmation screen, you'll be taken to the PayPal website to make payment.
6.  Underneath the login box for PayPal username/password, there is a link to Purchase without a PayPal account. Click that link.
7.  Fill in and/or confirm your personal information.
8.  Fill in your payment details including credit card number. (You should NOT use a credit card number that's already associated with any PayPal account !!)
9.  Confirm the transaction.
10.  You will be returned to your store after completion.
11.  Verify that you received two or three emails: one from PayPal, one from the store to you as a customer, and one from the store to your _Admin_ address. If you did not receive the emails from the store within five minutes, then go to the Troubleshooting section of this document, above.
12.  Log in to your BUSINESS PayPal account and refund your test transaction.

