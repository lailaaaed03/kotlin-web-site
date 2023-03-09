[//]: # (title: Hello world)

Below is a simple program that prints "Hello, world!":

```kotlin
fun main() {
    println("Hello, world!")
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="hello-world-kotlin"}

In Kotlin:
* `fun` is used to declare a function
* the entry point is the `main` function
* function arguments are written within parentheses `()`
* the body of a function is written within curly brackets `{}`
* [`println()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.io/println.html) and [`print()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.io/print.html) functions print their arguments to standard output

We'll discuss functions more in a couple of chapters.

## Variables

All programs need to be able to store data and variables help you to do just that. In Kotlin, you can declare:
* read-only variables with `val`
* <tooltip tooltip="mutable"> mutable </tooltip> variables with `var`

To assign a value, use the assignment operator `=`.

```kotlin
fun main() { 
//sampleStart
    val popcorn = 5
    val hotdog = 7
    var customers = 10
    
    //Some customers leave the queue
    customers = 8
//sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="variables-kotlin"}

> Variables can be declared at top level as well as within functions.
{type="info"}

As `customers` is a mutable variable, its value can be reassigned after declaration.

> We recommend that you declare all variables as read-only (`val`) by default. Declare mutable variables (`var`) only if 
> necessary.
{type="info"}

You'll notice that we haven't declared any types for our variables. Kotlin has inferred the type for us: `Int`. We'll cover
the different Kotlin types and how to declare them in the next chapter.

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
[Learn about Kotlin basic types](kotlin-tour-types.md)
