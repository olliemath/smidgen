### Smidgen: a mirror ranking tool for Arch Linux

When run, smidgen uses a config file `~/.smidgenrc` to
rank mirrors from the user's preferred countries, uncomment the fastest ones and write a new `mirrorlist`. It obfuscates the need for manual editing when pacman saves a new mirrorlist to `mirrorlist.pacnew`.

### Features disguised as 'FAQ's\*:
Q: Can I use a custom mirror not in the standard files, e.g. `http://delta.archlinux.fr/$repo/os/$arch`?

A: Yes. In the above example your would place the line `Server = http://delta.archlinux.fr/$repo/os/$arch` in your smidgenrc and, so long as the server responds when smidgen runs, it will appear at the top of any new mirrorlist.

Q: Does smidgen only use https?

A: By default, yes. To allow http, uncomment the `ALLOW_HTTP` option in smidgenrc, or add your favorite http server directly to your smidgenrc file, as above.

Q: Smidgen destroyed my favorite mirrorlist. Arggh!

A: Smidgen keeps a backup of the last mirrorlist file at `/etc/pacman.d/mirrorlist.bkup`. If you want to file a bug report, please include your smidgenrc and the bad mirrorfile smidgen created.

### Example
Typical use case:
```
[foo@bar]$ sudo pacman -Syu
# Lots of updatey type stuff happens here
warning: /etc/pacman.d/mirrorlist installed as /etc/pacman.d/mirrorlist.pacnew
[foo@bar]$ smidgen
Got list of mirrors. Attempting to rank them - this may take some time.
Cleaning up, backing up and writing files.
[foo@bar]$
```

Typical config file:
```rc
# Config at ~/.smidgenrc

# Countries near me:
UnitedKingdom
France

# My own favorite servers to use above all others:
Server = http://my_fave_server/as/it/would_appear/in/mirrorlist

# ALLOW_HTTP
```

<sub> \* Nobody has ever asked any of these questions </sub>
