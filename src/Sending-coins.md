# Using the _sendcoins_ command

_Please note that the functionality described here is best left to advanced users._

In some cases, like channel closures, users' funds might be deposited automatically into Breez's built-in (on-chain) Bitcoin wallet. If this occurs, we strongly recommend sending the funds to a secure BTC address as soon as possible. Breez offers an _Unexpected Funds_ screen to facilitate this process.

However, the funds may not suffice to initiate a transaction and cover the fees incurred. 
To send the funds with a minimal fee, enter the following command in the **Preferences > Developers** screen:

<code>
sendcoins --sweepall=1 --addr=dest-btc-address --sat_per_byte=10
</code>
