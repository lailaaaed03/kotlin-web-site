[//]: # (title: Functions)

<microformat>
    <p>This is the fifth part of the <strong>Beginner</strong> Kotlin tour:</p>
    <p><img src="icon-1-done.svg" width="20" alt="First step" /> <a href="kotlin-tour-hello-world.md">Hello world</a><br />
        <img src="icon-2-done.svg" width="20" alt="Second step" /> <a href="kotlin-tour-types.md">Basic types</a><br />
        <img src="icon-3-done.svg" width="20" alt="Third step" /> <a href="kotlin-tour-collections.md">Collections</a><br />
        <img src="icon-4-done.svg" width="20" alt="Fourth step" /> <a href="kotlin-tour-control-flow.md">Control flow</a><br />
        <img src="icon-5.svg" width="20" alt="Fifth step" /> <strong>Functions</strong><br />
        <img src="icon-6-todo.svg" width="20" alt="Sixth step" /> <a href="kotlin-tour-classes-part-1.md">Classes</a><br />
        <img src="icon-7-todo.svg" width="20" alt="Final step" /> <a href="kotlin-tour-null-safety.md">Null safety</a></p>
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
```

Can also be written as a lambda expression:

```kotlin
{ string: String -> string.uppercase() }
```

Lambda expressions are written within curly braces `{}`.

Within the lambda expression, you write:
* the parameters followed by an `->`.
* the function body after the `->`.

In the above example:
* `string` is a function parameter.
* `string` has type `String`.
* the function returns the result of the [`uppercase()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.text/uppercase.html)
function called on `string`.

> If you declare a lambda without parameters, then there is no need to use `->`. For example:
> ```kotlin
> { println("Log message") }
> ```
>
{type="note"}

Lambda expressions can be used in a number of ways. You can:
* assign a lambda to a variable that you can then invoke later
* pass a lambda expression as a parameter to another function
* return a lambda expression from a function
* invoke a lambda expression on its own

The following sections demonstrate each of these use cases.

### Capture a variable

Assigning a lambda expression to a variable is also referred to as capturing a variable. You assign a lambda expression 
to a variable by using the assignment operator (`=`):

```kotlin
val upperCase = { string: String -> string.uppercase() }

fun main() {
    println(upperCase("hello"))
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-lambda-variable-kotlin"}

### Pass to another function

A great example of when it is useful to pass a lambda expression to a function, is using the [filter()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/filter.html)
function on collections. If a lambda expression is the only function parameter, you can drop the function parentheses `()`.

For example:

```kotlin
fun main() {
    //sampleStart
    val numbers = listOf(1, -2, 3, -4, 5, -6)
    val positives = numbers.filter { x -> x > 0 }
    val negatives = numbers.filter { x -> x < 0 }
    println(positives)
    //[1, 3, 5]
    println(negatives)
    //[-2, -4, -6]
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-lambda-filter-kotlin"}

The `filter()` function accepts a lambda expression as a predicate:
* `{ x -> x > 0 }` takes each element of the list and returns only those that are positive
* `{ x -> x < 0 }` takes each element of the list and returns only those that are negative

Another good example, is using the [map()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/map.html) 
function to transform items in a collection:

```kotlin
fun main() {
    //sampleStart
    val numbers = listOf(1, -2, 3, -4, 5, -6)
    val doubled = numbers.map { x -> x * 2 }
    val tripled = numbers.map { x -> x * 3 }
    println(doubled)
    //[2, -4, 6, -8, 10, -12]
    println(tripled)
    //[3, -6, 9, -12, 15, -18]
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-lambda-map-kotlin"}

The `map()` function accepts a lambda expression as a predicate:
* `{ x -> x * 2 }` takes each element of the list and returns that element multiplied by 2
* `{ x -> x * 3 }` takes each element of the list and returns that element multiplied by 3

### Function types

Before demonstrating how you can return a lambda expression from a function, you first need to understand **function
types**.

You have already learned about basic types but functions themselves also have a type. Kotlin's powerful type inference 
can infer a function's type most of the time from the parameter type. But there may be times when you need to explicitly
specify the function type so that the compiler knows what is and isn't allowed for that function.

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

### Return from a function

Lambda expressions can be returned from a function. So that the compiler understands what type the lambda
expression returned is, you must declare a function type.

In the below example, the `toSeconds()` function has function type `(Int) -> Int` because it always returns a lambda
expression that takes a parameter of type `Int` and returns an `Int` value.

The example uses a when expression to determine which lambda expression is returned when `toSeconds()` is invoked.

```kotlin
fun toSeconds(time: String): (Int) -> Int = when (time) {
    "hour" -> { value -> value * 60 * 60 }
    "minute" -> { value -> value * 60 }
    "second" -> { value -> value }
    else -> { value -> value }
}

fun main() {
    val timesInMinutes = listOf(2, 10, 15, 1)
    val min2sec = toSeconds("minute")
    val totalTimeInSeconds = timesInMinutes.map(min2sec).sum()
    println("Total time is $totalTimeInSeconds secs")
}
```

### Invoke separately

Lambda expressions can be invoked on their own by placing parentheses `()` after the curly braces `{}` and including
any parameters within the parentheses. For example:

```kotlin
fun main() {
    //sampleStart
    println({ string: String -> string.uppercase() }("hello"))
    //HELLO
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-lambda-standalone-kotlin"}

### Trailing lambdas

If a lambda expression is passed as the last parameter of a function, then the expression can be written outside the
function parentheses `()`. This syntax is called a trailing lambda.

For example, the [`fold()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.sequences/fold.html) function accepts an 
initial value and an operation:

```kotlin
fun main() {
    //sampleStart
    //The initial value is zero. The operation sums the initial value with every item in the list cumulatively.
    println(listOf(1, 2, 3).fold(0, { x, item -> x + item })) //6

    //Alternatively, in the form of a trailing lambda
    println(listOf(1, 2, 3).fold(0) { x, item -> x + item })  //6
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-trailing-lambda-kotlin"}

For more information on lambda expressions, see [Lambda expressions and anonymous functions](lambdas.md#lambda-expressions-and-anonymous-functions).

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
