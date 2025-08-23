[Documentation](https://github.com/apple/swift-syntax#documentation) refers 3 main things - `SwiftSyntax`, `SwiftSyntaxParser`, `SwiftOperators`

The GH repo has a list of interesting [example](https://github.com/apple/swift-syntax/tree/main/Examples) projects that use swift-syntax.

[SourceKitten](https://github.com/jpsim/SourceKitten) is an open source framework from pre-Swift Syntax days to do what SwiftSyntax now does. It works with [SourceKit](https://github.com/apple/sourcekit-lsp) and Clang. SourceKit is the set of tools that enables most of Swift’s source code manipulation features: source code parsing, syntax highlighting, typesetting, autocomplete, cross-language header generation, and lots more. ([JP Simard article on SourceKit](https://www.jpsim.com/uncovering-sourcekit/))

[TrySwiftNYC 2017 talk](https://www.youtube.com/watch?v=5ivuYGxW_3M) (potentially obsolete now)

[Syntax Operators](https://github.com/apple/swift-syntax/blob/main/Sources/SwiftOperators/SwiftOperators.docc/SwiftOperators.md)

[Alejandro MP artcile](https://alejandromp.com/blog/implementing-using-in-swift-with-swiftsyntax/) that covers the basics

If there is a 'Missing package product' error - reset package menu option, do swift package update
