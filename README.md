# PKGBUILDS
PKGBUILDS for some Arch Linux packages I maintain, collected here for ease of management.

I maintain an unofficial user repository which provides prebuilt versions of these packages 
and their dependencies from the AUR. To use that add my signing key to the pacman keyring
```bash
pacman-key --recv-keys E029EB9088C833C2
pacman-key --lsign-key E029EB9088C833C2
```
and add the my repo at the end of `/etc/pacman.conf`
```
[kotontrion]
Server = https://arch-pkgs.kotontrion.net/$arch/
```
