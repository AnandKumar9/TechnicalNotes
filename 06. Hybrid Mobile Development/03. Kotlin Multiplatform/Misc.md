**How does it render UI**

(As per ChatGPT), Kotlin Multiplatform (KMP) does not handle UI rendering directly on iOS — it does not map to native UI elements on its own. Instead, KMP focuses on sharing business logic, and the UI layer is still written using platform-native tools.

There are some UI toolkits built on top of KMP that aim to share UI code. Like Jetpack Compose Multiplatform (JCM), but that uses its own rendering engine known as Skiko (which in turn wraps Flutter's Skia) i.e. does not map directly to high level native UI frameworks such as UIKit, etc. Some projects attempt to call native UIKit/SwiftUI APIs from Kotlin using bindings or wrapper (such as KMMBridge), but it is not mainstream and is verbose.