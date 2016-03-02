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
Composer is a dependency manager for PHP. We will need it to obtain the Heroku dependencies for our project. 
You can download and install composer from the terminal by running the following commands:

```
$ php -r "readfile('https://getcomposer.org/installer');" > composer-setup.php
$ php -r "if (hash('SHA384', file_get_contents('composer-setup.php')) === 'fd26ce67e3b237fffd5e5544b45b0d92c41a4afe3e3f778e942e43ce6be197b9cdc7c251dcde6e2a52297ea269370680') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); }"
$ php composer-setup.php
$ php -r "unlink('composer-setup.php');" 
```

This will generate a composer.phar file which you will be able to use in any PHP project to install dependencies. 

#### 3. Obtain the [Heroku Toolbelt](https://toolbelt.heroku.com/)
This will help you manage and deploy Heroku Apps.
Once downloaded, you can enter your Heroku credentials via the following command:

```
$ heroku login
```

You are now ready to create your first Heroku App.

### Create Heroku App 

#### Setup
create a folder where your Heroku project will reside. Create another folder inside which will contain the actual code for your website:

```
$ mkdir myapp
$ cd myapp
$ mkdir web
```

Create a file called composer.json and populate it with the following code:

```json
{
  "require-dev" : {
  	"heroku/heroku-buildpack-php": "*"
  }
}
```

This file is what Composer uses to download the dependencies. 
In order to download the dependancies, copy the composer.phar file we generated earlier to this 'myapp' folder and run the following command:

```
$ php composer.phar install
```

After the dependancies are created, create an index.php file in the 'web' folder, populate it with the following code:

```PHP
<?php include_once("index.html");?>
```

All this script does is tell the server to load the index.html file when someone accesses the website. Create an index.html file in the same 'web' folder and insert the code generated for your Donate Button inside the body. 
The following is just an example, you will use your own <a> link when populating your own index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Random title</title>
</head>
<body>
	<!-- Insert your Donate Button here -->
	<a class="coinbase-button" data-code="b30a0e523fc911c51e31badbd1e8b52c" data-button-style="custom_large" href="https://www.coinbase.com/checkouts/b30a0e523fc911c51e31badbd1e8b52c">Donate BTC!</a><script src="https://www.coinbase.com/assets/button.js" type="text/javascript"></script>
</body>
</html>
```

Finally, before we can deploy on Heroku, we need to create one more file called Procfile in the main 'myapp' folder.
Put the following line in this file:

```
web: vendor/bin/heroku-php-apache2 web/
```

When your app is deployed on Heroku, this file tells the server how to run your app. In this case, it uses an apache server to run whatever is inside the web folder.

#### Deploy!
You are finally ready to deploy your project. 

Initialize a git repository:

```
$ git init
$ git add . && git commit -m "Initial Commit"
```

use the following command to link to a Heroku Remote:

```
$ heroku create
```

Deploy your project by pushing to the Heroku remote:

```
$ git push heroku remote
```

View your project in a browser!

```
$ heroku open
```







