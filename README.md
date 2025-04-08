Provided configuration is needed for signing git commits inside neovim.

Before using, install pinentry-tty

```bash
sudo apt install pinentry-tty
```

Reload agent


```bash
gpg-connect-agent reloadagent /bye
```

---

To add my keys run

```bash
gpg --import private.key
gpg --import public.key
gpg --edit-key YOUR_KEY_ID
> trust
> 5
> save
gpg --list-secret-keys --keyid-format=long
```

If for some reason you want to use default pinentry-curses, to make it work under tmux add `export GPG_TTY=$(tty)` to `~/.bashrc`
