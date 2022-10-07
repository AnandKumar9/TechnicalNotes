Kotlin bootcamp - https://developer.android.com/codelabs/kotlin-bootcamp-welcome#1
Kotlin reference - https://kotlinlang.org/docs/home.html
Android with Kotlin bootcamp - https://developer.android.com/courses/android-basics-kotlin/course

-------

Distinguishes between nullable and non-nullable data types.
Strongly typed, and it does a lot of type inference.
Does have has lambdas, coroutines, and properties.

```
data class Aquarium (var temperature: Int = 0)
```

The code compiles so that you can use Java and Kotlin code side-by-side, and continue to use your favorite Java libraries.

JDK should be installed to be able to run Kotlin programs. JRE (Java Runtime Engine) is what is actually needed for running Kotlin programs, but JDK includes JRE in addition to other development tools.

Had to install JDK and then these things returned a version.
java -version
javac -version

Test frameworks - JUnit, TestNG


Kotlin REPL is like a terminal console that can be used to do some basic REPL testing (inspite of proper code already being there in the standard editor). (Tools > Kotlin > Kotlin REPL)
> A read–eval–print loop (REPL), also termed an interactive toplevel or language shell, is a simple interactive computer programming environment that takes single user inputs, executes them, and returns the result to the user; a program written in a REPL environment is executed piecewise.[

Basic function -
```
fun printHello() {
    println("Hello World")
}

printHello()
```

Operators - +, -, *, /
number types - `Int`, `Long`, `Double`, `Float`. Numbers are primitive, but can still have methods as if they were objects.
```
2.times(3)
res2: kotlin.Int = 6
```

It is possible to create actual object wrappers around numbers, which is known as `Boxing`. Boxing happens automatically, such as for collections, where numbers are boxed and unboxed as needed. It is expensive though.

Declaring variables -
```
val i: Int = 6
```

Kotlin does not implicitly convert between number types, so you can't assign a short value directly to a long variable, or a Byte to an Int. This is because implicit number conversion is a common source of errors in programs. You can always assign values of different types by casting.
```
val i: Int = 6
val b1 = i.toByte()
```
`toInt()`, `toString()`, `toDouble()`

Kotlin allows you to place underscores in the numbers, where it makes sense to you.
```
val oneMillion = 1_000_000
val hexBytes = 0xFF_EC_DE_5E
```

`var` is used to declare a variable whose value can be changed, and `val` for a variable whose value cannot change.

`""` is used for strings and `''` for single characters. `$variable` is used for string templates.
```
val numberOfFish = 5
val numberOfPlants = 12
"I have $numberOfFish fish" + " and $numberOfPlants plants"
```


-----

Conditions and Booleans

Operators - `<`, `==`, `>`, `!=`, `<=`, `>=`

```
val fish = 50
if (fish in 1..100) {
    println(fish)
}
```
`elseif` exists too.

`when` is like `switch` in other languages.
```
when (numberOfFish) {
    0  -> println("Empty tank")
    in 1..39 -> println("Got fish!")
    else -> println("That's a lot of fish!")
}
```

-----

Nullability

By default, variables cannot be null. To have something be nullable, it should be declared with a `?` (i.e. like optionals in Swift).

```
var rocks: Int = null     // ⇒ error: null can not be a value of a non-null type Int
var marbles: Int? = null
```

`?` can also check if a variable is null.
```
var fishFoodTreats = 6
fishFoodTreats = fishFoodTreats?.dec()
```

`?:` is just like the nil-coalescing operator in Swift.
```
fishFoodTreats = fishFoodTreats?.dec() ?: 0
```

The not-null assertion operator, `!!` (double-bang), converts any value to a non-null type and throws an exception if the value is null. That is if you'd really prefer `NullPointerExceptions`. Using `!!` is not a recommended practice.
```
val len = s!!.length   // throws NullPointerException if s is null
```

-----

Arrays, Lists, Loops

```
val school = listOf("mackerel", "trout", "halibut")

val myList = mutableListOf("tuna", "salmon", "shark")
myList.remove("shark")
```

Unlike lists, arrays are immutable and their size are fixed.
With an array defined with `val`, you can't change which array the variable refers to, but you can still change the contents of the array.
```
val school = arrayOf("shark", "salmon", "minnow")
val numbers = intArrayOf(1,2,3)
```

An array created using `arrayOf` can have any type inserted into it.
```
val mix = arrayOf("fish", 2)
```

You can nest arrays and lists.

```
val array = Array (5) { it * 2 }
```

A `for` loop.
```
val school = arrayOf("shark", "salmon", "minnow")
for (element in school) {
    print(element + " ")
}

for ((index, element) in school.withIndex()) {
    println("Item at $index is $element\n")
}
```

You can step backward using `downTo` and change increments using `step`.
```
for (i in 5 downTo 1) print(i)

for (i in 3..6 step 2) print(i)
```

`while` loop.
```
var bubbles = 0
while (bubbles < 50) {
    bubbles++
}
```

`do...while` loop.
```
do {
    bubbles--
} while (bubbles > 50)
```

-----

Functions

When a function doesn't return anything, the return type is actually `kotlin.Unit`.

Kotlin not configured
rm -rf .idea .gradle gradle
Reopen the project, and let Gradle finish all its downloads

fun main(args: Array<String>) {

In Kotlin, almost everything is an expression and has a value—even if that value is kotlin.Unit.
Loops are exceptions to "everything has a value." There's no sensible value for for loops or while loops, so they do not have values. 

import java.util.* - Has things like Random(), nextInt(), etc.

Use a when expression without an argument, which in Kotlin acts as a series of if/else if checks.

fun fishFood (day : String) : String {
    return when (day) {
        "Monday" -> "flakes"
        "Wednesday" -> "redworms"
        "Thursday" -> "granules"
        "Friday" -> "mosquitoes"
        "Sunday" -> "plankton"
        else -> "nothing"
    }
}

Default value for arguments - fun swim(speed: String = "fast") {}

swim()   // uses default speed
swim("slow")   // positional argument
swim(speed="turtle-like")   // named parameter

Compact functions ~ single-expression functions. When a function returns the results of a single expression, you can specify the body of the function after an = symbol, omit the curly braces {}, and omit the return.

fun isTooHot(temperature: Int) = temperature > 30


-----

Functions  - Filters

Filters are a handy way to get part of a list based on some condition.

By default, filter is eager, and each time you use the filter, a list is created.
To make the filter lazy, you can use a Sequence, which is a collection that can only look at one item at a time, starting at the beginning, and going to the end. 

val decorations = listOf ("rock", "pagoda", "plastic plant", "alligator", "flowerpot")
val eager = decorations.filter { it [0] == 'p' }  // // eager, creates a new list

// lazy, will wait until asked to evaluate
val filtered = decorations.asSequence().filter { it[0] == 'p' }

// force evaluation of the lazy list
val newList = filtered.toList()

-----

Lambdas and higher-order functions 

A lambda is an expression that makes a function. What makes this useful is that the lambda expression can now be passed as data. 
You can create a higher-order function by passing a lambda to another function. (The real power of lambdas is using them to create higher-order functions, where the argument to one function is another function.)

Lambdas -
val waterFilter = { dirty : Int -> dirty / 2}
println(waterFilter(20))

val waterFilter: (Int) -> Int = { dirty -> dirty / 2 }

Higher-order functions -
fun updateDirty(dirty: Int, operation: (Int) -> Int): Int {
   return operation(dirty)
}

Kotlin prefers that any parameter that takes a function is the last parameter. When working with higher-order functions, Kotlin has a special syntax, called the last parameter call syntax, which lets you make the code even more concise. In this case, you can pass a lambda for the function parameter, but you don't need to put the lambda inside the parentheses.

var dirtyLevel = 19;
dirtyLevel = updateDirty(dirtyLevel) { dirtyLevel -> dirtyLevel + 23}
println(dirtyLevel)

-------

Classes - 

An interface is a specification that a class can implement. So like protocols in Swift.
Packages are a way to group related code to keep it organized, or to make a library of code.

IntelliJ - New Package (has reverse domain name)

class Aquarium {
    var width: Int = 20
    var height: Int = 40
    var length: Int = 100

    fun printSize() {
        println("Width: $width cm " +
                "Length: $length cm " +
                "Height: $height cm ")
    }
}

Under the hood, Kotlin automatically creates getters and setters for the properties.

class Aquarium(length: Int = 100, width: Int = 20, height: Int = 40) { .. Works as Constructor

class Aquarium(var length: Int = 100, var width: Int = 20, var height: Int = 40) { .. Even properties need not be exolicitly declared.

init blocks. There can be multiple initializer blocks. They all run in the order in which they are defined.

    init {
        println("aquarium initializing")
    }
    init {
        // 1 liter = 1000 cm^3
        println("Volume: ${width * length * height / 1000} l")
    }

Kotlin coding style says each class should have only one constructor, using default values and named parameters. Before writing a secondary constructor, consider whether a [factory function](https://kotlinlang.org/docs/coding-conventions.html#infix-functions)x` would work instead, to keep the class definition clean.

Every secondary constructor must call the primary constructor first, either directly using this(), or indirectly by calling another secondary constructor.

constructor(numberOfFish: Int) : this() {
    // 2,000 cm^3 per fish + extra room so water doesn't spill
    val tank = numberOfFish * 2000 * 1.1
}

Explicit property getter and settr.
var volume: Int
    get() = width * height * length / 1000
    set(value) {
        height = (value * 1000) / (width * length)
    }

Visibility modifiers - 
public - visible outside the class. The default.
internal - only be visible within that module. A module is a set of Kotlin files compiled together, for example, a library or application.
private - only visible in that class (or source file if you are working with functions).
protected - Same as private, but it will also be visible to any subclasses

If you want a property that your code can read or write, but outside code can only read, you can leave the property and its getter as public and declare the setter private.

var volume: Int
    get() = width * height * length / 1000
    private set(value) {
        height = (value * 1000) / (width * length)
    }

----

Subclasses and Inheritance

By default, classes cannot be subclassed. Similarly, properties and member variables cannot be overridden by subclasses (though they can be accessed).

You must mark a class as open to allow it to be subclassed. Similarly, you must mark properties and member variables as open, in order to override them in the subclass.

Subclasses must declare their constructor parameters explicitly.

class TowerTank (override var height: Int, var diameter: Int): Aquarium(height = height, width = diameter, length = diameter) {

----

Abstract classes cannot be instantiated on its own. It can have a constructor though. They are always open and don't need to be marked as open. Properties and methods of an abstract class are non-abstract unless you explicitly mark them with the abstract keyword. That means subclasses can use them as given. If properties or methods are abstract, the subclasses must implement them.

abstract class AquariumFish {
    abstract val color: String
}

class Shark: AquariumFish() {
    override val color = "gray"
}

class Plecostomus: AquariumFish() {
    override val color = "gold"
}

Creating an Interface.

interface FishAction  {
    fun eat()
}

When you use interfaces to compose a class, the class's functionality is extended by way of the class instances that it contains. Composition often leads to better encapsulation, lower coupling (interdependence), cleaner interfaces, and more usable code. For these reasons, using composition with interfaces is the preferred design. 

Use an interface if you have a lot of methods and one or two default implementations
Use an abstract class any time you can't complete a class. 
> Didn't study much, should revisit.

Interface delegation is an advanced technique where the methods of an interface are implemented by a helper (or delegate) object, which is then used by a class. This technique can be useful when you use an interface in a series of unrelated classes.

Kotlin lets you declare a class where you can only create one instance of it by using the keyword object instead of class.

object GoldColor : FishColor {
    override val color = "gold"
}

class Plecostomus:  FishAction, FishColor by GoldColor {

----

Data class

A data class is similar to a struct in some other languages—it exists mainly to hold some data—but a data class object is still an object. 

data class Decoration(val rocks: String) {
}

val decoration1 = Decoration("granite")

In Kotlin, using == on data class objects is the same as using equals() (structural equality). If you need to check whether two variables refer to the same object (referential equality), use the === operator. 

To get at the properties of a data object and assign them to variable. This is called destructuring.
val rock = decoration.rock
val (rock, wood, diver) = decoration

----

Singleton classes -  object. There can be only one instance of it.
object GoldColor : FishColor {
   override val color = "gold"
}

Enums -  You can also get the ordinal value of an enum using the ordinal property, and its name using the name property.

enum class Direction(val degrees: Int) {
    NORTH(0), SOUTH(180), EAST(90), WEST(270)
}

println(Direction.EAST.ordinal)

Sealed class - A sealed class is a class that can be subclassed, but only inside the file in which it's declared.

sealed class Seal
class SeaLion : Seal()
class Walrus : Seal()

For example, sealed classes are great for returning success or error from a network API.

----

Pairs and Triples

Pairs and triples are premade data classes for 2 or 3 generic items. 

You can create a pair by creating an expression connecting two values, such as two strings, with the keyword to, then using .first or .second to refer to each value.

val equipment = "fish net" to "catching fish"
println("${equipment.first} used for ${equipment.second}")

You create a triple using Triple() with 3 values. Use .first, .second and .third to refer to each value.

val numbers = Triple(6, 9, 42)
println(numbers.toString())
println(numbers.toList())

Separating pairs and triples into their parts is called destructuring. 

destructuring pairs and triples works the same as with data classes, (understand)

----

List, MutableList functions - add(element: E), remove(element: E), reversed(), contains(element: E), subList(fromIndex: Int, toIndex: Int)

In Kotlin, you can map pretty much anything to anything else using hashMapOf(). Hash maps are sort of like a list of pairs, where the first value acts as a key. (So like a dictionary?)

If a key isn't in the map, trying to return the matching disease returns null. Depending on the map data, it may be common to have no match for a possible key. 
getOrElse()
getOrDefault()

Immutable collections are particularly useful in a threaded environment where there might be problems if multiple threads touch the same collection.

------

const val - 

The value for const val is determined at compile time, where as the value for val is determined during program execution, which means, val can be assigned by a function at run time.

val value1 = complexFunctionCall() // OK
const val CONSTANT1 = complexFunctionCall() // NOT ok

In addition, const val only works at the top level, and in singleton classes declared with object, not with regular classes. You can use this to create a file or singleton object that contains only constants, and import them as needed.

object Constants {
    const val CONSTANT2 = "object constant"
}
val foo = Constants.CONSTANT2


Companion object - 

Kotlin does not have a concept of class level constants.

To define constants inside a class, you have to wrap them into companion objects declared with the companion keyword. 

class MyClass {
    companion object {
        const val CONSTANT3 = "constant in companion"
    }
}

The basic difference between companion objects and regular objects is:

Companion objects are initialized from the static constructor of the containing class, that is, they are created when the object is created.
Regular objects are initialized lazily on the first access to that object; that is, when they are first used.

---------

Extensions - 

Extension functions allow you to add functions to an existing class without having to access its source code.

fun String.hasSpaces(): Boolean {
    val found = this.find { it == ' ' }
    return found != null
}
println("Does it have spaces?".hasSpaces())

Extension functions only have access to the public API of the class they're extending. Variables that are private can't be accessed.

Kotlin also lets you add extension properties. 

val AquariumPlant.isGreen: Boolean
   get() = color == "green"

The class you extend is called the receiver, and it is possible to make that class nullable. If you do that, the this variable used in the body can be null, so make sure you test for that. 
The ?. operator can be paired with apply to check for null before executing code. For example: this?.apply { println("removing $this") }

---------

Generics -

class MyList<T> {
    fun get(pos: Int): T {
        TODO("implement")
    }
    fun addItem(item: T) {}
}

in and out types - 

An in type is a type that can only be passed into a class, not returned. An out type is a type that can only be returned from a class.

The in and out types are directives for Kotlin's type system. Explaining the whole type system is outside the scope of this bootcamp (it's pretty involved); however, the compiler will flag types that are not marked in and out appropriately, so you need to know about them.

val and var are about the VALUES of variables. 
in and out are about the TYPES of variables. 

class Aquarium<out T: WaterSupply>(val waterSupply: T) {
    ...
}

interface Cleaner<in T: WaterSupply> { }

Need to try these.

Generic functions - 

fun <T: WaterSupply> isWaterClean(aquarium: Aquarium<T>) { ... }

---------

Reified types -

Reified types are sometimes necessary because of type erasure. Reified types, unlike generic types, persist to runtime.

All generic types are only used at compile time by Kotlin. This lets the compiler make sure that you're doing everything safely. By runtime all the generic types are erased, hence the earlier error message about checking an erased type.

Use the check() function to verify your code is running as expected. For example: check(!waterSupply.needsProcessing) { "water supply needs processing first" } 

What are these really?

---------

Annotations - 

Annotations are a way of attaching metadata to code, and are not something specific to Kotlin. The annotations are read by the compiler and used to generate code or logic. Many frameworks, such as Ktor and Kotlinx, as well as Room, use annotations to configure how they run and interact with your code. You are unlikely to encounter any annotations until you start using frameworks .

@file:JvmName("InteropFish")
class InteropFish {
   companion object {
       @JvmStatic fun interop()
   }
}

This says the exported name of this file is InteropFish with the JvmName annotation; the JvmName annotation is taking an argument of "InteropFish". In the companion object, @JvmStatic tells Kotlin to make interop() a static function in InteropFish.

You can also create your own annotations, but this is mostly useful if you are writing a library that needs particular information about classes at runtime, that is reflection.

For creating annotations - 
annotation class ImAPlant
Annotations can target getters or setters. When they do, you can apply them with the @get: or @set: prefix. This comes up a lot when using frameworks with annotations.

There are also annotations that are available through the Kotlin standard library that control the way code is compiled. They're really useful if you're exporting Kotlin to Java code, but otherwise you don't need them that often.

---------

Labeled breaks -

 A break qualified with a label jumps to the execution point right after the loop marked with that label. This is particularly useful when dealing with nested loops.

Any expression in Kotlin may be marked with a label. Labels have the form of an identifier followed by the @ sign.

fun labels() {
    outerLoop@ for (i in 1..100) {
         print("$i ")
         for (j in 1..100) {
             if (i > 10) break@outerLoop  // breaks to outer loop
        }
    }
}



---------

Passing a lambda or other function as an argument to a function creates a higher-order function.


---------

Lambdas and higher-order functions are really useful, but there is something you should know: lambdas are objects. A lambda expression is an instance of a Function interface, which is itself a subtype of Object.

The Function interface has a method, invoke(), which is overridden to call the lambda expression. 

Kotlin provides inline as a way to handle this case to reduce overhead during runtime by adding a bit more work for the compiler.

Use inline carefully, but it can help reduce resource usage by your program.

SAM, Single Abstract Method, is a common pattern, and made simpler with lambdas. The basic pattern is: Class.singleAbstractMethod { lamba_of_override }

https://developer.android.com/codelabs/kotlin-bootcamp-sams#5