Benefits - Remote caching, faster builds, predictable

##### Videos

Two large team iOS Bazel migrations (Erik Kerber) - https://www.youtube.com/watch?v=wy3Q38VJ5uQ <br>iOS dev with Bazel (Peter Iakovlev) - https://www.youtube.com/watch?v=O3A9KmFUwMc <br>What's Bazel? Why should you care (Siemens) - https://www.youtube.com/watch?v=sW8b-cgqicc

##### Language

Starlark language ([overview](https://github.com/bazelbuild/starlark/?tab=readme-ov-file), [specs](https://github.com/bazelbuild/starlark/blob/master/spec.md)) - Designed to be a configuration language for Bazel. A subset of Python, dynamically typed, has garbage collerction. Used in both BUILD files, and WORKSPACE files. Gurantees thread safe execution.

##### Common rules

Bazel glossary - https://bazel.build/reference/glossary<br>Bazel iOS - https://bazel-ios.github.io<br>

Getting started - https://bazel.build/start <br>Basic iOS tutorial - https://github.com/bazelbuild/rules_apple/blob/master/doc/tutorials/ios-app.md <br>Build concepts - https://bazel.build/concepts/build-ref <br>

User guides - https://bazel.build/docs <br>Migrating from Xcode to Bazel - https://bazel.build/migrate/xcode <br>Full reference - https://bazel.build/reference <br>Extending Bazel - https://bazel.build/extending <br>

rules_apple ([link](https://github.com/bazelbuild/rules_apple)) - Handles linking and building of apps and extensions (i.e. forms .app, .ipa) <br>objc_library ([link](https://bazel.build/reference/be/objective-c#objc_library)) - Produces a static lib from ObjC files <br>rules_swift ([link](https://github.com/bazelbuild/rules_swift)) - Rules to buld libs and executables for macOS and Linux from Swift files <br>swift_library ([link](https://github.com/bazelbuild/rules_swift/blob/master/doc/rules.md#swift_library)) - Produces a static lib/swiftmodule from Swift code <br>rules_ios ([link](https://github.com/bazel-ios/rules_ios)) - Rules for iOS apps (accounts for both Swift and ObjC code) <br>

