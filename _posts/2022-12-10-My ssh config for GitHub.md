---
title: My ssh config for two GitHub accounts
category: ssh
tags: [ssh, github]
---
This is the ssh config file settings and the commands to add ssh passphrase to Apple Keychain. 
Also there's commands to test the settings out.

### Add and change ssh passphrase to Apple Keychain Access
``` console
$ ssh-add --apple-use-keychain ~/.ssh/_ed255-gitlab
$ ssh-keygen -p -f ~/.ssh/_ed255-gitlab
```

### My ssh config
```zsh
# G2K account
Host github.com-g2k
   HostName github.com
   User git
   IdentityFile ~/.ssh/
   AddKeysToAgent yes
   UseKeychain yes

# personal account
Host github.com-yong
   HostName github.com
   User git
   IdentityFile ~/.ssh/
   AddKeysToAgent yes
   UseKeychain yes

# GitLab
Host gitlab
   HostName gitlab.com
   User git
   IdentityFile ~/.ssh/
   AddKeysToAgent yes
   UseKeychain yes
```


**Teshing the ssh connections to GitHub**

Type this command to test:
``` console
$ ssh -T git@github.com-yong
```
Then look out for this output:
``` console
> Hi USERNAME! You've successfully authenticated, but GitHub does not
> provide shell access.
```
