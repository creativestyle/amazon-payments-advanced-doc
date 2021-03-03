.. _migration_checkout_v2:

Migration to Amazon Pay (Checkout v2)
===============================

Amazon Payments provides a new payment service: Amazon Pay (Checkout v2), which resolves some of the issues introduced by PSD2 directive and brings some new features improving the buyer shopping experience. The following guide provides necessary information on how to migrate to the new Amazon Pay (Checkout v2) extension.  

About Amazon Pay
----------------
Amazon Pay is an end-to-end payment solution that gives hundreds of millions of active Amazon customers a familiar, fast, and secure way to complete their purchase through your online store. Shoppers can use the address and payment information already stored in their Amazon account to check out - avoiding account creation or the need to re-enter their billing and shipping information. The performance is continually optimised by technology, learnings, and best practises from Amazon.  

Key Benefits
~~~~~~~~~~~~
* Reduce friction with a payment process that customers trust and can complete in minimal clicks
* Proactively notify customers when their order is on its way or has arrived with Amazon Alexa
* Rest assured with advanced fraud protection technology backed by Amazon
* Easily integrate Amazon Pay into your online store

Key Features
~~~~~~~~~~~~
* PSD2 compliant: Built-in support for strong customer authentication as required under PSD2
* Delivery Notifications: Proactively alert customers on the arrival status of physical goods orders via Amazon Alexa
* Multi-currency: Maintain the local currency experience across the shopping journey and help customers avoid currency conversion fees from their credit card issuer or bank
* Amazon Sign-in: Reduce friction during account creation and sign-in by offering a fast and secure way for customers to authenticate through Amazon. Shoppers with an active Amazon account don’t need to login again
* Automatic Decline Handling: Reduce lost sales with a consistent experience for customers to gracefully recover from a declined payment
* Payment Protection Policy: Protection against fraud-related chargebacks (check `User Agreement <https://pay.amazon.eu/help/201212430>`_ for more details)
* Amazon Pay A-to-z Guarantee: Increase customer confidence to complete purchase in your online store with extra assurance on the timeliness of delivery and order quality

Pre-migration steps
-------------------

* Create a backup of your shop before proceeding to install.
* If your shop is using compilation (you can check it in :menuselection:`System --> Tools --> Compilation`), disable it please before proceeding to install.


Getting the installation package
--------------------------------

Go to `Creativestyle Magento 1.x connect channel <https://connect.creativestyle.de/Creativestyle_AmazonCheckout>`_ and download the recent installation package of the extension. Unpack the downloaded file to your Magento root directory.

.. note::
   If you are using any VCS (git, svn, mercurial) for versioning your shop basecode, you can also commit the content of the downloaded file to the VCS repository and next deploy it to your shop.


.. _v2_installation-process:

Installation process
--------------------

After unpacking the downloaded installation package to your Magento root directory, please login to Magento admin, go to :menuselection:`System --> Cache Management` and flush Magento cache storage. If you have disabled compiler in pre-installation stage, you can go now to :menuselection:`System --> Tools --> Compilation`, recompile and enable compiler again. Next, logout from the Magento admin and login again.


.. _v2_activation:

Activation
----------

After the succesfull installation, you have to switch to the new payment service. If you have active previous Amazon Pay extension, the new one is disabled by default. To activate the new Amazon Pay (Checkout v2) go to :menuselection:`creativestyle --> Amazon Pay and Login with Amazon --> Settings` (or :menuselection:`System --> Configuration --> Amazon Payments` tab), on the top of the settings page you will find a control to switch between old Amazon Pay and the new one Amazon Pay (Checkout v2). Click :guilabel:`Amazon Checkout v2` button to activate the new payment service.

.. _v2_configuration:

Configuration
-------------

Amazon Pay (Checkout v2) extension for Magento 1.x provides automated settings migration routine. If your Amazon Pay extension for Magento 1.x is configured properly, most of your settings will be migrated automatically once you refresh the cache after the new extension installation. The following settings will be migrated from the previous Amazon Pay extension:

* Payment region
* Merchant ID
* Client ID
* Operation mode (live / sandbox)
* Payment action (authorize / authorize & capture)
* Display language
* Store name
* Soft descriptor

The only settings that **require manual input** are:

* Private key
* Public key ID

If you were using Alexa Delivery Notifications with the previous Amazon Pay, you should already have those settings, otherwise please login to Amazon Seller Central, generate new keys (or provide your own ones) and then paste Private key and assigned Public key ID to the appropriate input fields on the Amazon Checkout settings page.


Testing the new integration
---------------------------

After making sure that all settings are complete, you should test your installation. Only after successfully testing in the Sandbox mode you should switch to the live environment and make the button visible for all your sellers.

These tests should cover the different workflow that you encounter while processing orders. Both include the standard process like receiving an order, invoicing, shipment and alternative processes like canceling orders and refunding orders. Verify that all objects in your Magento admin are in the expected status and you correctly received all order information including the shipping address, contact details and the billing address (if applicable).

You should test also payment declines. To receive the complete testing scenarios contact Amazon Payments.
