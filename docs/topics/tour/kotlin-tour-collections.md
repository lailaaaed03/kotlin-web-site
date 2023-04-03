[//]: # (title: Collections)

<microformat>
    <p>This is the third part of the <strong>Beginner</strong> Kotlin tour:</p>
    <p><img src="icon-1-done.svg" width="20" alt="First step" /> <a href="kotlin-tour-hello-world.md">Hello world</a><br />
        <img src="icon-2-done.svg" width="20" alt="Second step" /> <a href="kotlin-tour-types.md">Basic types</a><br />
        <img src="icon-3.svg" width="20" alt="Third step" /> <strong>Collections</strong><br />
        <img src="icon-4-todo.svg" width="20" alt="Fourth step" /> <a href="kotlin-tour-control-flow.md">Control flow</a><br />
        <img src="icon-5-todo.svg" width="20" alt="Fifth step" /> <a href="kotlin-tour-functions.md">Functions</a><br />
        <img src="icon-6-todo.svg" width="20" alt="Sixth step" /> <a href="kotlin-tour-classes-part-1.md">Classes</a><br />
        <img src="icon-7-todo.svg" width="20" alt="Final step" /> <a href="kotlin-tour-null-safety.md">Null safety</a></p>
</microformat>

Kotlin has collections for grouping items:
* Lists are ordered collections of items
* Sets are unique collections of items
* Maps are sets of key-value pairs where keys are unique and map to only one value

Each collection type can be mutable or read only.

## List

To create a read-only list (`List`), use the `listOf()` function.

To create a mutable list (`MutableList`), use the `mutableListOf()` function.

When creating lists, Kotlin can sometimes infer the type of items stored. To declare the type explicitly, add the type
within angled brackets after the list declaration.

```kotlin
fun main() {
    //sampleStart
    val readOnlyNumbers = listOf(1, 2, 3)                  //Read only list
    val numbers: MutableList<Int> = mutableListOf(1, 2, 3) //Mutable list with explicit type declaration
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="lists-declaration-kotlin"}

> To prevent unwanted modifications, obtain read-only views of mutable lists by casting them to `List`.
> ```kotlin
>     val numbers: MutableList<Int> = mutableListOf(1, 2, 3)
>     val numbersLocked: List<Int> = numbers
> ```
> 
{type="tip"}

## Set

To create a read-only set (`Set`), use the `setOf()` function.

To create a mutable set (`MutableSet`), use the `mutableSetOf()` function.

When creating sets, Kotlin can sometimes infer the type of items stored. To declare the type explicitly, add the type
within angled brackets after the set declaration.

```kotlin
fun main() {
    //sampleStart
    val readOnlyFruit = setOf("apple", "banana", "cherry", "cherry")                    //Read only set
    val fruit: MutableSet<String> = mutableSetOf("apple", "banana", "cherry", "cherry") //Mutable set with explicit type declaration
    println(readOnlyFruit)
    //[apple, banana, cherry]
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="sets-declaration-kotlin"}

You can see in the example above that because sets only contain unique elements, the duplicate `"cherry"` item is dropped.

> To prevent unwanted modifications, obtain read-only views of mutable sets by casting them to `Set`.
> ```kotlin
>     val fruit: MutableSet<String> = mutableSetOf("apple", "banana", "cherry", "cherry")
>     val fruitLocked: MutableSet<String> = fruit
> ```
>
{type="tip"}

## Map

To create a read-only map (`Map`), use the `mapOf()` function.

To create a mutable map (`MutableMap`), use the `mutableMapOf()` function.

When creating maps, Kotlin can sometimes infer the type of items stored. To declare the type explicitly, add the types
of the keys and values within angled brackets after the map declaration.

The easiest way to create maps is to use the [`to`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/to.html) function:

```kotlin
fun main() {
    //sampleStart
    val readOnlyAccountBalances = mapOf(1 to 100, 2 to 100, 3 to 100)                      //Read only map
    val accountBalances: MutableMap<Int, Int> = mutableMapOf(1 to 100, 2 to 100, 3 to 100) //Mutable map with explicit type declaration
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="maps-declaration-kotlin"}

> To prevent unwanted modifications, obtain read-only views of mutable maps by casting them to `Map`.
> ```kotlin
>     val accountBalances: MutableMap<Int, Int> = mutableMapOf(1 to 100, 2 to 100, 3 to 100)
>     val accountBalancesLocked: MutableMap<Int, Int> = accountBalances
> ```
>
{type="tip"}

## Practice

### Exercise 1 {initial-collapse-state="collapsed"}
Complete the code below to make the function print `"OK"` to standard output. Test your code in [Playground](https://play.kotlinlang.org).
```kotlin
    fun main() {
        TODO()
    }
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" validate="false"}

|---|---|
```kotlin
    fun main() {
        println("OK")
    }
```
{initial-collapse-state="collapsed" collapsed-title="Example solution"}

## Next
[Learn about control flow](kotlin-tour-control-flow.md)
