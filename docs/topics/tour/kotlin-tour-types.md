[//]: # (title: Learn about Kotlin basic types)

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

[Learn about control flow]()
