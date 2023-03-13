[//]: # (title: Functions)

<microformat>
    <p>This is the fourth part of the <strong>First steps</strong> Kotlin tour.</p>
    <p><img src="icon-1-done.svg" width="20" alt="First step"/> <a href="kotlin-tour-hello-world.md">Set up an environment</a><br/><img src="icon-2-done.svg" width="20" alt="Second step"/> <a href="kotlin-tour-types.md">Basic types</a><br/><img src="icon-3-done.svg" width="20" alt="Third step"/> <a href="kotlin-tour-control-flow.md">Control flow</a><br/><img src="icon-4.svg" width="20" alt="Fourth step"/> <strong>Functions</strong><br/><img src="icon-5-todo.svg" width="20" alt="Fifth step"/> Classes</p>
</microformat>

You can declare your own functions in Kotlin using the `fun` keyword. Add parameters within parentheses `()` using Pascal
notation - _name: type_. You must declare a type for each parameter and multiple parameters must be separated by commas.
You also need to declare the return type of your function, separated by a colon `:` after the function's parentheses `()`.
Add any code that you want to be executed as part of your function inside curly brackets `{}`. Use the `return` keyword
to exit or return an object from a function.

In the below example:
* `x` and `y` are function parameters
* `x` and `y` have type `Int`
* the function's return type is `Int`
* the function returns a sum of `x` and `y` when called

```kotlin
fun sum(x: Int, y: Int): Int {
    return x + y
}

fun main() {
    println(sum(1, 2))
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-simple-function-kotlin"}

> We recommend in our [coding conventions](coding-conventions.md#function-names) that you name functions starting with 
> a lowercase letter and use camel case with no underscores.
> 
{type="tip"}

## Named arguments

When calling your function, you don't have to include the parameter name. However, if you do, then you can change the order
that the parameters are provided.

In the below example, we use [string templates](strings.md#string-templates) (`$`) to access
the parameter values, convert them to `String` type, and then concatenate them into a string for printing.

```kotlin
fun printMessageWithPrefix(message: String, prefix: String = "Info") {
    println("[$prefix] $message")
}

fun main() {
    printMessageWithPrefix(prefix = "Log", message = "Hello") //Using named arguments with swapped parameter order
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-named-arguments-function-kotlin"}

## Default parameter values

You can define default values for your function parameters. Any parameter with a default value can be omitted when
calling your function. To declare a default value, use the assignment operator `=` after the type.

In the below example, we use [string templates](strings.md#string-templates) (`$`) to access
the parameter values, convert them to `String` type, and then concatenate them into a string for printing.

```kotlin
fun printMessageWithPrefix(message: String, prefix: String = "Info") {
    println("[$prefix] $message")
}

fun main() {
    printMessageWithPrefix("Hello", "Log") //Function called with both parameters
    printMessageWithPrefix("Hello")        //Function called only with message parameter
    printMessageWithPrefix(prefix = "Log", message = "Hello")
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-default-param-function-kotlin"}

> You can skip specific parameters with default values, rather than omitting them all. However, after the 
> first skipped parameter, you must name all subsequent parameters.
>
{type="note"}

## Unit type

If your function doesn't return a useful value then it's return type is `Unit`. `Unit` is a type with only one value - 
`Unit`. 

> You don't have to declare that `Unit` is returned explicitly in your function body.
>
{type="note"}

```kotlin
fun printMessage(message: String): Unit {
    println(message)
    // `return Unit` or `return` is optional
}

fun main() {
    printMessage("Hello")
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-unit-function-kotlin"}

## Single-expression functions

To make your code more concise, you can use single-expression functions. For example, the below function can be shortened:

```kotlin
fun sum(x: Int, y: Int): Int {
    return x + y
}

fun main() {
    println(sum(1, 2))
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-simple-function-before-kotlin"}

We can remove the curly braces `{}` and declare the function body using the assignment operator `=`. And due to Kotlin's
powerful type inference, we can also omit the return type. This function then becomes one line:

```kotlin
fun sum(x: Int, y: Int) = x + y

fun main() {
    println(sum(1, 2))
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-simple-function-after-kotlin"}

> Omitting the return type is only possible when your function has no body (`{}`). Unless your function's return type
> is `Unit`.
> 
{type="note"}

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
[Learn about classes](kotlin-tour-classes-part-1.md)
