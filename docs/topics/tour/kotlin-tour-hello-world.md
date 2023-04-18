[//]: # (title: Hello world)

<microformat>
    <p>This is the first part of the <strong>Beginner</strong> Kotlin tour:</p>
    <p><img src="icon-1.svg" width="20" alt="First step" /> <strong>Hello world</strong><br />
        <img src="icon-2-todo.svg" width="20" alt="Second step" /> <a href="kotlin-tour-types.md">Basic types</a><br />
        <img src="icon-3-todo.svg" width="20" alt="Third step" /> <a href="kotlin-tour-collections.md">Collections</a><br />
        <img src="icon-4-todo.svg" width="20" alt="Fourth step" /> <a href="kotlin-tour-control-flow.md">Control flow</a><br />
        <img src="icon-5-todo.svg" width="20" alt="Fifth step" /> <a href="kotlin-tour-functions.md">Functions</a><br />
        <img src="icon-6-todo.svg" width="20" alt="Sixth step" /> <a href="kotlin-tour-classes-part-1.md">Classes</a><br />
        <img src="icon-7-todo.svg" width="20" alt="Final step" /> <a href="kotlin-tour-null-safety.md">Null safety</a></p>
</microformat>

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
* the body of a function is written within curly braces `{}`
* [`println()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.io/println.html) and [`print()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.io/print.html) functions print their arguments to standard output

Functions will be discussed in more detail in a couple of chapters. Until then, all examples use the `main` function.

## Variables

All programs need to be able to store data, and variables help you to do just that. In Kotlin, you can declare:
* read-only variables with `val`
* mutable variables with `var`

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

## String templates

It's useful to know how to print the contents of variables to standard output. You can do this with string templates. 
You can use template expressions to access data stored in variables and other objects, and convert them into strings.
A string value is a sequence of characters in double quotes (`"`). Template expressions always start with a dollar sign (`$`).

For example:

```kotlin
fun main() { 
//sampleStart
    val customers = 10
    println("There are $customers customers")
    //There are 10 customers
//sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="string-templates-kotlin"}

For more information, see [String templates](strings.md).

You'll notice that there aren't any types declared for variables. Kotlin has inferred the type itself: `Int`. The different
Kotlin basic types and how to declare them are discussed in the [next chapter](kotlin-tour-types.md).

## Practice

### Exercise 1 {initial-collapse-state="collapsed"}
Complete the code below to make the function print `"OK"` to standard output. Test your code in [Playground](https://play.kotlinlang.org).
```kotlin
    fun main() {
        TODO()
    }
```
{initial-collapse-state="expanded" validate="false"}

|---|---|
```kotlin
    fun main() {
        println("OK")
    }
```
{initial-collapse-state="collapsed" collapsed-title="Example solution"}
