[toc]

##### Installing Cocoapods on Apple M1 Macs

The usual way to install Cocoapods is to just install the gem ([link](https://guides.cocoapods.org/using/getting-started.html)).

```
sudo gem install cocoapods
```

But this gives an error on M1 chip Macs (as of early 2022). The workaround is to first check 'Open using Rosetta' for `Terminal.app`, and then doing a `sudo gem install ffi` before doing a `sudo gem install cocoapods`. ([link](https://medium.com/codex/simple-way-to-use-cocoapods-on-m1-ac9e22cf7e1c))

![](../../../../Technical Notes/03. iOS/09. Dependency Management/1. Cocoapods/assets/Misc-f834d0cf.png)

> `Ruby-FFI` is a gem for programmatically loading dynamically-linked native libraries, binding functions within them, and calling those functions from Ruby code. Its an abbreviation for 'Foreign Function Interface'. ([Why use ffi](https://github.com/ffi/ffi/wiki/why-use-ffi) to write Ruby extensions.)

> `Rosetta` is a dynamic binary translator developed by Apple Inc. for macOS, an application compatibility layer between different instruction set architectures. It gives developers and consumers a transition period in which to update their application software to run on newer hardware, by "translating" it to run on the different architecture. ([link](https://en.wikipedia.org/wiki/Rosetta_(software)))

##### Adding git passphrase in ssh config file

If you get prompted for your passphrase repeatedly while doing a pod install, do [this](https://apple.stackexchange.com/questions/18458/password-dialog-appears-when-ssh-private-key-permissions-are-set-to-0600/264963#264963). <br>
Create the file `~/.ssh/config` with contents:

```
Host *
   AddKeysToAgent yes
   UseKeychain yes
   IdentityFile ~/.ssh/id_rsa
```

##### xcproj tool

`xcproj` is a command line tool for managing the Xcode project file.

##### Semantic versioning

Semantic versioning [link](https://semver.org/)
