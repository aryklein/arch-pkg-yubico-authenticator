# arch-pkg-yubico-authenticator
Yubico Authenticator package for Arch Linux

## How to install
Import the necessary GnuPG key:

```bash
gpg --recv-keys 20EE325B86A81BCBD3E56798F04367096FBA95E8
```

Build the package using the Arch Linux `makepkg` tool:

```bash
makepkg -s
```

Install the built package with `pacman`:

```bash
sudo pacman -U yubico-authenticator-<pkgver>-x86_64.pkg.tar.zst
```
