If you get prompted for your passphrase repeatedly while doing a pod install, do [this](https://apple.stackexchange.com/questions/18458/password-dialog-appears-when-ssh-private-key-permissions-are-set-to-0600/264963#264963). <br>
Create the file `~/.ssh/config` with contents:
```
Host *
   AddKeysToAgent yes
   UseKeychain yes
   IdentityFile ~/.ssh/id_rsa
```

**********

`xcproj` is a command line tool for managing the Xcode project file.

Semantic versioning [link](https://semver.org/)

**********
