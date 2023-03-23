[//]: # (title: Functions)

<microformat>
    <p>This is the fourth part of the <strong>Beginner</strong> Kotlin tour.</p>
    <p><img src="icon-1-done.svg" width="20" alt="First step"/> <a href="kotlin-tour-hello-world.md">Hello world</a><br/><img src="icon-2-done.svg" width="20" alt="Second step"/> <a href="kotlin-tour-types.md">Basic types</a><br/><img src="icon-3-done.svg" width="20" alt="Third step"/> <a href="kotlin-tour-control-flow.md">Control flow</a><br/><img src="icon-4.svg" width="20" alt="Fourth step"/> <strong>Functions</strong><br/><img src="icon-5-todo.svg" width="20" alt="Fifth step"/> <a href="kotlin-tour-classes-part-1.md">Classes</a><br/><img src="icon-6-todo.svg" width="20" alt="Sixth step"/> <a href="kotlin-tour-null-safety.md">Null safety</a></p>
</microformat>

You can declare your own functions in Kotlin using the `fun` keyword. 

In Kotlin:
* function parameters are written within parentheses `()` using Pascal
notation - _name: type_.
* you must declare a type for each parameter and multiple parameters must be separated by commas.
* the return type is written after the function's parentheses `()`, separated by a colon `:`.
* the body of a function is written within curly braces {}.
* the `return` keyword is used to exit or return a data structure from a function.

In the below example:
* `x` and `y` are function parameters.
* `x` and `y` have type `Int`.
* the function's return type is `Int`.
* the function returns a sum of `x` and `y` when called.

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

## Lambda expressions

Kotlin allows you to write even more concise code for functions by using lambda expressions.

For example, the below function:

```kotlin
fun uppercaseString(string: String): String {
    return string.uppercase()
}

fun main() {
    val upperCase = uppercaseString("hello")  
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-lambda-before-kotlin"}

Can also be written as:
```kotlin
val upperCase = { string: String -> string.uppercase() }

fun main() {
    println(upperCase("hello"))
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-lambda-after-kotlin"}

You store a lambda expression in a variable by using the assignment operator (`=`). The lambda expression itself is
written within curly braces `{}`.

Within the lambda expression, you write:
* the parameters followed by an `->`.
* the function body after the `->`.

> If you declare a lambda without parameters, then there is no need to use `->`.
>
{type="note"}

### Function types

In the previous example, Kotlin's type inference inferred the type of `upperCase` from the parameter type. 
But there may be times when you need to explicitly specify the parameter and return type. 
Kotlin has **function types** for this purpose.

The syntax for a function type has:
* the parameters' types written within parentheses and separated by commas.
* the return type written after `->`.

For example: `(String) -> String`

This is what a lambda expression looks like if we define the function type for `upperCase`:

```kotlin
val upperCase: (String) -> String = { string -> string.uppercase() }

fun main() {
    println(upperCase("hello"))
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-lambda-function-type-kotlin"}

If your lambda has no parameters then the parentheses are left empty. For example: `() -> Unit`

> You must declare parameter and return types either in the lambda expression or as a function type. Otherwise, the
> compiler won't be able to know what type your variable is.
> 
> For example, the below won't work:
> 
> `val upperCase = { str -> str.uppercase() }`
>
{type="note"}

For more information on lambda expressions, see [Lambda expressions and anonymous functions](lambdas.md#lambda-expressions-and-anonymous-functions).

<!---

## Anonymous functions

Maybe?

## Higher-order functions

In Kotlin, functions can be used as a data type and stored in data structures such as variables. This means that we can
use functions as function parameters and return them from other functions.

A higher-order function is a function that takes another function as a parameter and/or returns a function.

For example:

```kotlin
fun calculate(x: Int, y: Int, operation: (Int, Int) -> Int): Int {
    return operation(x, y)
}
```
-->

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
