###### Regex flavors

There are several different flavors (i.e. engines) of regular expressions. Typically every language that supports regular expressions have their own flavors, though most of them are modeled on Perl's.

Swift's based on something called ICU.

Though all these flavors are mostly same, there can be a few differences. For example,
JavaScript doesn't support look behinds.
PHP and some others support look behinds, but needs them to be fixed length
Regex engines of text editors (Notepad++) generally don't support look around.

https://en.wikipedia.org/wiki/Comparison_of_regular_expression_engines

PCRE stands for PERL Compatible Regular Expressions. It's a regex engine written in C and inspired by Perl's capabilities.

###### Lines containing two substrings in any order

`^(?=.*\bstr1\b)(?=.*\bstr2\b).*$` <br>
This is a robust version and can be easily extended for more substrings. So ^ denotes beginning of string. (?=.*\bstr1\b) after that means str1 should occur as a word somewhere afterwards. (?=.*\bstr2\b) means str2 should occur as a word somewhere afterwards. Both of them I think are lookaheads for beginning of string, i.e. ^. So lookbehinds can be combined.


str1.*str2|str2.*str1
A very simplistic version that will only work for two substrings.

###### Verifying that a substring occurs only once

`^(?:(?!str).)*str(?!.*str).*$`

(Don't get the explanation. How is ?! above a lookbehind negative and not a lookahead negative instead.)

[link](https://stackoverflow.com/a/30145010/1135417)

###### Matching files changed in a PR using `grep`

[(Regex101 link)](https://regex101.com/r/TsMebp/1)

```
grep -E "\d+ +(\w|\.).*(swift|pdf|pbxproj|xib|json)" Scratchpad.txt | cat -b
```
Matches these -
```
417  Sandbox/Features/RecurringTransactions/Screens/RecurringTransactionDetailsViewController.xib

167  ...ox/Features/RecurringTransactions/Screens/RecurringTransactionDetailsViewController.swift

6  Sandbox/Sandbox/Assets.xcassets/DigitalCardPostLSRP/Contents.json
```

###### Misc. -

Online tester - [Regex101](https://regex101.com/) <br>
Cheat sheet - [Rexegg](http://www.rexegg.com/regex-quickstart.html) <br>
FAQs - [StackOverflow](https://stackoverflow.com/questions/22937618/reference-what-does-this-regex-mean/22944075#22944075) <br>
Exercises - [Regex Crossword](https://regexcrossword.com/)

> Understand `\G` (beginning of string or end of previous match) better
