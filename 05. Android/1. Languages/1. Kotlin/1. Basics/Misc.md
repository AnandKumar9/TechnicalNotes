Kotlin bootcamp - [developer.android.com](https://developer.android.com/codelabs/kotlin-bootcamp-welcome#1) <br>
Kotlin reference - [kotlinlang.org](https://kotlinlang.org/docs/home.html) <br>

---------

#### Package and Module

At a very high level, `Packages` collect related classes, and correspond roughly to directories. `Modules` are a much higher level and correspond to projects and/or compiler runs. ([link](https://stackoverflow.com/a/57531914/1135417))

The necessary package, etc. should be imported in the beginning of the file. The below import brings in functions like `Random()`, `nextInt()`, etc.
```
import java.util.*
```

Packages are typically named as reverse domain name.

#### Reified types

`Reified types` are sometimes necessary because of type erasure. Reified types, unlike generic types, persist to runtime.

All generic types are only used at compile time by Kotlin. This lets the compiler make sure that you're doing everything safely. By runtime all the generic types are erased, hence the earlier error message about checking an erased type.

Use the `check()` function to verify your code is running as expected. For example -
```
check(!waterSupply.needsProcessing) { "water supply needs processing first" }
```

> What are these really?

#### Annotations

Annotations are a way of attaching metadata to code, and are not something specific to Kotlin. The annotations are read by the compiler and used to generate code or logic. Many frameworks, such as Ktor and Kotlinx, as well as Room, use annotations to configure how they run and interact with your code. You are unlikely to encounter any annotations until you start using frameworks .

```
@file:JvmName("InteropFish")
class InteropFish {
   companion object {
       @JvmStatic fun interop()
   }
}
```

This says the exported name of this file is InteropFish with the JvmName annotation; the JvmName annotation is taking an argument of "InteropFish". In the companion object, `@JvmStatic` tells Kotlin to make `interop()` a static function in InteropFish.

You can also create your own annotations, but this is mostly useful if you are writing a library that needs particular information about classes at runtime, that is reflection.

##### For creating annotations

```
annotation class ImAPlant
```

Annotations can target getters or setters. When they do, you can apply them with the `@get:` or `@set:` prefix. This comes up a lot when using frameworks with annotations.

There are also annotations that are available through the Kotlin standard library that control the way code is compiled. They're really useful if you're exporting Kotlin to Java code, but otherwise you don't need them that often.



#### Some standard functions

`repeat` executes the given function action (i.e. lambda?) specified number of times. A zero-based index of current iteration is passed as a parameter.

```
// greets three times
repeat(3) {
    println("Hello")
}

// greets with an index
repeat(3) { index ->
    println("Hello with index $index")
}
```

> in the second example above the lambda has a parameter but in the first example it does not. How is that done, are there multiple implementations of `repeat` internally.

####  Exception Handling

A sample snippet for exception handling.

```
try {
    val listResult = MarsApi.retrofitService.getPhotos()
    _status.value = listResult
} catch (e: Exception) {
    _status.value = "Failure: ${e.message}"
}
```

##### Scope functions﻿

The Kotlin standard library contains several functions whose sole purpose is to execute a block of code within the context of an object. When you call such a function on an object with a lambda expression provided, it forms a temporary scope. In this scope, you can access the object without its name. Such functions are called scope functions. There are five of them - `let`, `run`, `with`, `apply`, and `also`.

`let` is one of Kotlin's Scope functions which lets you execute a code block within the context of an object. ([Reference](https://kotlinlang.org/docs/scope-functions.html))

```
imgUrl?.let {
    val imgUri = imgUrl.toUri().buildUpon().scheme("https").build()
    imgView.load(imgUri) {
        placeholder(R.drawable.loading_animation)
        error(R.drawable.ic_broken_image)
    }
}
```
