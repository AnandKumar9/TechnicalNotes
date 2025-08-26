(From ChatGPT) Unlike ReactNative, Flutter components are not rendered using native UI elements. Instead Flutter has its own UI rendering engine named **Skia**. 

> Building a custom UI engine for iOS, like Skia (used by Flutter), is a highly advanced and specialized task that involves working far beneath UIKit and Core Animation, typically with Core Graphics, Metal, or OpenGL ES. 

So it does of course eventually use native UI frameworks but not the high level frameworks like UIKit, etc. Instead it uses low level frameworks such as Metal, CoreGraphics, etc.