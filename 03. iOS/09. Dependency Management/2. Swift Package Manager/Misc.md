##### WWDC videos

[(Google Sheets list)](https://docs.google.com/spreadsheets/d/1b5_i0HhzGC7TM0O_Yzb4Vb5qwlwgrtTf1HsrycFThGE/edit#gid=409775223)

WWDC 2022: Meet Swift Package plugins <br>
WWDC 2022: Create Swift Package plugins <br>

WWDC 2021: Discover and curate Swift Packages using Collections <br>
WWDC 2020: Swift packages: Resources and localization <br>
WWDC 2019: Adopting Swift Packages in Xcode <br>
WWDC 2019: Creating Swift Packages <br>
WWDC 2018: Getting to Know Swift Package Manager <br>
WWDC 2019: What's New in Xcode 11 (12:40 onwards) <br>

WWDC 2020: Distribute binary frameworks as Swift packages <br>

Apple documentation - [Swift packages](https://developer.apple.com/documentation/xcode/swift-packages) <br>
Apple documentation - [Creating a Standalone Swift Package](https://developer.apple.com/documentation/xcode/creating-a-standalone-swift-package-with-xcode) <br>
Apple reference - [PackageDescription module](https://developer.apple.com/documentation/packagedescription) <br>

Libraries vs Frameworks - [Kseniia Zozulia](https://medium.com/@zippicoder/libraries-frameworks-swift-packages-whats-the-difference-764f371444cd) <br>

##### llbuild, libsytnax, libSwiftPM

SwiftPM uses `llbuild` for building (for whatever that may mean).

`libSyntax` is something more interesting ([link](https://github.com/apple/swift/blob/main/lib/Syntax/README.md)). It appears to be an Apple library which makes it easier to edit Swift code itself in an automated fasion (without getting into complicated regex work). If there is a need to modify package manifest files through CICD, it can be the recommended way to do it. (One more reason to use declrative syntax in manifest file, i.e. let the package simply be declared using `let/var package = Package(....)`.)

> The `WWDC 2018: Getting to Know Swift Package Manager` video at 25:36 mark gives lots of insights on how SPM could evolve (or possibly now already has).

`libSwiftPM` appears to be a library exposed by SwiftPM package itself, which is ueful to develope more tools and utilities that itself have to be built on top of SwiftPM.

##### Misc. errors

Sometimes there is an error while trying to the build the package and it says  "xcrun: error: unable to find utility "xctest", not a developer tool or in PATH". If this happens, it just needs to be ensured that there is something in in Xcode > Locations > Command Line Tools.

-----

Study EASE packages

SPM source code

Check the commands list

What is the right term? Libraries or Swift package? Are they the identical things?

A company may prefer to distribute binaries instead of source files to protect intellectual property (i.e. distribute xcFramework). So a consumer app has adds a binary package (i.e. xcFramework made available as a Swift Package). ([Distributing Binary Frameworks from Swift Packages](https://developer.apple.com/documentation/xcode/distributing-binary-frameworks-as-swift-packages) (Make binaries available to other developers by creating Swift packages that include one or more XCFrameworks) )

To find out whether a package dependency is a binary dependency or if a source-based package depends (https://developer.apple.com/documentation/xcode/identifying-binary-dependencies)



