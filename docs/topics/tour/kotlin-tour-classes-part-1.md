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
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-inheritance-kotlin"}

> Note that when creating an instance of `SiberianTiger`, no parameters are needed in the constructor. The `origin`
> is automatically set to `"Siberia"`.
>
{type="note"}

It's only possible to inherit from one class at a time. Kotlin doesn't support multiple inheritance, where you inherit
from two classes at the same time.

```kotlin
open class Sheep                //Class Sheep can be inherited from
open class Dog                  //Class Dog can be inherited from
open class Yorkshire : Dog()    //Class Yorkshire inherits from class Dog
open class Yorkie : Yorkshire() //Class Yorkie inherits from class Yorkshire

// class Sheepdog : Sheep() : Dog() //You can't create a class that inherits from both class Sheep and class Dog
```

By default, if no parent class is declared, your class inherits from the [`Any`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-any/) class.
The `Any` class is at the root of the Kotlin class hierarchy.

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
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-override-member-function-kotlin"}

> Note that if you override a member function, the function that you override it with is automatically inheritable.
>
{type="note"}

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
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-override-property-kotlin"}

For more information, see [Inheritance](inheritance.md).

## Extensions

Sometimes it's not possible to inherit from a class. For example, if you are using a function from a third-party
library. Instead, you can write new functions to extend the class.

### Extension functions

The syntax for declaring extension functions is very similar to declaring a normal function. They key difference is that
you need to write the name of the class that you want to extend followed by a period `.` before your function name.

> The class to be extended is called the **receiver type**. Every extension function must have a receiver type.
>
{type="tip"}

```kotlin
class Contact(val id: Int, var email: String) {
    fun printId() {
        println(id)
    }
}

fun Contact.getInfo() = "$id $email" //Extension function for class Contact

fun main() {
    val contact = Contact(1, "mary@gmail.com")
    contact.printId()           //Calls member function printId() that prints 1
    print(client.getInfo())     //Calls print() on extension function getInfo()
}
```
{kotlin-runnable="true" kotlin-min-compiler-version="1.3" id="tour-extension-function-kotlin"}

> Note, it's not possible to override an extension function. If the class has a member function that has the same
> signature as an extension function, the member function always takes precedence.
>
{type="note"}

For more information, see [Extensions](extensions.md).

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
