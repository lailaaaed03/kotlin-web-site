[//]: # (title: Learn about control flow)

Like other programming languages, Kotlin has tools for checking conditions and creating loops.

## Conditions

Kotlin provides `if` and `when` for checking conditions.

### If

To use `if`, add the condition within parentheses and the action to take if the result is true within curly brackets `{}`:

```kotlin
fun main() { 
//sampleStart
    val d: Int
    val check =  true

    if (check) {
        d = 1   
    } else {
        d = 2   
    }

    println(d)
//sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-if-kotlin"}

There is no ternary operator `condition ? then : else` in Kotlin. Instead, `if` can be used as an expression. When using
`if` as an expression, there are no curly brackets `{}`:

```kotlin
fun main() { 
//sampleStart
    val a = 1
    val b = 2

    println(if (a > b) a else b) // Returns a value: 2
//sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-if-expression-kotlin"}

### When

When to use when???

Instead of the widely used switch statement, Kotlin provides the more flexible and clear `when` construction. 
It can be used either as a statement or as an expression.

Below is an example of using `when` as a statement. Again the condition is within parentheses and the actions to take
are within curly brackets `{}`. `->` is used in each branch to separate each condition from each action.

```kotlin
fun main() {    
    val obj = "Hello"    
    
    when (obj) {                                     
        1 -> println("One")                          // Checks whether obj equals to 1
        "Hello" -> println("Greeting")               // Checks whether obj equals to "Hello"
        else -> println("Unknown")                   // Default statement
    }   
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-when-statement-kotlin"}

Note that all branch conditions are checked sequentially until one of them is satisfied. So, only the first suitable 
branch is executed.

Below is an example of using `when` as an expression.

```kotlin
fun main() {    
    val obj = "Hello"    
    
    val result = when (obj) {                                     
        1 -> "One"                // If obj equals 1, sets result to "one"
        "Hello" -> 1              // If obj equals "Hello", sets result to 1
        else -> 42                // Sets result to 42 if no previous condition is satisfied
    }
    println(result)
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-when-expression-kotlin"}

## Loops

### For

### While

## Ranges


For more information and examples of conditional expressions and loops, see [Conditions and loops](control-flow.md).

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
[Learn about functions](kotlin-tour-types.md)
