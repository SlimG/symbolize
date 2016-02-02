# symbolize
Use this with ex. [Dropbox](https://www.dropbox.com) to keep your configuration files synced between your workstations using symbolic links

I was inspired by [Ira](https://github.com/lra)'s (https://github.com/lra/mackup), but I needed to have some configuration files shared between all my computers (ex. ~/.vimrc), and some available in Dropbox under their own hostname folders for backup-purpose (ex. ~/.ssh).

## Installation
Put the symbolize script in your $PATH

## Usage
```bash
symbolize SOURCE DESTINATIONFOLDER
```

### Example: SOURCE exists, but DESTINATIONFOLDER does not.
```bash
symbolize ~/.ssh ~/Dropbox/config/$HOSTNAME
The destination directory "/home/slimg/Dropbox/config/maggie" does not yet exist.
Do you want to have this folder created for you? (y|n) :
y
The source "/home/slimg/Dropbox/config/.ssh" does exist. The destination "/home/slimg/Dropbox/config/maggie/.ssh" does not exist.
Do you want to move "/home/slimg/Dropbox/config/.ssh" to "/home/slimg/Dropbox/config/maggie/.ssh", and then create "/home/slimg/Dropbox/config/.ssh" as symbolic link towards "/home/slimg/Dropbox/config/maggie/.ssh" ? (y|n) :
y
"/home/slimg/Dropbox/config/.ssh" has been moved to "/home/slimg/Dropbox/config/maggie/.ssh".
Symbolic link "/home/slimg/Dropbox/config/.ssh" pointing toward "/home/slimg/Dropbox/config/maggie/.ssh" has been created.
```

### Example: DESTINATIONFOLDER has existing config, but SOURCE does not.
```bash
symbolize ~/.vimrc ~/Dropbox/config/shared
The source "/home/slimg/Project/testing/.vimrc" does not exist. The destination "/home/slimg/Dropbox/config/shared/.vimrc" does exist.
Do you want to create "/home/slimg/Project/testing/.vimrc" as a symbolic link towards "/home/slimg/Dropbox/config/shared/.vimrc" ? (y|n) :
y
Symbolic link "/home/slimg/Project/testing/.vimrc" pointing toward "/home/slimg/Dropbox/config/shared/.vimrc" has been created.
```

### Example: Both exist.
```bash
symbolize ~/.irssi ~/Dropbox/config/shared
Both "/home/slimg/.irssi" and "/home/slimg/Dropbox/config/shared/.irssi" exist.

Options:
  d: Replace "/home/slimg/.irssi" with a symoblic link toward "/home/slimg/Dropbox/config/shared/.irssi".
    s: Overwrite "/home/slimg/Dropbox/config/shared/.irssi" using "/home/slimg/.irssi", then create "/home/slimg/.irssi" as a symbolic link towards "/home/slimg/Dropbox/config/shared/.irssi".
      n: Don't do anything.
      What do you want to do? (d|s|n) :
      s
      "/home/slimg/Dropbox/config/shared/.irssi" has been deleted.
      "/home/slimg/.irssi" has been moved to "/home/slimg/Dropbox/config/shared/.irssi".
      Symbolic link "/home/slimg/.irssi" pointing toward "/home/slimg/Dropbox/config/shared/.irssi" has been created.
```
