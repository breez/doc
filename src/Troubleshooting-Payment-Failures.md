# Troubleshooting Payment Failures

Breez is a non-custodial service that uses lnd and Neutrino under the hood.
Routing is done on the client side using the graph information provided by lnd. 

## No route found/Unable to find path/Timeout
If you are trying to pay an invoice, but you see an error like **no route found**, **unable to find path** or timeout errors, please try the following:
* Make sure you are running the latest version of the app.
* Retry paying the invoice. lnd has a function called **mission control** in its routing algorithm. Mission control improves routing based on previous attempts, so simply retrying a payment might do the trick. 
* Don't exhaust the channel reserve value (600 sats for old Breez channels). No invoice plus fees may  reduce the channel balance below this amount.
* Reset the Bitcoin Node by clicking the **Reset** button on the **Preferences > Network** screen.
* Try refreshing the graph information. Click on three dots at the top right of the **Preferences > Developers** menu, then on **Update Graph**. Then re-open Breez, keep it in the foreground for a few minutes, and retry the payment. 
* Restart the Breez app and wait 30 seconds. Then, click on the **getinfo** command in the **Preferences > Developers > General** menu to check whether all the channels are active, which is the case when there's a "_0_" in the "_numOfInactiveChannels_" line.
* Check that Breez has the latest graph information. You can verify this by clicking on the  **getinfo** command in the **Preferences > Developers > General** menu. If the _synced_to_graph_ line of the output indicates _true_, then your node is synced with the graph. In case the value is _false_, keep the app running in foreground for a couple of minutes until it syncs.
* Try resetting mission control by running the **resetmc** command from the **Preferences > Developers > Payments** menu and retry the payment.   
* Advanced users can also debug the routing path by running the **Developers > Payments > queryroutes** command. 
