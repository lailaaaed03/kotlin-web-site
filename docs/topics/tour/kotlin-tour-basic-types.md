[//]: # (title: Basic types)

<microformat>
    <p>This is the second part of the <strong>Beginner</strong> Kotlin tour:</p>
    <p><img src="icon-1-done.svg" width="20" alt="First step" /> <a href="kotlin-tour-hello-world.md">Hello world</a><br />
        <img src="icon-2.svg" width="20" alt="Second step" /> <strong>Basic types</strong><br />
        <img src="icon-3-todo.svg" width="20" alt="Third step" /> <a href="kotlin-tour-collections.md">Collections</a><br />
        <img src="icon-4-todo.svg" width="20" alt="Fourth step" /> <a href="kotlin-tour-control-flow.md">Control flow</a><br />
        <img src="icon-5-todo.svg" width="20" alt="Fifth step" /> <a href="kotlin-tour-functions.md">Functions</a><br />
        <img src="icon-6-todo.svg" width="20" alt="Sixth step" /> <a href="kotlin-tour-classes-part-1.md">Classes</a><br />
        <img src="icon-7-todo.svg" width="20" alt="Final step" /> <a href="kotlin-tour-null-safety.md">Null safety</a></p>
</microformat>

Kotlin has data types that tell the compiler what functions and properties an object has.

In the last chapter, Kotlin's powerful type inference inferred from the previous example that `customers` has type: [`Int`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-int/).
As `Int` is a number data type, you can perform arithmetic operations with `customers`:

```kotlin
fun main() {
//sampleStart
    var customers = 10

    //Some customers leave the queue
    customers = 8

    customers = customers + 3 //Example of addition: 11
    customers += 7            //Example of addition: 18
    customers -= 3            //Example of subtraction: 15
    customers *= 2            //Example of multiplication: 30
    customers /= 3            //Example of division: 10

    println(customers) // 10
//sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="arithmetic-kotlin"}

> `+=`, `-=`, `*=`, `/=`, and `%=` are augmented assignment operators. For more information, see [Augmented assignments](operator-overloading.md#augmented-assignments).
{type="info"}

In total, Kotlin has the following basic types:

|Category| Basic types|
|--|--|
| Integers | `Byte`, `Short`, `Int`, `Long` |
| Unsigned integers | `UByte`, `UShort`, `UInt`, `ULong` |
| Floating-point | `Float`, `Double` |
| Booleans | `Boolean` |
| Characters | `Char` |
| Strings | `String` |

For more information on basic types and their properties, see [Basic types](basic-types.md).

With this knowledge, you can now declare variables and initialize them later. Kotlin can manage this as long as variables
are initialized before the first read.

To declare a variable without initializing it, specify its type with `:`. 

```kotlin
fun main() {
//sampleStart
    val d: Int               // Variable declared without initialization
    d = 3                    // Variable initialized
    
    val e: String = "hello"  //Variable explicitly typed and initialized

    println(d)               // Variable can be read because it has been initialized
    println(e)
//sampleEnd
}
```

Now that you know how to declare basic types, it's time to learn about [collections](kotlin-tour-collections.md).

## Practice

<deflist collapsible="true">
    <def title="Exercise 1">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit
    </def>
</deflist>

<deflist collapsible="true">
    <def title="Hint">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit
    </def>
</deflist>

```kotlin
    fun main() {
        println("Hello, world!")
    }
```
{initial-collapse-state="collapsed" collapsed-title="Example solution"}
