---
title: Square Error Messages
description: Understanding the various Square errors
category: payment
weight: 10
---

Here are some common Square errors and the steps required to fix them. 

--- 

###  The provided OAuth access token has expired. You must renew the access token via the Renew Access Token endpoint. 

**Situation:**  
Customer is attempting to complete a purchase and paying via Square. They login, provide payment details, and click the Continue button, and they are shown this message. 

**Action to Resolve:** 

1. Open Square in your Zen Cart Admin by going to Admin > Modules > Payment > Square WebPay and clicking Edit.

1. Login at [https://connect.squareup.com/apps](https://connect.squareup.com/apps) and open the app you are using for payment. 

1. Click the OAuth link on the left, then click the "Replace secret" button.

1. Click "Show" on the Application secret, and paste it into your Zen Cart Admin. 



