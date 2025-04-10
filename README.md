Provided configuration is needed for signing git commits inside neovim.

Before using, install pinentry-tty:

```bash
sudo apt install pinentry-tty
```

Reload agent:


```bash
gpg-connect-agent reloadagent /bye
```

---

Add my keys:

```bash
gpg --import private.key
gpg --import public.key
gpg --edit-key F3F6E72B21D354FC
> trust
> 5
> save
gpg --list-secret-keys --keyid-format=long
```

Setup gpg permissions:

```bash
chown -R $(whoami) ~/.gnupg/
find ~/.gnupg -type f -exec chmod 600 {} \;
find ~/.gnupg -type d -exec chmod 700 {} \;
```

To make git auto-sign commits:

```bash
git config --global user.signingkey F3F6E72B21D354FC
git config --global commit.gpgsign true
git config --global tag.gpgSign true
```

If for some reason you want to use default pinentry-curses, to make it work under tmux add `export GPG_TTY=$(tty)` to `~/.bashrc`:

```bash
[ -f ~/.bashrc ] && echo -e '\nexport GPG_TTY=$(tty)' >> ~/.bashrc
```
