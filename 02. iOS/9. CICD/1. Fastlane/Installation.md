First install RVM - The second step is important and the path to `source` is actually shown as a part of the previous curl command's console output
```
curl -L https://get.rvm.io | bash -s stable
source /Users/Anand/.rvm/scripts/rvm
```

Then install Ruby -
`rvm install ruby-2.4.1`

Install Fastlane -
`gem install fastlane --verbose`

>Now in my office network I first had to run a script which configures the proxy for terminal (apparently the system preferences' proxy does not automatically come into effect for network calls made using terminal) or else the RVM download was getting blocked. <br>
RVM is essentially needed to get a newer version of Ruby.

Fastlane requires Ruby 2.1 or later.

code command line tools should also be already installed. A simple way to install them (or to check if they are installed or not) is running this command.
`xcode-select --install`


Its also possible to install Fastlane using Homebrew cask (did not use this though) -
`brew cask install fastlane`
