##### tree command

A custom commmand used to get a tree like listing of a folder's contents. It can be installed via Homebrew as well as MacPorts ([link](https://superuser.com/a/359727)).

```
brew install tree
port install tree
```

`-d` - Lists directories only <br>
`-L` - Specifies nesting depth of the tree to be listed <br>
`-P` - Lists only the files that match the wild-card pattern <br>
`-I` - Does not list the files that match the wild-card pattern <br>
`-h` - List the file size as well <br>

For specifying multiple patterns, club them in `()`.
```
tree -I '*png|*md'
```
