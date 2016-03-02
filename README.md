# Coinbase Donate Button Tutorial
This mini-tutorial will guide you through the process of setting up a Coinbase account, creating a 'donate bitcoin' button and 
putting it into a website which will then be deployed via Heroku.


## Creating a Coinbase Account
Start by creating a [Coinbase account](https://www.coinbase.com/signup). If you wish, you may also create a [sandbox account](https://sandbox.coinbase.com/) instead. This is exactly like a regular coinbase account, except it gives you some fake bitcoins to play around with so you don't have to wait for funds to be transfered from your bank. Sandbox accounts can send/receive fake bitcoins only from other sandbox accounts. 
If you opt for the sandbox option, you'll notice $1,000 USD worth of BTC in your account once created. 

### Merchant Tools
If you wish to accept BTC payments on your account, you must also set up a merchant profile. This option is not visible on the default dashboard for some reason, however you can access merchant tools via the following link:

[https://coinbase.com/merchant_tools](https://sandbox.coinbase.com/merchant_tools)

If you're using a sandbox account, use [https://coinbase.com/merchant_tools](https://sandbox.coinbase.com/merchant_tools) instead.

Go to the profile tab and create your merchant profile. You can enter fake information for now if you do not wish to give your SSN/SIN number.
Once created, you'll notice that the secret "Merchants" section is now visible on the left menu (see image below)

![Screen](http://i.imgur.com/mNhRY65.png)

### Create Donate Button
Finally, we can create a Donate button by going to the 'tools' tab in the merchant tools section.
Customize your button the way you want and press "Generate Button Code" when ready. This will create an HTML tag which you can embed in your own personal website (next section). 

If you wish to allow the donater to enter their own BTC amount, click "Advanced Options" at the bottom and checkmark the "Let the user change the amount" option. Then generate the button. 


## Deploy a Website with Heroku
[Heroku](https://www.heroku.com/) is a platform for managing cloud-based apps. It allows you to deploy and test your web app easily without having to worry about managing servers. 

### Set up Heroku
Start by creating a [Heroku Account](https://toolbelt.heroku.com/).

Since we're only interested in a simple HTML website, we'll be using PHP as our server-side language. We first need to install a few things.

#### 1. Install [PHP](http://php.net/)

#### 2. Get [Composer](https://getcomposer.org/)
Composer is a dependency manager for PHP. We will need it to obtain the heroku dependencies for our proect. 
You can download and install composer from the terminal by running the following commands:

```
$ php -r "readfile('https://getcomposer.org/installer');" > composer-setup.php
$ php -r "if (hash('SHA384', file_get_contents('composer-setup.php')) === 'fd26ce67e3b237fffd5e5544b45b0d92c41a4afe3e3f778e942e43ce6be197b9cdc7c251dcde6e2a52297ea269370680') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); }"
$ php composer-setup.php
$ php -r "unlink('composer-setup.php');" 
```



