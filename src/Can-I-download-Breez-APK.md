# Can I download the Breez APK?
Yes. It requires Android 7.0 or greater and a 64-bit device. [Click here to download.](https://github.com/breez/breezmobile/releases/download/0.15.lnd.hf1/1666517910-1.apk) 

### Verifying the release
In order to verify the release, you'll need `gpg` or `gpg2` installed on your system. Breez puts hashes of the release files in a `SHA256SUM` file. The `SHA256SUM` file is then signed with the Breez GPG key. In order to verify the signatures, complete the following steps:

* Download the APK, ```SHA256SUMS``` and ```SHA256SUMS.asc``` from the release assets. 

* Download Breez's GPG key:
```
curl -O https://breez.technology/breez.technology.gpg
```

* Verify that the fingerprint is `02B5 268A 5D94 F50C D8B2  1734 C9B2 A8A6 46E9 4858`
```
gpg --show-keys --fingerprint < breez.technology.gpg
```

* Check the signature of the SHA256SUM file:
```
gpgv --keyring ./breez.technology.gpg SHA256SUMS.asc SHA256SUMS
```

This should give the following output:
```
gpgv: Signature made di 22 nov 16:13:07 2022 CET
gpgv:                using EDDSA key C4193B7F45B972375DFFDBACF5C584019396C59D
gpgv: Good signature from "Breez Technology <contact@breez.technology>"
```
* Finally, check the apk file hash:
```
sha256sum -c SHA256SUMS
```

This should give the following output:
```
xyz.apk: OK
```
