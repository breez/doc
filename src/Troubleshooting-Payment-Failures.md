# Troubleshooting Payment Failures

Breez is a non-custodial service that uses lnd and Neutrino under the hood.
This routing is done on the client side using the graph information provided by lnd. 

## No route found/Unable to find path/Timeout
If you are trying to pay an invoice, but you get **no route found**, **unable to find path** or timeout errors, please try the following:
* Make sure you are running the latest version of the app.
* Retry paying the invoice. lnd has something called **mission control** used in its routing algorithm. Mission control improves routing based on previous attempts, so simply retrying a payment might do the trick. 
* Make sure you are not trying to pay an invoice that will leave with a balance lower than the channel reserve value (600 sats for old Breez channels). Notice this includes fees, so if your current balance minus the invoice amount equals to the channel reserve, the payment will also fail because fees weren't taken into account.
* Try to Reset the Bitcoin Node in _Preferences > Network_ screen.
* Try refreshing the graph information. Click on _Update Graph_ from the top right menu of the _Preferences > Developers_ screen. Then, open Breez, keep it for a few minutes in the foreground and retry to pay. 
* Restart the Breez app and wait 30 seconds. Then, run _General > getinfo_ command in the _Preferences > Developers_ screen and check that all the channels are active (there's a 0 in numOfInactiveChannels).
* Check that Breez has the latest graph information. You can verify this by running the _General > getinfo_ command in the _Preferences > Developers_ screen. If the **synced_to_graph** property is set to **true**, then you are synced with the graph. In case the value is **false**, keep the app running in foreground for a couple of minutes till it syncs.
* Try resetting mission control by running the _Payments > resetmc_ command from the _Preferences > Developers_ screen and retry to pay.   
* Advanced users can also debug the routing path by running the _Payments > queryroutes_ command. 
