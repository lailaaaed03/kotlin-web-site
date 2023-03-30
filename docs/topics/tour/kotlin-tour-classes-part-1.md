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

Characteristics of a class's object can be declared in properties. You can declare properties for a class:
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

We recommend that you declare properties as read-only (`val`) unless they need to be changed after an instance of the class
is created.

You can declare properties without `val` or `var` within parentheses but these properties are not accessible after an 
instance has been created.

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

> To concatenate the value of a property as part of a string, you can use template expressions (`$`).
> For example:
> ```kotlin
> println("Their email address is: ${contact.email}")
> ```
>
{type="tip"}

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

<!-- Rewrite intro to explain why data classes are useful -->

Data classes are a special type of class declared with keyword `data`, that have predefined member functions that
automatically come with the class:

| Function           | Description                                                                                                     |
|--------------------|-----------------------------------------------------------------------------------------------------------------|
| `copy()`           | To create a class instance by copying another, potentially with some different properties.                      |
| `componentN()`     | To access properties of the class in their order of declaration. E.g. `component1` accesses the first property. |
| `equals()` or `==` | To compare instances of a class.                                                                                |
| `hashCode()`       | To expose the hash code of an instance, for comparison.                                                         |
| `toString()`       | To print a readable string of the class instance and its properties.                                            |

See below for an example of these functions in action:

```kotlin
data class User(val name: String, val id: Int)

fun main() {
    val user = User("Alex", 1)
    val secondUser = User("Alex", 1)
    val thirdUser = User("Max", 2)
    
    //toString()
    println(user)              //Automatically uses toString() function so that output is easy to read
    //User(name=Alex, id=1)

    //equals()
    println("user == secondUser: ${user == secondUser}") //Compares user to second user
    //user == secondUser: true
    println("user == thirdUser: ${user == thirdUser}")   //Compares user to third user
    //user == thirdUser: false

    //hashCode()
    println(user.hashCode())
    //63347075
    println(secondUser.hashCode())
    //63347075
    println(thirdUser.hashCode())
    //2390846
    
    //copy()
    println(user.copy())       //Creates an exact copy of user
    //User(name=Alex, id=1)
    println(user.copy("Max"))  //Creates a copy of user with name: "Max"
    //User(name=Max, id=1)
    println(user.copy(id = 3)) //Creates a copy of user with id: 3
    //User(name=Alex, id=3)
    
    //componentN()
    println(user.component1()) //Prints first property of user
    //Alex
    println(user.component2()) //Prints second property of user
    //1

}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-data-classes-kotlin"}

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
