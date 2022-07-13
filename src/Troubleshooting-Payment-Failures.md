# Troubleshooting Payment Failures

Breez is a non-custodial service that uses lnd and Neutrino under the hood.
Routing is done on the client side using the graph information provided by lnd. 

## No route found/Unable to find path/Timeout
If you are trying to pay an invoice, but you see an error like **no route found**, **unable to find path** or timeout errors, please try the following:
* Make sure you are running the latest version of the app.
* Retry paying the invoice. lnd has a function called **mission control** in its routing algorithm. Mission control improves routing based on previous attempts, so simply retrying a payment might do the trick. 
* Don't exhaust the channel reserve value (600 sats for old Breez channels). No invoice plus fees may  reduce the channel balance below this amount.
* Try to Reset the Bitcoin Node in _Preferences > Network_ menu.
* Try refreshing the graph information. Click on _Update Graph_ from the top right menu of the _Preferences > Developers_ screen. Then, open Breez, keep it in the foreground for a few minutes and retry the payment. 
* Restart the Breez app and wait 30 seconds. Then, click on _getinfo_ command in the _Preferences > Developers>General_ menu to check whether all the channels are active, which is the case when there's a "0" in "numOfInactiveChannels" line.
* Check that Breez has the latest graph information. You can verify this by clicking on the  _getinfo_ command in the _Preferences > Developers>General_ menu. If the **synced_to_graph** line of the output indicates **true**, then your node is synced with the graph. In case the value is **false**, keep the app running in foreground for a couple of minutes until it syncs.
* Try resetting mission control by running the _resetmc_ command from the _Preferences > Developers > Payments_ menu and retry the payment.   
* Advanced users can also debug the routing path by running the _Payments > queryroutes_ command. 
