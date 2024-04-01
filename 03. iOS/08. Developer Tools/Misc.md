[toc]

LLVM at high level - https://www.infoworld.com/article/3247799/development-tools/what-is-llvm-the-power-behind-swift-rust-clang-and-more.html

###### Running Swift from command line

Swift code can be put in a file and the file run from command line.

1. Add a shebang at top.
```
#!/usr/bin/swift
```
2. Make the script executable.
```
chmod +x FileName.swift
```
3. Execute the Swift file.
```
./FileName.swift
```

Any command line arguments that get passed can be accessed in Swift this way.
```
 let arg = CommandLine.arguments[1]  // First argument.
```

And yes, Swift can be run interactively too. Just type `swift` in command line and then the terminal interface becomes `REPL`.

[link](https://jblevins.org/log/swift)

###### Compiling a Swift file from command line

```
swiftc -o CompiledExecutable FileName.swift   // This generates the executable
./CompiledExecutable   // And then run the executable

swiftc first.swift second.swift third.swift -o program  // Compile multiple Swift file, yet to try
```

###### xed

Just a command line tool (that comes pre-installed with Xcode/macOS) and can be used to open projects/files in Xcode with the right Xcode version (even if multiple versions are installed).

```shell
xed . -> Opens the project in current directory

xed -xc test.swift -> Creates a new file and opens it, does not link it to project though

xed Test.swift -> Opens the file

xed help -> See all options
```

[Article](https://dive.medium.com/xcode-invocation-tool-xed-deb04d03cf98)
