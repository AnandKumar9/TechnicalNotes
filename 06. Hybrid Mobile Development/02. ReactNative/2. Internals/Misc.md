##### How native code and JS interact at runtime

When the project is compiled by Xcode, what happens is - 

1. Native frameworks (UIKit, any custom native code, etc.) - Compiled into native machine code. These are in Swift, C, Objective-C, etc.
2. ReactNative library's own native code (typically C, C++, Swift) - Compiled into native machine code.
3. All the custom JS/TS code written by developers - Transpiled into a JS bundle, Hermes (if used) precompiles that into JS Hermes bytecode

During runtime, when a JS code for UI creation is interpreted at runtime it invokes compiled native code which is the equivalent of something like this

```objective-c
[UIManager createViewWithTag:123 viewName:@"RCTView" props:props];
[[RCTView alloc] initWithFrame:frame];
```

And that is how it works, there are some very basic native UI components that get compiled and shipped, and they receive values at runtime (from interpreted JS) to actually instantiate themselves in many different ways.

ChatGPT [link](https://chatgpt.com/g/g-p-68d848671ccc819190a215c58c55d1a2-react-native/c/68eaa2cb-5cc4-8321-9a40-94d37d3d55eb)