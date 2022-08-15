 ---
title: Square Errors and Issues 
description: Handling problems with Square WebPay
category: payment
weight: 10
---

Here are some common Square issues and the steps required to fix them. 

--- 

###  The provided OAuth access token has expired. You must renew the access token via the Renew Access Token endpoint. 

**Situation:**  
Customer is attempting to complete a purchase and paying via Square. They login, provide payment details, and click the Continue button, and they are shown this message. 

Or you get an email that says 

```
[ACCESS_TOKEN_EXPIRED]: The provided OAuth access token has expired. 
```

**Action to Resolve:** 

1. Open Square in your Zen Cart Admin by going to Admin > Modules > Payment > Square WebPay and clicking Edit.  **Be sure to click Edit before going further.**

1. Go to [https://connect.squareup.com/apps](https://connect.squareup.com/apps), click "Sign In" and open the app you are using for payment. 

1. Click the OAuth link on the left, then click the "Replace secret" button.

1. Click "Show" on the Production Application secret, and paste it into your Zen Cart Admin in the *Application Secret (OAuth)* field. 

### I get a white screen in Admin where Square Configuration should be!

If you forgot to click Edit in the first step, you may get a blank screen on the right hand side of the page when you finally do click Edit.

Here's what to do if that happens: 

- Edit the URL in the address bar, which will end with 

```
&action=edit
```

Change this to 

```
&action=delete 
```

and press Enter.  Press the "Remove Module" button and remove Square WebPay.  Then re-add it using the [reinstall instructions](/user/payment/square/#reinstalling-square-web-payments). 

###  Two Factor Authentication

Square uses two factor authentication (either via SMS or an authenticator app).  If you have multiple people accessing your Square dashboard (either multiple store admins or a store admin and a web developer), be sure that both of them can authenticate independently. (Without this, the one who can't authenticate will be locked out until the other one is available.)

As a short term solution, you can disable two factor authentication in the Square Dashboard by clicking on **Personal Information** under **Account**, then clicking **Disable 2-step verification**.
