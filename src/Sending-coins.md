#Sending Coins

In some cases, like a closed channel, you might receive funds to Breez's underlying Bitcoin wallet. If such cases, it is highly recommend to send the funds out to a BTC address ASAP.
Breez offers a UI, an _Unexpected Funds_ screen, to facilitate sending your coins out.
However, sometimes the funds are not enough to create a transaction with the recommended fees. 
To send out the coins with a minimal fee enter the following command in the _Preferences_ > _Developers_ screen:

sendcoins --sweepall=1 --addr=dest-btc-address --sat_per_byte=10
