# Coinbase Donate Button Tutorial
This mini-tutorial will guide you through the process of setting up a Coinbase account, creating a 'donate bitcoin' button and 
putting it into a website which will then be deployed via Heroku.

## Creating a Coinbase Account
Start by creating a Coinbase account. For the purposes of this tutorial we will be using a [sandbox account](https://sandbox.coinbase.com/). This is exactly like a regular coinbase account, except it gives you some fake bitcoins to play around with. sandbox accounts can send/receive bitcoins from other sandbox accounts. 

Once created, you should notice $1,000 USD worth of BTC in your account. 

### Merchant Tools

If you wish to accept BTC payments on your account, you must also set up a merchant profile. This option is not visible on the default dashboard for some reason, however you can access merchant tools via the following link:

[https://sandbox.coinbase.com/merchant_tools](https://sandbox.coinbase.com/merchant_tools)

Go to the profile tab and create your merchant account. You can enter fake information since this is just a sandbox account. 
Once created, you'll notice that the "Merchants" section is now visible on the left menu (see image below)

![Screen](http://i.imgur.com/mNhRY65.png)

### Create Donate Button

Finally, we can create a Donate button by going to the 'tools' tab in the merchant tools section.
Customize your button the way you want and press "Generate Button Code" when ready. This will create an HTML tag which you can embed in your own personal website (next section). 

If you wish to allow the donater to enter their own BTC amount, click "Advanced Options" at the bottom and checkmark the "Let the user change the amount" option. Then generate the button. 

