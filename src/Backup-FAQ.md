# Backup FAQ

### Important note
Restore your wallet only if you've lost your device or accidentally uninstalled Breez. Restoring from backup is unlikely to fix problems you may be experiencing with the app.

### Does Breez have a backup seed?
Unlike an on-chain wallet, Breez requires continuous backups of the user's current channel states, which necessitates cloud storage (e.g. Google Drive, iCloud, Nextcloud or any WebDav server) rather than a simple seed phrase to backup/restore. In Breez, an encrypted backup is triggered automatically after whenever a BTC address is generated or a Lightning payment event occurs.
### Why does Breez require cloud access?
As a Lightning wallet, Breez requires continuous backups of the user's channel states backup to the cloud. From a security standpoint, there are many advantages to saving these backups in a major third-party cloud-storage provider. Even better, with cloud backup users' backup files don't rely on the availability of the Breez server.
### Can Google/Apple access my backup information?
Neither company is fully transparent about their data encryption. That's why Breez offers an additional layer of encryption to data backed up in the cloud. To generate a backup phrase, activate _Encrypt Backup Data_ in the _Preferences > Security & Backup_ screen.
### Why can't I restore my data in other wallets despite entering the correct encryption key?
Breez's encryption key is not a wallet seed. Rather, the key encrypts the user's data stored in the cloud. In order to restore the information, users need access their cloud backups and decrypt them with their individual keys. Currently, Breez backups can only be restored from within the Breez app.
### How do I restore from backup?
You can restore from backup inside the Breez app. You'll see a **Restore from Backup** link under the **Let's Breez** button on the opening screen.
**DO NOT RUN A PREVIOUS INSTANCE OF BREEZ AFTER RESTORING ON A NEW DEVICE.**
### Can I view the backup files in Google Drive/iCloud?
Backup files are stored in a private data directory accessible only through the Breez app.
Google Drive users can manage their Breez storage by opening Google Drive in a browser and clicking on: **Settings > Manage Apps**.
### Can I switch from Android to iOS and vice versa?
Yes, by storing your backup in Google Drive or on a remove server that is supported on both platforms. To switch cloud provider, use the **Store Backup Data in** setting on the **Preferences > Security & Backup** screen.
### I can't authenticate to Nextcloud. What can I do?
Create an [app password](https://docs.nextcloud.com/server/latest/admin_manual/configuration_user/two_factor-auth.html), enter the new app credentials and retry.
### Do you support pCloud?
Yes, but a business account is required (with WebDav support). The URL should be entered in the following format:
* pCloud (US): <code>https://webdav.pcloud.com</code>
* pCloud (EU): <code>https://ewebdav.pcloud.com</code>
### Breez says my key is wrong. What can I do?
If Breez says you're entering an incorrect key, then the key you are entering does not match what is saved in the software. Unfortunately, there are few means to recover a key that was recorded inaccurately. Please ensure that you've entered the words in the right order and that all the words are spelled correctly. More than once, the obstacle has turned out to be a small error in entering the words, [even a single letter](https://github.com/breez/breezmobile/issues/615#issuecomment-955764720). 
