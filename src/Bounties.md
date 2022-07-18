# Bounties

## Active Bounties

Breez is offering bounties for the tasks listed below. Relevant PRs must be reviewed and merged before developers can claim the bounty listed. To inquire about status of a bounty, to contribute to a bounty, or to propose a new bounty, [please send us an email](mailto:contact@breez.technology). 

Please read the [Overview for Developers](https://doc.breez.technology/Overview-for-Developers.html) before getting started. The Tor implementation should probably be in the go layer (Breez library). Please feel free to open issues and communicate with us to figure out the right architecture. 

## Past Bounties
### Tor support
**Description**: add support for Tor. There are few reasons we want to support Tor, mainly:
1. We want to allow people to connect to other Lightning nodes using Tor (see [Opening Channels](https://doc.breez.technology/Opening-Channels.html)).
2. Users in some countries cannot use the app because their ISPs seem to block the on-chain traffic (Breez uses Neutrino BIP 157 to communicate with the chain).
3. Many people use Umbrel to run Bitcoin nodes, and Umbrel uses Tor. We want to allow these users to connect to their home nodes instead of relying on the Breez node (via the **Preferences > Network** screen).
4. Backup to Nextcloud/WebDav over Tor.

**Payout**: 10M sats (0.1 btc) for iOS and Android.

**Bounty patrons**: Breez (10M sats).

**Bounty claimed by** [Nick Ochiel](https://github.com/nochiel) (5M sats).

### LNURL-Pay support
**Description**: add support for LNURL-Pay links and QRs. Support should follow a similar architecture to existing supported LNURLs, like LNURL-Withdraw and be tested against services using LNURL-Pay, such as Zebedee.   

**Payout**: 1.5M sats (0.015 btc)

**Bounty claimed by** [Nick Ochiel](https://github.com/nochiel) 💪💥

**Bounty patrons**: Breez (1.2M sats), [Alex Waltz](https://twitter.com/raw_avocado) (172,480 sats), [alex giurgiu](https://twitter.com/nustiudinastea) (40K sats), anonymous donors (15K sats), Daniel F (10K sats), B0B0 (1000 sats).

## Donations
To donate to our bounties, please use our [tippin' page](https://tippin.me/@Breez_Tech). Add the bounty name and your Twitter handle (if you want to be credited).

## Developer resources
* [Overview for Developers](Overview-for-Developers.md)
