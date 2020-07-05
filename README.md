Steps to replace Windows with Linux.

# Check the target system
- old Windows 7 laptop
- 64-bit Windows
- 4GB RAM
- Intel i5-2520M CPU @ 2.50GHz

## Linux Mint requirements
- 4GB RAM is OK: Mint requires 1GB RAM, 2GB for comfortable use
- was 64-bit Windows, so download a 64-bit Linux

# Create Linux Mint boot disk

## Download ISO
- download the `.iso` image of the 64-bit cinnamon distribution:
    - linuxmint-19.3-cinnamon-64bit.iso

## Verify ISO
The following are my notes while following the guide here: <https://linuxmint.com/verify.php>

- download the checksum .txt and .txt.gpg files:
    - sha256sum.txt
    - sha256sum.txt.gpg

- calculate the `sha256` checksum of the `.iso` in `bash`:

```bash
$ sha256sum.exe linuxmint-19.3-cinnamon-64bit.iso
7a9e54212433c8547edfd789ac933c91a9bde1a61196fa7977c5357a2c40
```

- confirm this matches the checksum in the downloaded file
- check the signature on the downloaded file by validating the gpg key
- download the key:

```bash
$ gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-key "27DE B156 44C6 B3CF 3BD7  D291 300F 846B A25B AE09"

gpg: requesting key A25BAE09 from hkp server keyserver.ubuntu.com
gpg: key A25BAE09: public key "Linux Mint ISO Signing Key <root@linuxmint.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
```

- verify:

```bash
$ gpg --verify sha256sum.txt.gpg sha256sum.txt
gpg: Signature made Mon, Dec 16, 2019 10:10:16 AM EST using RSA key ID A25BAE09
gpg: Good signature from "Linux Mint ISO Signing Key <root@linuxmint.com>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 27DE B156 44C6 B3CF 3BD7  D291 300F 846B A25B AE09
```

According to the guide, this is correct:

> The output of the last command should tell you that the file signature is
> 'good' and that it was signed with the following key: 27DE B156 44C6 B3CF 3BD7
> D291 300F 846B A25B AE09 (with or without spaces).

> Note: Unless you trusted this signature in the past, or a signature which
> trusted it, GPG should warn you that the signature is not trusted. This is
> expected and perfectly normal.

## Burn ISO onto USB stick
Follow this guide:

<https://linuxmint-installation-guide.readthedocs.io/en/latest/burn.html>

- TLDR: download burner: <https://www.balena.io/etcher/>
- another burner option is `Win32 Disk Imager`
