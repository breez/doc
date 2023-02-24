# How to Get Started with Breez POS?

## What is Breez POS?
[Breez](https://breez.technology/technology.html) is a full-service, non-custodial Lightning app. Let’s break that down:
* **Lightning** is a bitcoin payment network that reduces transaction times from minutes to milliseconds and transaction fees from several dollars to a few cents or less. Lightning turns bitcoin from digital gold into digital currency while preserving all of the benefits that make bitcoin great. 
* **Non-custodial** means that Breez doesn’t take possession of users’ money. Many Lightning apps do take possession of their users’ money. They’re basically bitcoin banks. With a non-custodial app like Breez, all users are their own banks.
* **Full-service** means that Breez takes care of almost all the technical operations automatically and in the background. Things like [channel creation](https://medium.com/breez-technology/the-breez-release-candidate-getting-lightning-ready-for-the-global-takeover-b5d1f9756229), [inbound liquidity](https://medium.com/breez-technology/lightning-economics-how-i-learned-to-stop-worrying-and-love-inbound-liquidity-511d05aa8b8b), and [routing](https://medium.com/breez-technology/lightning-network-routing-privacy-and-efficiency-in-a-positive-sum-game-b8e443f50247) stay under the hood. (But Breez is also open source, so those interested in auditing the technology are welcome to do so!)

[Breez POS is short for our point-of-sale mode](https://medium.com/breez-technology/breezs-point-of-sale-mode-a-new-tool-for-the-day-after-tomorrow-fb8c0ba660a5). In other words, Breez works like a digital cash register for businesses and merchants who want to accept Lightning payments (in addition to its “standard” mode, which is like the digital version of a leather wallet for bitcoin, and a [next-generation podcast player](https://medium.com/breez-technology/podcasts-on-breez-streaming-sats-for-streaming-ideas-d9361ae8a627)). 
Now let’s look at how to set Breez up as a Lightning cash register for your business.
## How to get started with Breez?
The first step is to download the app. It’s available for [Android](https://play.google.com/apps/testing/com.breez.client) and [iOS](https://testflight.apple.com/join/wPju2Du7) (install TestFlight and click the link from your device). 

Breez can [back itself up](Backup-FAQ.md) automatically to Google Drive, iCloud or any WebDav server.

Note that each device runs its own Lightning node. You can run POS mode on as many devices as you’d like, but the balances will remain separate.

With the app open, click on the icon at the top left to find the **Point of Sale** mode.

## Setting up POS
Click that icon at the top left, and click **Point of Sale > POS Settings**.
### The Manager Password
In the **POS Settings**, you have the option to create a manager password. The manager password makes it impossible to send outgoing payments from the Breez app without authorization. Sales staff will only be able to receive payments from the device. Note that if you're using this option, you might also want to prevent access to Breez's backup, so using an external WebDav account (e.g. [Nextcloud](https://nextcloud.com/signup)) is recommended for this use case.
### The Items List
The _items list_ is a catalog of items for sale and their prices. There are two ways to add items to the list:
* To enter items one at a time, click on **Items** near the top of the main POS view, then on the **“+”** sign at the bottom right. Here you can enter the name of a single type of item, the price (displayed in the currency equivalent of your choice), and [the SKU](https://squareup.com/us/en/townsquare/stock-keeping-unit) (a unique internal identifier for that type of item; it’s optional).
* To enter many items at once, click on the calculator icon at the top left, then **Point of Sale > Preferences > POS Settings**, and then click on the three dots to the right of **Items List**, and then on **Import from CSV**. This will allow you to import a CSV file that you prepared in advance containing your items’ names, prices, and SKUs.
## Fiat Display	
Breez only sends and receives bitcoin, and for most transactions on Lightning, which tend to be for smaller amounts, the sum is usually displayed in Satoshis, a.k.a. sats (1 BTC = 100,000,000 sats). However, many merchants find it practical to be able to see (and tell customers) the value of the purchase displayed in the local fiat currency.

In the main POS view, the currency currently being displayed is visible on the right side (default is SAT). There is also a drop-down list of other currencies available to display. To add or remove currencies from this drop-down list, click on **Point of Sale > Preferences > Fiat Currencies**. Then simply check the currencies you would like to have in your drop-down menu and uncheck those you would like to omit.

The values displayed are from [yadio](https://yadio.io/), a respected outlet for exchange-rate data, and they’re updated in near real time. But remember: whatever currency value is currently being displayed, the payment itself is in bitcoin.
## Charging an Order
To compose the order, either add items from the item list or simply enter a sum in the keypad. Then click on **Charge** at the top of the main POS view. You will then see a QR code that the customer can scan with their Lightning app, that you can share directly from another app on your device, or that you can copy and paste where necessary.

On scanning that code or clicking on the shared/pasted invoice, the customer will see the invoice in their Lightning app and have the option to pay it and settle the transaction immediately.

Once you see the _Payment approved!_ animation in the Breez app on the merchant’s device, you can click on the printer icon to generate a receipt for the customer. To use a receipt printer in Android, try using [this driver](https://play.google.com/store/apps/details?id=me.shadura.escposprint&hl=en&gl=US). Note that you can also print past transactions via the **Transactions** screen.

## Sales Report
To view a daily/weekly/monthly report of your sales (for accounting purposes or others), click on the icon in the top left, and then click on **Transactions**. Click on the Report icon to display the report and the Calendar icon to change the selected date range. 

## Exporting Transactions
To view a list of the payments received in Breez, click on the icon in the top left, and then click on **Transactions**. Click on the three dots on the top right, then on **Export** to export a list of incoming payments in CSV format. To restrict the list to a certain period of time, click on the calendar icon to set a date range.

## Printing Receipts
To print a sale receipt, click on the print icon on the top right of the payment confirmation dialog. Alternatively, click on the icon in the top left, and then click on **Transactions**. Locate the sale to print, open it and click the top right print icon. 

Note: use [this driver](https://play.google.com/store/apps/details?id=me.shadura.escposprint) to print on a portable 58mm/80mm Bluetooth/USB thermal printer. 

## I want to learn more
* For more information on Lightning and Breez, check out our [blog](https://medium.com/breez-technology). 
* For more technical tips on how to get the most out of the app and perform common operations, check out our [documentation](Introducing-Breez.md).
* If you get stuck and can’t find the answer in any of our help literature, you can find us on [Telegram](https://t.me/breez_lightning) or send us an [email](mailto:contact@breez.technology).
* If you want to see some demonstration videos of the Breez POS mode in action made by our fans and users, here is a great [short one](https://www.youtube.com/watch?v=0knlEAnFTs0), and here is a longer, [more detailed one](https://www.youtube.com/watch?v=TjdS3fTOZ04).
