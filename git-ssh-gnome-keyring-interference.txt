# ssh authentication problem for git (gnome keyring interference)

### Fixing gnome-keyring interference :

```sh
# "Startup Applications" -> "SSH Key Agent" (Gnome Keyring) : unckeck it !
ps -aux | grep agent
pkill -HUP gpg-agent
ssh -T git@gitbucket.org -i $HOME/.ssh/${USER}_rsa
```

