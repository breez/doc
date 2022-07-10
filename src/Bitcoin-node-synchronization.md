# Bitcoin node synchronization

By default, Breez uses this node to connect to the Bitcoin network:

<code>bb1.breez.technology</code>

However, any Bitcoin node that supports block filters (BIP 157) can be used instead.
Check out [this site](https://bitnodes.io/nodes/?q=NODE_COMPACT_FILTERS) to find alternative nodes. 

### My sync is stuck at 0%, what can I do?
* Try to reset the Bitcoin node in the _Preferences> Network_ screen. 
* Make sure there is no VPN running or other software that might interfere with the network traffic.
* Try to configure an alternative node from the site specified above. Choose a regular IP address, not a Tor (.onion) address. 
