# symbolize
Use this with ex. [Dropbox](https://www.dropbox.com) to keep your configuration files synced between your workstations using symbolic links

I was inspired by [Ira](https://github.com/lra)'s [mackup](https://github.com/lra/mackup), but I needed to have some configuration files shared between all my computers (ex. ~/.vimrc), and some available in Dropbox under their own hostname folders for backup-purpose (ex. ~/.ssh).

## Installation
Put the symbolize script in your $PATH, or run the following if you have [Snap](https://snapcraft.io/):

```
snap install symbolize
```

## Usage
```
symbolize SOURCE DESTINATIONFOLDER
```

### Example: SOURCE exists, but DESTINATIONFOLDER does not.
```
symbolize ~/.ssh ~/Dropbox/config/$HOSTNAME
WARNING: The following folder does not yet exist:
  /home/slimg/Dropbox/config/maggie

Do you want to create it? (y|n) :
y

Running: mkdir -p "/home/slimg/Dropbox/config/maggie"
Running: mv "/home/slimg/.ssh" "/home/slimg/Dropbox/config/maggie/.ssh"
Running: ln -s "/home/slimg/Dropbox/config/maggie/.ssh" "/home/slimg/.ssh"
```

### Example: DESTINATIONFOLDER has existing config, but SOURCE does not.
```
symbolize ~/.vimrc ~/Dropbox/config/shared
Running: ln -s "/home/slimg/Dropbox/config/shared/.vimrc" "/home/slimg/.vimrc"
```

### Example: Both exist.
```
symbolize ~/.irssi ~/Dropbox/config/shared
WARNING: Both exist.

Options:
  d: Sacrifice "/home/slimg/.irssi"
  s: Sacrifice "/home/slimg/Dropbox/config/shared/.irssi"
  n: Don't do anything.

What do you want to do? (d|s|n) :
s

Running: rm -R "/home/slimg/Dropbox/config/shared/.irssi"
Running: mv "/home/slimg/.irssi" "/home/slimg/Dropbox/config/shared/.irssi"
Running: ln -s "/home/slimg/Dropbox/config/shared/.irssi" "/home/slimg/.irssi"
```
