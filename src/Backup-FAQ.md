# Backup FAQ

### Important note
Restore your wallet only if you've lost your device or accidentally uninstalled Breez. If you have problems with Breez, most likely restoring from backup won't fix them.

### Does Breez have a backup seed?
Breez isn't an on-chain wallet, so a seed phrase in this case isn't enough for backup/restore. Breez is a Lightning wallet and thus requires an on-going channels state backup to the cloud (Google Drive, iCloud, Nextcloud or any WebDav server). In Breez, backup is automatically triggered after BTC address generation and Lightning payments.
### Why does Breez require cloud access?
Breez is a Lightning wallet and thus requires an on-going channel state backup to the cloud. From a security standpoint, there are many advantages in saving these backups in a major 3rd-party cloud storage provider. In addition, your backup isn't dependent on Breez server availability.
### Can Google/Apple access my backup information?
Both companies are not being fully transparent regrading their data encryption. That's the reason Breez is offering an option to add an additional encryption to the cloud backup data. To generate a backup phrase, activate **Encrypt Backup Data** in the **Preferences > Security & Backup** screen.
### I wrote down my encryption key, but I can't restore the data in other wallets. Why?
Breez's encryption key is not a wallet seed. It is used as a key to encrypt the data stored in the cloud. In order to restore the information, you need access to the cloud data and the key to decrypt it. Currently, you can only restore the information via the Breez app.
### How do I restore from backup?
You can restore from backup after installing Breez. You'll see a **Restore from Backup** link under the **Let's Breez** button in the opening screen.
DO NOT RUN YOUR OLD BREEZ APP AFTER RESTORING ON A NEW DEVICE.
### Can I view the backup files in Google Drive/iCloud?
Backup files are stored in a private data directory accessible only via the Breez app.
You can see manage it via Drive: **Settings > Manage Apps** in the browser.
### Can I switch from Android to iOS and vice versa?
Yes, by storing your backup in Google Drive or Remove Server which are supported on both platforms. To switch cloud provider, use the **Store Backup Data in** setting in the **Preferences > Security & Backup** screen.
### I can't authenticate to Nextcloud. What can I do?
Create an [app password](https://docs.nextcloudpi.com/en/two-factor-authentication-for-nextcloud/#:~:text=To%20add%20an%20App%20Password,until%20you%20find%20App%20passwords%20), enter the new app credentials and retry.
### Do you support pCloud?
Yes, but a business account is required (with WebDav support). URL should be entered in the below format:
* pCloud (US)- https://webdav.pcloud.com
* pCloud (EU) – https://ewebdav.pcloud.com
### Breez says my key is wrong. What can I do?
If Breez says your keys is wrong, then it's wrong. Unfortunately, there's not much that can be done in this case. Please validate that you've entered the words in the right order and that all the words are spelled correctly. It happened (more than once) that users tried to entered a word that [was similar the right one](https://github.com/breez/breezmobile/issues/615#issuecomment-955764720). 
