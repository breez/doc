# Running Breez in simnet

Developing Breez mobile requires Breez backend services to be up and running. As there are a few services that are configured to run in parallel, configuring everything from scratch might be tedious. Although we recommend that developers familiarize themselves with each of the services and the overall architecture, we do provide a quick solution to run all Breez services in a simnet environment that developers can connect to from their self-compiled Breez mobile app.
These are the required backend services:
* LSP node: a Lightning node that opens a channel with the Breez mobile app.
* LSPD: an LSP daemon that interacts with Breez server and provides information about its node and services.
* Breez Server: the main service that interacts with the Breez mobile app.
* btcd/bitcoind: a Bitcoin node utilizing Neutrino (BIP 157).
* SubSwap node: a node that provides submarine-swap services ([adding funds to Breez](https://doc.breez.technology/Adding-Funds-via-Submarine-Swaps.html) via an on-chain address).

### Running Breez's simnet cluster
We've created a [docker-compose](https://github.com/breez/breez/blob/master/docker/dev-simnet.yml) file that configures and runs all the backend services. It exposes the necessary endpoints to the Breez mobile app, similar to a production environment.
This [script](https://github.com/breez/breez/blob/master/docker/start-dev-env.sh) runs the cluster. Before running this script, please configure it as follows:
1. Change the DEV_HOST_IP env variable to the host IP address (it should run in the same network as the mobile device).
2. Change the TEST_DIR value to a directory where all the containers' persistent data will be stored.

### Connecting from mobile:
To connect from mobile, these configuration files should be placed under the _conf_ directory:
* [breez.con](https://github.com/breez/breezmobile/blob/master/conf/simnet/breez.conf): replace the <DEV_HOST_IP> with your cluster IP address.
* [lnd.conf](https://github.com/breez/breezmobile/blob/master/conf/simnet/lnd.conf): replace the <DEV_HOST_IP> with your cluster IP address.

### Receiving payments
A container named **alice** is configured as part of the cluster, and it runs another Breez client app. This container should be used to send payments to your mobile node using the command line.
Run the following commands in order to open a channel and receive a payment:
* From your mobile app, generate a payment request via **Receive > Receive via Invoice**.
* From your terminal:
1. Retrieve the LSP node pubkey: 
> `docker exec dev-breez "/lnd/lncli" -network=simnet getinfo`
2. Generate 6 blocks: 
> `docker exec dev-btcd /start-btcctl.sh generate 6`
3. Generate a btc address for Alice: 
> `docker exec dev-alice "/go/bin/lncli" --network simnet newaddress np2wkh`
4. Send coins from the LSP node to Alice: 
> `docker exec dev-breez "/lnd/lncli" -network=simnet sendcoins <alice_address> 20000000`
5. Generate 6 blocks: 
> `docker exec dev-btcd /start-btcctl.sh generate 6`
6. Open a channel from Alice to the LSP node: 
> `docker exec dev-alice "/go/bin/lncli" -network=simnet openchannel --node_key <lsp pubkey> --local_amt=200000 --connect=10.5.0.3:9735 --private`
7. Generate blocks to confirm the channel: 
> `docker exec dev-btcd /start-btcctl.sh generate 6`

Note this script uses jq, which must installed in your environment.

8. Send a Lightning payment: 
> `docker exec dev-alice "/go/bin/lncli" -network=simnet payinvoice --pay_req <payment_request>`

If the test is successful, the LSP node should open a channel to your mobile app and send the payment. You should see the payment in the transactions list in your mobile app.
