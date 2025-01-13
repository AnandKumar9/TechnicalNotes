[toc]

#### Documentation

Swift Concurrency documentation - swift.org ([link](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/concurrency/)) <br>Swift Concurrency - API reference ([link](https://developer.apple.com/documentation/swift/concurrency/))

#### WWDC videos

[(Google Sheets list)](https://docs.google.com/spreadsheets/d/1b5_i0HhzGC7TM0O_Yzb4Vb5qwlwgrtTf1HsrycFThGE/edit#gid=409775223)

##### async await (aka Swift Concurrency)

2023: Beyond the basics of structured concurrency <br>2022: Visualize and optimize Swift concurrency <br>2022: Eliminate data races using Swift Concurrency - k <br>

2021: Meet async/await in Swift - k <br>
2021: Explore structured concurrency in Swift - k <br>
2021: Protect mutable state with Swift actors - k <br>
2021: Swift concurrency: Behind the scenes - k <br>
2021: Swift concurrency: Update a sample app <br>
2021: Meet AsyncSequence - k <br>

| Video                                                  | Summary                                                      |
| ------------------------------------------------------ | ------------------------------------------------------------ |
| 2021: Meet async/await in Swift - k                    | - Introduces `async` functions and how they can be called using `await` <br>- Briefly mentions `for-await-in` loops (i.e. AsyncSequence) <br>- Briefly mentions structured concurrency, i.e. using `Task` to call async code from sync contexts <br>- Introduces `CheckedContinuation` (i.e. how to implement async functions) <br>- 'Does not' introduce concurrent binding, i.e. `async let` |
| 2021: Explore structured concurrency in Swift - k      | - Says what is structured programming and structured concurrency <br>- Introduces concurrent binding, i.e. `asynchronous let` <br>- Explains Tasks, Task Trees <br>- How to check task cancellation status <br>- TaskGroup created with `withTaskGroup`, `withThrowingTaskGroup` <br>- `@Sendable` closure, using `for-await-in` to gather group's tasks' results. <br>- Explains how plain `Task{}` is an Unstructured Task <br>- Explains Detached Task and when to use it <br>- Summary table of all kinds of Tasks |
| 2021: Protect mutable state with Swift actors - k      | - Gives some trivial examples on how data races can happen <br>- Introduces `actor` types, and how their mutating interface should be accessed asynchronously from outside <br>- Explains what is actor reentrancy and how to avoid it <br>- Explains what is actor isolation, and how to use `nonisolated` keyword for protocol conformance by actors when necessary <br>- Explains Sendable types, i.e. `Sendable` protocol as well as `@Sendable` closure <br>- Introduces and explains `@MainActor` |
| 2021: Meet AsyncSequence - k                           | - Introduces AsyncSequence and consumption with for-await-in, for-try-await-in <br>- Shows how they can be put in tasks when taking long time, or be cancelled <br>- Shows the several Sequence like API, `first`, `contains(where:)`, `map()`, etc. <br>- Shows how to create your own AsyncSequence by using AsyncStream, AsyncThrowingStream |
| 2022: Eliminate data races using Swift Concurrency - k | - Introduces `@unchecked Sendable` conformance <br>- Explains `nonisolated` functions in more details <br>- Explains `@MainActor` in more details <br>- Introduces 'Swift Concurrency Checking' Build settings for Sendable types |

##### GCD

2017: Modernizing Grand Central Dispatch usage <br>
2016: Concurrent Programming With GCD in Swift 3 - k <br>
2015: Building responsive and efficient apps with GCD - k <br>
2014: Power, performance and diagnostics: What's New in GCD and XPC <br>

##### OperationQueues

2015: Advanced NSOperations <br>

#### Plan for when I resume

##### 2025 03 25 

Gotten myself up to date with a lot of Swift Concurrency basics. This should do for now. **The main thing to do now is to properly internalize and retain what I have learnt.**

When I do feel like resuming and understanding more, this should be the most relevant order -

Swift Concurrency documentation - swift.org ([link](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/concurrency/)) (Read, yet to do this) <br>2023: Beyond the basics of structured concurrency (Looks most relevant) <br>2021: Swift concurrency: Update a sample app (Skim) <br>2021: Swift concurrency: Behind the scenes - k (Revise) <br>2022: Visualize and optimize Swift concurrency <br>

