[//]: # (title: Basic types)

<microformat>
    <p>This is the second part of the <strong>Beginner</strong> Kotlin tour.</p>
    <p><img src="icon-1-done.svg" width="20" alt="First step"/> <a href="kotlin-tour-hello-world.md">Hello world</a><br/><img src="icon-2.svg" width="20" alt="Second step"/> <strong>Basic types</strong><br/><img src="icon-3-todo.svg" width="20" alt="Third step"/> <a href="kotlin-tour-control-flow.md">Control flow</a><br/><img src="icon-4-todo.svg" width="20" alt="Fourth step"/> <a href="kotlin-tour-functions.md">Functions</a><br/><img src="icon-5-todo.svg" width="20" alt="Fifth step"/> <a href="kotlin-tour-classes-part-1.md">Classes</a></p>
</microformat>

In Kotlin, we have data types that tell the compiler what functions and properties an object has.

In the last chapter, Kotlin's powerful type inference inferred from our example that `customers` has type: [`Int`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-int/).
Thus, we can perform arithmetic operations with `customers`:

```kotlin
fun main() {
    val popcorn = 5
    val hotdog = 7 
//sampleStart
    var customers = 10
    
    //Some customers leave the queue
    customers = 8
    
    customers+= 7 //Example of addition: 15
    customers-= 3 //Example of subtraction: 12
    customers*= 2 //Example of multiplication: 24
    customers/= 3 //Example of division: 8

    println(customers) // 8
//sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="arithmetic-kotlin"}

> `+=`, `-=`, `*=`, `/=`, and `%=` are augmented assignment operators. For more information, see [Augmented assignments](operator-overloading.md#augmented-assignments).
{type="info"}

Kotlin has the following basic types:
* Integers:
  * `Byte`
  * `Short`
  * `Int`
  * `Long`
* Unsigned integers:
  * `UByte`
  * `UShort`
  * `UInt`
  * `ULong`
* Floating-point types:
  * `Float`
  * `Double`
* Booleans:
  * `Boolean`
* Characters:
  * `Char`
* Strings:
  * `String`

For more information on basic types and their properties, see [Basic types](basic-types.md).

With this knowledge, we can now declare variables and initialize them later. Kotlin can manage this as long as your variables
are initialized before the first read.

To declare a variable without initializing it, specify its type with `:`. 

```kotlin
fun main() {
//samplesStart
    val d: Int // Variable declared without initialization
    d = 3      // Variable initialized

    println(d) // Variable can be read because it has been initialized
//sampleEnd
}
```

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

## Next

[Learn about control flow](kotlin-tour-control-flow.md)
