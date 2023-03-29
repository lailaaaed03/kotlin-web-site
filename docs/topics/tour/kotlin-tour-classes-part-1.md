[//]: # (title: Classes I)

<microformat>
    <p>This is the fifth part of the <strong>Beginner</strong> Kotlin tour.</p>
    <p><img src="icon-1-done.svg" width="20" alt="First step"/> <a href="kotlin-tour-hello-world.md">Hello world</a><br/><img src="icon-2-done.svg" width="20" alt="Second step"/> <a href="kotlin-tour-types.md">Basic types</a><br/><img src="icon-3-done.svg" width="20" alt="Third step"/> <a href="kotlin-tour-control-flow.md">Control flow</a><br/><img src="icon-4-done.svg" width="20" alt="Fourth step"/> <a href="kotlin-tour-functions.md">Functions</a><br/><img src="icon-5.svg" width="20" alt="Fifth step"/> <strong>Classes</strong><br/><img src="icon-6-todo.svg" width="20" alt="Sixth step"/> <a href="kotlin-tour-null-safety.md">Null safety</a></p>
</microformat>

Kotlin supports object-oriented programming with classes and objects. Objects are useful for storing data in your program.
Classes allow you to declare a set of characteristics for an object. When you create objects from a class, you can save
time and effort because you don't have to declare these characteristics every time.

To declare a class, use the `class` keyword. 

```kotlin
class Customer
```

## Properties

Characteristics of a class's object can be declared in properties. You can declare mutable (`var`) or read-only (`val`)
properties for a class:
* Within parentheses `()` after the class name.
```kotlin
class Contact(val id: Int, var email: String)
```
* Within the class body defined by curly braces `{}`.
```kotlin
class Contact(val id: Int, var email: String) {
    val category: String
}
```

> * The content contained within parentheses `()` is called the class header.
> * You can use a [trailing comma](coding-conventions.md#trailing-commas) when declaring class properties.
>
{type="tip"}

Just like with function parameters, class properties can have default values:
```kotlin
class Contact(val id: Int, var email: String = "example@gmail.com") {
    val category: String = "work"
}
```

## Create instance

To create an object from a class, you create a class **instance** using a **constructor**.

By default, Kotlin automatically creates a constructor with the parameters declared in the class header.

For example:
```kotlin
class Contact(val id: Int, var email: String)

fun main() {
    val contact = Contact(1, "mary@gmail.com")
}
```

In the above example:
* `Contact` is a class
* `contact` is an instance of the `Contact` class
* `id` and `email` are properties
* `id` and `email` are used with the default constructor to create `contact`

Kotlin classes can have many constructors, including ones that you define yourself. To learn more about how to declare 
multiple constructors, see [Constructors](classes.md#constructors).

## Access properties

To access a property of an instance, write the name of the property after the instance name appended with a period `.`:

```kotlin
class Contact(val id: Int, var email: String)

fun main() {
    val contact = Contact(1, "mary@gmail.com")
    println(contact.email)           //Prints the value of the property: email
    contact.email = "jane@gmail.com" //Updates the value of the property: email
    println(contact.email)           //Prints the new value of the property: email
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-access-property-kotlin"}

## Member functions
In addition to declaring properties as part of an object's characteristics, you can also define an object's behavior 
with member functions.

In Kotlin, member functions must be declared within the class body. To call a member function on an instance, write the 
function name after the instance name appended with a period `.`. For example:

```kotlin
class Contact(val id: Int, var email: String) {
    fun printId() {
        println(id)
    }
}

fun main() {
    val contact = Contact(1, "mary@gmail.com")
    contact.printId()           //Calls member function printId() that prints 1
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-member-function-kotlin"}

## Data classes


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
[Learn about null safety](kotlin-tour-null-safety.md)
