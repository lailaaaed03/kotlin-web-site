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

To access an item in a list, use the [indexed access operator](operator-overloading.md#indexed-access-operator) `[]`:

```kotlin
fun main() {
    //sampleStart
    val readOnlyNumbers = listOf(1, 2, 3)
    println("The first item in the list is: ${readOnlyNumbers[0]}")
    //The first element of the list is: 1
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="list-access-kotlin"}

To get the first or last item in a list, use [first()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/first.html)
and [last()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/last.html) functions respectively.

```kotlin
fun main() {
    //sampleStart
    val readOnlyNumbers = listOf(1, 2, 3)
    println("The first item in the list is: ${readOnlyNumbers.first()}")
    //The first item in the list is: 1
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="list-first-kotlin"}

To get the number of items in a list, use the [count()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/count.html)
function:

```kotlin
fun main() {
    //sampleStart
    val readOnlyNumbers = listOf(1, 2, 3)
    println("This list has ${readOnlyNumbers.count()} items")
    //This list has 3 items
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="list-count-kotlin"}

To add or remove items from a mutable list, use [add()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-list/add.html)
and [remove()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/remove.html) functions respectively.

```kotlin
fun main() {
    //sampleStart
    val numbers: MutableList<Int> = mutableListOf(1, 2, 3)
    numbers.add(4)    //Add 4 to the list
    println(numbers)  //[1, 2, 3, 4]
    
    numbers.remove(4) //Remove the first 4 from the list
    println(numbers)  //[1, 2, 3]
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="list-add-remove-kotlin"}

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

As sets are **unordered**, it's not possible to access an item at a particular index.

To get the number of items in a set, use the [count()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/count.html)
function:

```kotlin
fun main() {
    //sampleStart
    val readOnlyFruit = setOf("apple", "banana", "cherry", "cherry")
    println("This set has ${readOnlyFruit.count()} items")
    //This set has 3 items
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="set-count-kotlin"}

To add or remove items from a mutable set, use [add()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-list/add.html)
and [remove()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/remove.html) functions respectively.

```kotlin
fun main() {
    //sampleStart
    val fruit: MutableSet<String> = mutableSetOf("apple", "banana", "cherry", "cherry")
    fruit.add("dragonfruit")    //Add "dragonfruit" to the set
    println(fruit)  //[apple, banana, cherry, dragonfruit]
    
    fruit.remove("dragonfruit") //Remove "dragonfruit" from the set
    println(fruit)  //[apple, banana, cherry]
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="set-add-remove-kotlin"}

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

To access a value in a map, use the [indexed access operator](operator-overloading.md#indexed-access-operator) `[]` with
its key:

```kotlin
fun main() {
    //sampleStart
    val readOnlyAccountBalances = mapOf(1 to 100, 2 to 100, 3 to 100)
    println("The first value in the map is: ${readOnlyAccountBalances[1]}")
    //The first value in the map is: 100
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="map-access-kotlin"}

To get the number of items in a map, use the [count()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/count.html)
function:

```kotlin
fun main() {
    //sampleStart
    val readOnlyAccountBalances = mapOf(1 to 100, 2 to 100, 3 to 100)
    println("This map has ${readOnlyAccountBalances.count()} key-value pairs")
    //This map has 3 key-value pairs
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="map-count-kotlin"}

To add or remove items from a mutable map, use [put()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-mutable-map/put.html)
and [remove()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/remove.html) functions respectively.

```kotlin
fun main() {
    //sampleStart
    val accountBalances: MutableMap<Int, Int> = mutableMapOf(1 to 100, 2 to 100, 3 to 100)
    accountBalances.put(4, 100)  //Add key 4 with value 100 to the list
    println(accountBalances)     //{1=100, 2=100, 3=100, 4=100}
    
    accountBalances.remove(4)    //Remove the key 4 from the list
    println(accountBalances)     //{1=100, 2=100, 3=100}
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="map-put-remove-kotlin"}

To check if a specific key is already included in a map, use the [containsKey()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/contains-key.html)
function:

```kotlin
fun main() {
    //sampleStart
    val readOnlyAccountBalances = mapOf(1 to 100, 2 to 100, 3 to 100)
    println(readOnlyAccountBalances.containsKey(2))
    //true
    //sampleEnd
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="map-contains-keys-kotlin"}

To obtain a collection of the keys or values of a map, use the [`keys`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-map/keys.html)
and [`values`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-map/values.html) properties respectively:

```kotlin
fun main() {
    //sampleStart
    val readOnlyAccountBalances = mapOf(1 to 100, 2 to 100, 3 to 100)
    println(readOnlyAccountBalances.keys)
    //[1, 2, 3]
    println(readOnlyAccountBalances.values)
    //[100, 100, 100]
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="map-keys-values-kotlin"}

For more information on what you can do with collections, see [Collections](collections-overview.md).

Now that you know about basic types and how to manage collections, let's explore the logic that you can
use in your programs.

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
