[//]: # (title: Control flow)

<microformat>
    <p>This is the third part of the <strong>Beginner</strong> Kotlin tour.</p>
    <p><img src="icon-1-done.svg" width="20" alt="First step"/> <a href="kotlin-tour-hello-world.md">Hello world</a><br/><img src="icon-2-done.svg" width="20" alt="Second step"/> <a href="kotlin-tour-types.md">Basic types</a><br/><img src="icon-3.svg" width="20" alt="Third step"/> <strong>Control flow</strong><br/><img src="icon-4-todo.svg" width="20" alt="Fourth step"/> <a href="kotlin-tour-functions.md">Functions</a><br/><img src="icon-5-todo.svg" width="20" alt="Fifth step"/> <a href="kotlin-tour-classes-part-1.md">Classes</a><br/><img src="icon-6-todo.svg" width="20" alt="Sixth step"/> <a href="kotlin-tour-null-safety.md">Null safety</a></p>
</microformat>

Like other programming languages, Kotlin has tools for checking conditional expressions and creating loops.

## Conditional expressions

Kotlin provides `if` and `when` for checking conditional expressions. If you have to choose between the two, we recommend
using `when` as it leads to more robust and safer programs.

### If

To use `if`, add the conditional expression within parentheses and the action to take if the result is true within curly braces `{}`:

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
`if` as an expression, there are no curly braces `{}`:

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

Use `when` when you have a conditional expression with multiple branches.
`when` can be used either as a statement or as an expression.

Below is an example of using `when` as a statement. Again, place the conditional expression within parentheses and the actions to take
within curly braces `{}`. Use `->` in each branch to separate each condition from each action.

```kotlin
fun main() {    
    val obj = "Hello"    
    
    when (obj) {                                     
        1 -> println("One")            //Checks whether obj equals to 1
        "Hello" -> println("Greeting") //Checks whether obj equals to "Hello"
        else -> println("Unknown")     //Default statement
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
        1 -> "One"            //If obj equals 1, sets result to "one"
        "Hello" -> 1          //If obj equals "Hello", sets result to 1
        else -> 42            //Sets result to 42 if no previous condition is satisfied
    }
    println(result)
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-when-expression-kotlin"}

If when is used as an expression, the else branch is mandatory, unless the compiler can detect that all possible cases 
are covered with branch conditions.

## Ranges

The most common way to create a range in Kotlin is to use the `..` operator. For example, `1..4` is equivalent to `1, 2, 3, 4`.

To declare a range that doesn't include the end value, use `until`. For example, `1 until 4` is equivalent to `1, 2, 3`.

To declare a range in reverse order, use `downTo.` For example, `4 downTo 1` is equivalent to `4, 3, 2, 1`.

To declare a range that increments in a step that isn't 1, use `step` and your desired increment value.
For example, `1..5 step 2` is equivalent to `1, 3, 5`.

You can also do the same with `Char` ranges:
* `'a'..'d'` is equivalent to `'a', 'b', 'c', 'd'`
* `'z' downTo 's' step 2` is equivalent to `'z', 'x', 'v', 't'`

Ranges are useful when creating loops, as you'll see in the next section.

## Loops

The two most common loop structures in programming are `for` and `while`. `for` is useful to iterate over a range of values and perform an action.
`while` is useful to continue an action until a particular condition is satisfied.

### For

Using our new knowledge of ranges, we can create a `for` loop that iterates over numbers 1 to 5 and prints the number each time.

Place the iterator and range within parentheses `()` with keyword `in`. Add the action you want to complete within curly braces `{}`.

```kotlin
fun main() {
    for (number in 1..5) { // number is the iterator and 1..5 is the range
        println(number)
    }
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-for-loop-kotlin"}

### While

`while` can be used in two ways:
1. To execute a code block while a conditional expression is true. (`while`)
2. To execute the code block first and then check the conditional expression. (`do-while`)

In the first use case (`while`):
* Declare the conditional expression for your while loop to continue within parentheses `()`. 
* Add the action you want to complete within curly braces `{}`.

> In the below examples, we use the [increment operator](operator-overloading.md#increments-and-decrements) `++` to
> increment the value of our `cakesEaten` variable.
>
{type="note"}

```kotlin
fun main() {
    cakesEaten = 0
    while (cakesEaten < 5) {
        println("Eat a cake")
        cakesEaten++
    }
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-while-loop-kotlin"}

In the second use case (`do-while`):
* Define the action you want to complete within curly braces `{}` with the keyword `do`.
* Declare the conditional expression for your while loop to continue within parentheses `()`.

```kotlin
fun main() {
    cakesEaten = 0
    cakesBaked = 0
    while (cakesEaten < 5) {
        println("Eat a cake")
        cakesEaten++
    }
    do {
        println("Bake a cake")
        cakesBaked++
    } while (cakesBaked < cakesEaten)
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-while-do-loop-kotlin"}

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
[Learn about functions](kotlin-tour-functions.md)
