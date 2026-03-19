##### Checking how much space various packages are taking

```
brew list --formula | while read f; do du -sh "$(brew --cellar)/$f"; done | sort -hr
```

Prints this ....

```
1.7G	/opt/homebrew/Cellar/llvm
382M	/opt/homebrew/Cellar/boost
157M	/opt/homebrew/Cellar/deno
124M	/opt/homebrew/Cellar/ruby
105M	/opt/homebrew/Cellar/node
.....
```

