###### Journal

If a command line argument is passed that does not match any property in the `ParsableCommand` struct, there seems to be an error.

```
Error: Unknown option '--xyzabc'
```

###### Experimental Features

There are some experimental features available too as a flag, they usually have the prefix ``--experimental`. For example,as of early 2023 if a command is run with `--experimental-dump-help` flag, it dumps the help information in JSON format. ([Reference](https://apple.github.io/swift-argument-parser/documentation/argumentparser/experimentalfeatures))

###### AsyncParsableCommand

`AsyncParsableCommand` I think is the type that needs to be used (instead of `ParsableCommand`) if the coammands `run()` has any async/await code.

```
import Foundation

@main
struct CountLines: AsyncParsableCommand {
    @Argument(transform: URL.init(fileURLWithPath:))
    var inputFile: URL

    mutating func run() async throws {
        let fileHandle = try FileHandle(forReadingFrom: inputFile)
        let lineCount = try await fileHandle.bytes.lines.reduce(into: 0) 
            { count, _ in count += 1 }
        print(lineCount)
    }
}
```

In Swift 5.5, you need to declare a separate, standalone type as your asynchronous `@main` entry point. Instead of designating your root command as `@main`, as described above, use the code snippet below, replacing the placeholder with the name of your own root command. Otherwise, follow the steps above to use `async`/`await` code within your commands’ `run()` methods.

```
@main struct AsyncMain: AsyncMainProtocol {
    typealias Command = <#RootCommand#>
}
```

([Reference](https://apple.github.io/swift-argument-parser/documentation/argumentparser/asyncparsablecommand/))

###### Parsing indefinite number of arguments

Its just a matter of declaring the `@Argument` property as an array.

```
@Argument var inputs: [String]
```

