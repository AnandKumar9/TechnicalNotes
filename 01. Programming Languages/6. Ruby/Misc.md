##### Ruby 3 and openssl

~2024 Mar

Ruby 3.* versions do not support OpenSSL 3 (the [OpenSSL/TLS](https://formulae.brew.sh/formula/openssl@3) lib that seems to be available by default with Homebrew) and trying to install any gems that need OpenSSL give errors like these.

```swift
The Ruby openssl extension was not compiled.
ERROR: Ruby install aborted due to missing extensions
Configure options used:
  --prefix=/Users/ricky/.rbenv/versions/3.0.4
  --enable-shared
  --with-readline-dir=/opt/homebrew/opt/readline
  --with-libyaml-dir=/opt/homebrew/opt/libyaml
  --with-openssl-dir=/usr/local/opt/openssl@1.1
  CC=clang
  LDFLAGS=-L/Users/ricky/.rbenv/versions/3.0.4/lib 
  CPPFLAGS=-I/Users/ricky/.rbenv/versions/3.0.4/include
```

So for that OpenSSL 1.1 needs to be used as Ruby 3 does support it. 

`````
brew install openssl@1.1

export LDFLAGS=-L/opt/homebrew/opt/openssl@1.1/lib
export CPPFLAGS=-I/opt/homebrew/opt/openssl@1.1/include
brew --prefix openssl@1.1

brew link --overwrite openssl@1.1
`````

And then something like 'rbenv install' can be done.

```swift
RUBY_CONFIGURE_OPTS="--with-openssl-dir=/opt/homebrew/opt/openssl@1.1" rbenv install 
```

