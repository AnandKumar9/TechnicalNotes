### EmptyView, EquatableView, AnyView, TupleView

`EmptyView` is view that doesn’t contain any content. Its used mostly by SwiftUI internally and is rarely actually needed as a public API. Its not a container kind of view.

`EquatableView` is a view that can be used for comparison with its previous value and prevents its child updating if its new value is the same as its old value. Again, this does not seem like something that is needed as a public API.

`AnyView` is a type-erased view.

`TupleView` is a tuple (i.e. combination) of various views. Again, this is used quite a bit by SwiftUI internally.
