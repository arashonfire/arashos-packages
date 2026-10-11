# ArashOS packages

The pacman repository of [ArashOS](https://github.com/arashonfire), an Arch-based distribution with a Hyprland desktop. The packages are the release assets of [the `x86_64` release](https://github.com/arashonfire/arashos-packages/releases/tag/x86_64); ArashOS installs use them, and so can any Arch system:

```ini
[arashos]
Server = https://github.com/arashonfire/arashos-packages/releases/download/$arch
```

Every package and the database are signed with the ArashOS release key:

```
443060AB26BEE9F9FAB94C19ED4DC6181E2F40E7  ArashOS Release Key
```

Its public key is [`arashos-release.asc`](arashos-release.asc). ArashOS systems get it from the `arashos-keyring` package on the install medium; elsewhere, add it with `pacman-key --add arashos-release.asc` and `pacman-key --lsign-key 443060AB26BEE9F9FAB94C19ED4DC6181E2F40E7`.

## Sources

- `arashos-*`: ArashOS's own packages (GPL-3.0).
- Everything else is built unchanged from the AUR recipe at the commit pinned in [`aur.lock`](aur.lock) (`https://aur.archlinux.org/<package>.git`), which downloads the upstream source named in that recipe, except for the changes in [`patches/`](patches): `patches/<package>/*.patch`, applied with `patch -p1` to the top of the package's source, with `.N` added to its `pkgrel` (`patches/<package>/pkgrel`, default 1), raised whenever the patches change.

Licences are those of each project; `pacman -Qi <package>` shows them.

This repository's files are copied from ArashOS by `packages/publish.sh` each time the packages are published; changes made here are overwritten.
