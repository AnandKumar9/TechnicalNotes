##### zsh basics

Equivalent of .bash_profile - `.zprofile` ([link](https://stackoverflow.com/a/23091184/1135417)).

Another common file is `.zshrc`, in fact this is where aliases are usually put.

All these files are usually located in `/private/etc`.

There are five separate profile scripts that get executed (in the order given below) when we launch a zsh shell or close it out.

(1) `.zshenv` --> This is always sourced first but can be overridden by other

(2) `.zprofile` --> This is equivalent for users coming from ksh experience

(3) `.zshrc` --> This is for all of the interactive customizations of zsh

(4) `.zlogin` --> This executes after first three are done

(5) `.zlogout` --> This is executed when we logout of the zsh shell it would be advisable to put your stuff in .zshenv or in .zshrc

##### aliases

For adding an alias, just put it in an appriopriate file (typically `zshrc`).
```
alias thinkandpush="git add *;git commit --amend --no-edit;git push origin master --force"
```
If the list of aliases becomes too long, the cleaner thing to do is to put them in a separate file of their own (say `/.zsh_aliases`) and then just have `. ~/.zsh_aliases` or `source ~/.zsh_aliases` in `zshrc` file.

Escaping certain characters in `zsh` scripts is slightly different than escaping in `bash` scripts. Its not just `"` and `\` that need to be escaped, but even `$` has to be escaped. ([Link](https://superuser.com/a/874764/150401))
