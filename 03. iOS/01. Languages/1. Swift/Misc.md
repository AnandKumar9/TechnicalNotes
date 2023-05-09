Swift is said to be a `type-safe` language. What it means is that it does not allow a variable of one type to be assigned a value of another type.

Not every type in Swift can be compared with equal to operator (`==`). However there is a protocol called `Equatable`, which requires its conforming types to implement the == and != operators.

When an array contains a collection of instances and is iterated over, the system automatically assumes the best possible type for each of the instances. If all them have a common superclass, then that is assumed as the type. Thus to access API of some subclass type that any of those elements might be, a downcasting must be done.

#### Result type

(This is available from Swift 5.0).

```
enum Result<Success, Failure> where Failure : Error {
  case success(Success)
  case failure(Failure)  
}
```

`init(catching: () -> Success)` - Creates a new Result by running the passes closure. Returned value is treated as success case, and any thrown error is treated as failure case.
```
let xyz = Result<String, PlaceholderError> {
    if Bool.random() {
        return "All nice"
    } else {
        throw PlaceholderError()
    }
}
```

`get()`- Returns the value in case of success, else throws an error.

`map()`, `mapError()`, `flaMap()`, `flatMapError()` - Maps (and flattens by one level of unwrap) the success, error.

#### Universal `Self`

(This was proposed in [SE-0068 Expanding Swift Self to class members and value types](https://github.com/apple/swift-evolution/blob/master/proposals/0068-universal-self.md) and introduced in Swift 5.1).

If a class property is referred to using `Self` qualifier, then it refers to that property's overriden value (i.e. when the override has happened in a subclass).

```
class NetworkManager {
    class var maximumActiveRequests: Int {
        return 3
    }

    func printDebugData() {
        print("Without using Self: \(NetworkManager.maximumActiveRequests).") // 3
        print("Using Self: \(Self.maximumActiveRequests).")  // 4
    }
}

class ImprovedNetworkManager: NetworkManager {
    override class var maximumActiveRequests: Int {
        return 4
    }
}

ImprovedNetworkManager().printDebugData()   // Prints 3 then 4
```

#### Boolean

`toggle()` is a mutating function for boolean.

#### Nested types

Its possible to define types within other types (nested types). And they can be accessed outside the context they are defined in, by using dot notation.

```
struct Struct1 {
    enum EnumA: Character {
        case ..
    }
    let property1: EnumA, ..
```

In fact until 3.0, it was not possible to create nested types in generic types. But 3.1 onwards it is, in fact even the nested type itself can make use of the generic placeholder.

```
class Class1<T> {
	let a: Int

	class Class2<T> {
```

#### Various protocols

`ErrorType` (has no requirement) <br>
`Equatable` ( == ) <br>
`Comparable` (inherits `Equatable` and has `<` requirement too) <br>
`Hashable` (`hashValue`, `hash(into:)`) <br>
`Sequence` (provides iteration requirements) <br>
`Collection` (inherits Sequence and has index and non-destructive requirements) <br>

#### Hashable

If a custom type needs to be made `Hashable` conformant, it needs to have implementations `hash(into: inout Hasher)`. It also needs `hashValue: Int` property implementation but that has now been deprecated. <br>
(This was proposed in [SE-026 Hashable Enhancements](https://github.com/apple/swift-evolution/blob/master/proposals/0206-hashable-enhancements.md) and implemented in Swift 4.2.)

`hash(into: inout Hasher)` is easier to implement than the previous `hashValue` property. The argument is an inout `Hasher` object. Inside the function `hasher.combine()` can be called for each of the type properties.

```
struct Point {
    var x: Int
    var y: Int
}
extension Point: Hashable {
    func hash(into hasher: inout Hasher) {
        hasher.combine(x)
        hasher.combine(y)
    }
}
```

> Understand `hash(into: inout Hasher)` better. Explained in Ole's 4.2 playground.

##### Failable initializers for numeric types

3.1 includes a bunch of failable initializers for numeric types.

`init?(exactly value: Int8)` <br>
`init?(exactly value: Float)`
...

For example, this will fail if `x` is 6.3 but succeed if `x` is 6.0
```
let a = Int(exactly: x)
```

#### Generating random values

It's pretty easy since Swift 4.2.

All number types now have a `random(in:)` method that takes in a range.
```
Int.random(in: 1...1000)
UInt8.random(in: .min ... .max)
Double.random(in: 0..<1)
```

There is more.
```
Bool.random()
collection1.random()!  // Returns optional, as it can be nil if collection is empty
```

`Collection` has a function called `randomElement()`.
Also, `Sequence` has functions called `shuffled()` (for non-mutable sequences) and `shuffle()` (for mutable sequences).

In fact there is even a protocol called `RandomNumberGenerator` which can now be conformed to if a type wishes to provide its own modified behavior of random(). It probably has a next() function. Also, the default system random generator is `SystemRandomNumberGenerator`.

> Need to try `RandomNumberGenerator`.

##### Accessing underlying contents through unsafe pointers

```
withUnsafeBufferPointer
withUnsafeMutableBufferPointer
withUnsafeBytes
withUnsafeMutableBytes
```

Tuples too can be compared (using <, > operators) if their values allow comparison to happen. Tuples are compared from left to right, one value at a time, until the comparison finds two values that aren’t equal. Int and String can be compared (i.e. < or >), but Bool cannot be.

##### callAsFunction

(This was proposed in [SE-0253 Callable values of user-defined nominal types
](https://github.com/apple/swift-evolution/blob/master/proposals/0253-callable.md) and introduced in Swift 5.2.)

If a type has a function called `callAsFunction`, then an instance of that type can be used as it was a function itself. The function can also take in arguments.

```
struct Dice {
    var lowerBound: Int
    var upperBound: Int

    func callAsFunction() -> Int {
        (lowerBound...upperBound).randomElement()!
    }
}

let d6 = Dice(lowerBound: 1, upperBound: 6)
let roll = d6()
````

##### Sundries

Getting a Date from unix format  timestamp - <br>
It is as simple as this. Unix timestamp are formats like 181481901.
```
Date.init(timeIntervalSince1970: unixTimestamp)
```

Restricting a property's value to a range -

```
public var imageQuality: CGFloat = 0.9 {
    didSet {
        if imageQuality > 1.0 { imageQuality = 1.0 }
        else if imageQuality < 0 { imageQuality = 0 }
    }
}
```

#### Integer and other data types

`Int` has a method called `isMultiple(of:)` to check if a number is a multiple of some smaller number.

--------



> Swift.org Protocols write-up, Protocols composition

> Swift 5.3

> The `New integer protocols` page in Ole Begemman's Swift 4 playground

> `dynamicMemberLookup`, `@inlinable`, `@usableFromInline` attributes in Swift 4.2. Ole's playground. `dynamicMemberLookup` is also in Paul Hudson's blog.

> MemoryLayout offset(of:) introduced in Swift 4.2
