[//]: # (title: Null safety)

<microformat>
    <p>This is the final part of the <strong>Beginner</strong> Kotlin tour:</p>
    <p><img src="icon-1-done.svg" width="20" alt="First step" /> <a href="kotlin-tour-hello-world.md">Hello world</a><br />
        <img src="icon-2-done.svg" width="20" alt="Second step" /> <a href="kotlin-tour-types.md">Basic types</a><br />
        <img src="icon-3-done.svg" width="20" alt="Third step" /> <a href="kotlin-tour-collections.md">Collections</a><br />
        <img src="icon-4-done.svg" width="20" alt="Fourth step" /> <a href="kotlin-tour-control-flow.md">Control flow</a><br />
        <img src="icon-5-done.svg" width="20" alt="Fifth step" /> <a href="kotlin-tour-functions.md">Functions</a><br />
        <img src="icon-6-done.svg" width="20" alt="Sixth step" /> <a href="kotlin-tour-classes-part-1.md">Classes</a><br />
        <img src="icon-7.svg" width="20" alt="Final step" /> <strong>Null safety</strong><br /></p>
</microformat>

In Kotlin, it's possible to have a `null` value. To help prevent issues with null values in your programs, Kotlin has 
null safety in place. Null safety detects potential problems with null values at compile time, rather than at run time.

Null safety is a combination of features that allow you to:
* explicitly declare when null values are allowed in your program
* check for null values
* use safe calls to properties or functions that may contain null values
* declare actions to take if null values are detected

Each section below covers in more detail how you can use each of these features.

## Nullable types

Kotlin supports nullable types which allows the possibility for the declared type to have null values. By default, a type
is not allowed to accept null values. Nullable types are declared by explicitly adding `?` after the type declaration.

For example:

```kotlin
fun main() {
    var neverNull: String = "This can't be null"          //neverNull has String type

    neverNull = null                                      //Throws a compiler error

    var nullable: String? = "You can keep a null here"    //nullable has nullable String type

    nullable = null                                       //This is OK  

    var inferredNonNull = "The compiler assumes non-null" //By default, null values aren't accepted

    inferredNonNull = null                                //Throws a compiler error

    fun strLength(notNull: String): Int {                 //notNull doesn't accept null values
        return notNull.length
    }

    println(strLength(neverNull))                         //18
    println(strLength(nullable))                          //Throws a compiler error
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-nullable-type-kotlin"}

> 'length' is a property of the [String](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/) class that 
> contains the number of characters within a string.
>
{type="tip"}

## Check for null values

You can check for the presence of null values within conditional expressions. In the below example, the `describeString()`
 function has an if statement that checks whether `maybeString` is **not** `null` and if its `length` is greater than zero.

```kotlin
fun describeString(maybeString: String?): String {
    if (maybeString != null && maybeString.length > 0) {
        return "String of length ${maybeString.length}"
    } else {
        return "Empty or null string"
    }
}

fun main() {
    var nullString: String? = null
    println(describeString(nullString))
    //Empty or null string
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-check-nulls-kotlin"}

## Use safe calls

To safely access a property that might contain a null value, use the safe call operator `?.`. The safe call operator
returns `null` if the property is `null`. This is useful if you want to avoid the presence of null values triggering
errors in your code.

In the below example, the `lengthString()` function uses a safe call to return either the length of the string or `null`:

```kotlin
fun lengthString(maybeString: String?): Int? = maybeString?.length

fun main() {
 var nullString: String? = null
 println(lengthString(nullString))
 //null
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-safe-call-property-kotlin"}

> Safe calls can be chained so that if any property contains a null value, then `null` is returned without an error being
> thrown. For example:
> ```kotlin
>   person.company?.address?.country
> ```
>
{type="tip"}

The safe call operator can also be used to safely call an extension or member function. In this case, a null check is 
performed before the function is called. If the check detects a null value, then the call is skipped and `null` is returned.

In the following example, `nullString` is `null` so the invocation of [`uppercase()`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.text/uppercase.html)
is skipped and `null` is returned.

```kotlin
fun main() {
 var nullString: String? = null
 println(nullString?.uppercase())
 //null
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-safe-call-function-kotlin"}

## Use Elvis operator

You can provide a default value to return if a null value is detected by using the **Elvis operator** `?:`.

Write on the left-hand side of the Elvis operator what should be checked for a null value.
Write on the right-hand side of the Elvis operator what should be returned if a null value is detected.

In the following example, `nullString` is `null` so the safe call to access the `length` property returns a `null` value.
As a result, the Elvis operator returns `0`.

```kotlin
fun main() {
    var nullString: String? = null
    println(name?.length ?: 0)
    //0
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-elvis-operator-kotlin"}

For more information about null safety in Kotlin, see [Null safety](null-safety.md).

This was the last chapter of our tour. It's time to wrap up and consider your next steps!

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
[Wrap up](kotlin-tour-beginner-wrap-up.md)
