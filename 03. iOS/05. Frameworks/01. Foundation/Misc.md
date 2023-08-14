[Reference](https://developer.apple.com/documentation/foundation)

###### Predicates

Strings not beginning with a certain substring.
```
NSPredicate *predicate = [NSPredicate predicateWithFormat:@"NOT (SELF BEGINSWITH[cd] %@)", @"InitialSubstring"];
```
