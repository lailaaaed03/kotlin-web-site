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
* Within the class body defined by curly brackets `{}`.
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

## Inheritance
By default, you can't inherit a class from another class. To allow class inheritance for a class, use the `open`
keyword in its declaration.

To declare a class that inherits from a parent class:
1. Add a colon `:` after the class name.
2. Add the name of the parent class after the colon `:`.
3. Add any parameters needed for the parent class constructor within parentheses `()`.

For example:

```kotlin
open class Dog          //Class Dog can be inherited from
class Yorkshire : Dog() //Class Yorkshire inherits from class Dog

open class Tiger(val origin: String)   //Class Tiger can be inherited from
class SiberianTiger : Tiger("Siberia") //Class SiberianTiger inherits from class Tiger with constructor parameter "Siberia" 

fun main() {
    val yorkshire = Yorkshire()         //Creates instance of class Yorkshire
    val siberianTiger = SiberianTiger() //Creates instance of class SiberianTiger
}
```

> Note that when creating an instance of `SiberianTiger`, no parameters are needed in the constructor. The `origin`
> is automatically set to `"Siberia"`.
>
{type="note"}

### Override member functions

You can also inherit and override member functions. To allow inheritance from a function, use the `open` keyword in its 
declaration.

To override the behavior of an inherited member function, inside your child class, use the `override` keyword before the
function declaration, and then define the new behavior.

For example:

```kotlin
open class Dog {
    open fun sayHello() {        //sayHello() function can be inherited
        println("wow wow!")
    }
}

class Yorkshire : Dog() {
    override fun sayHello() {   //Override sayHello() function
        println("wif wif!")     //New behavior
    }
}

fun main() {
    val yorkshire = Yorkshire()
    yorkshire.sayHello()         //Prints "wif wif!"
}
```

### Override properties

You can override and inherit properties in exactly the same way as with member functions:

```kotlin
open class Dog {
    open var bark = "wow wow!"     //bark variable can be inherited
    }

class Yorkshire : Dog() {
    override var bark = "wif wif!" //Override value of bark
    }

fun main() {
    val yorkshire = Yorkshire()
    println(yorkshire.bark)        //Prints "wif wif!"
}
```

For more information, see [Inheritance](inheritance.md).

## Extensions
Sometimes it's not possible to inherit from a class. For example, if you are using a function from a third-party
library. Instead, you can write new functions to extend the class. You can also do the same for properties.

### Extension functions


### Extension properties

For more information, see [Extensions](extensions.md).

## Any type

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
