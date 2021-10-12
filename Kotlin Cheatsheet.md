## Table of content:

1) [The Hello world program](#hello-world)
2) [Variables](#variables)
3) [Comments](#comments)
4) [Standard input and output](#standard-input-output)
5) [Standard type conversion](#standard-type-conversion)
6) [Null safety](#null-safety)
7) [Strings](#strings)
8) [Operators](#operators)
9) [Conditionals](#conditionals)
10) [Loops](#loops)
11) [Functions](#functions)
12) [Arrays](#arrays)
13) [Classes](#classes)
14) [Inner class](#inner-class)
15) [Inheritance](#inheritance)
16) [Abstract class](#abstract-class)
17) [Interface](#interface)
18) [Type check and type cast](#typecheck-typecast)
19) [Data class](#data-class)
20) [Enum class](#enum-class)
21) [Sealed class](#sealed-class)
22) [Singleton](#singleton)
23) [Anonymous class](#anonymous-class)
24) [Companion objects](#companion-objects)
25) [Extension functions](#extension-function)
26) [Lambda expression](#lambda-expression)
27) [Higher order functions](#higher-order-functions)
28) [Scope functions](#scope-functions)
29) [Generics](#generics)

### The Hello world program:<a id="hello-world" />

````Kotlin
fun main() {
    println("Hello World!")
}
````

The ``main`` function is the entry point of the Kotlin application

### Comments:<a id="comments" />

- Inline comment:

````Kotlin
// This is an inline comment
````

- Multi-line comment:

````Kotlin
/* This is a 
    multi-line comment */
````

- JavaDoc comment:

````Kotlin
/** This is JavaDoc comment */
````

Javadoc is a documentation generator created by Sun Microsystems for the Java language for generating API documentation
in HTML format from Java source code.

### Variables: <a id="variables" />

```Kotlin
var variableName: Type // Declaration
variableName = "value"  // Initialization

var variableName = "Name"  // Implicit type inference

var variableName: Type = value  // Explicit type inference

// Explicit type inference examples
val name: String = "Lomas"
val level: Int = 21
```

- The type name always starts with an uppercase letter.
- If we need to declare a variable and initialize it later, type inference won't work at all. We will need to do type
  declaration.

1) **Read only variables:**  
   Assign once, can't reassign

```Kotlin
val variableName = "Name"  // Implicit type inference

// OR

val variableName: Type = value  // Explicit type inference
```

2) **Mutable variables:**  
   Assign and reassign when needed

```Kotlin
var variableName = "value"

// OR

var variableName: Type = value
```

There is one restriction for mutable variables (the ones declared with the keyword var), though. When reassigning their
values, you can only use new values of the same type as the initial one.

```Kotlin
var name = "Lomas"  // Here type is String

name = 25 // Compile time error because we are assigning Integer type to String type

var name = "Lomas"  // Here type is String

name =
    "Someone special"  /* Compiles successfully because we are assigning the value of same type as the previous one i.e., String */
```

### Standard input and output:<a id="standard-input-output" />

- **Standard input:**

```Kotlin
val input = readLine()!!  // reads a whole line as string

val (a, b) = readLine()!!.split(" ")  // reads multiple values in one line

// Java scanner
import java.util.Scanner

val scanner = Scanner(System.`in`)

val input = scanner.next()  // reads only one word as string
val inputLine = scanner.nextLine()  // reads a whole line as string
val inputNum = scanner.nextInt()  // reads a number
```

- **Standard output:**

```Kotlin
print("Hello! I'm Lomas!")  // cursor stay in the same line after printing

println("Hello! I'm Lomas!")  // moves the cursor at the start of a new line after printing
```

### Standard type conversion:<a id="standard-type-conversion" />

- **Conversion between numeric types:**

All number types support conversion to other types:

``toByte(): Byte``

``toShort(): Short``

``toInt(): Int``

``toLong(): Long``

``toFloat(): Float``

``toDouble(): Double``

``toChar(): Char``

Smaller types are not implicitly converted to bigger types. They require explicit conversion.

- **String conversion:**

``toString()`` function can convert any type of value to string representation.

### Null safety:<a id="null-safety" />

- **Variables with Nullable and non-nullable types:**

In Kotlin, the type system distinguishes between references that can hold ```null```
(nullable references) and those that cannot (non-null reference).

```Kotlin
// Variable with nullable type
var variableName: String? = null

// Variable with non-nullable type
val variableName: String = null  // Compile time error
```

- **Safe calls:**

To access the nullable variable you can either use ```if-else``` check for ```null```
or use a safe call operator ```?.```:

```Kotlin
var a: String? = null
println(a?.length)
```

This returns ```a.length``` if ```a``` is not null, and ```null``` otherwise.

- **Not-Null assertion operator (```!!```):**

```!!``` converts any value to a non-null type and throw an exception if the value is
```null```.

```Kotlin
var name: String? = "Lomas"
println(myVariable!!.length)  // 5

name = null
println(myVariable!!.length)  // NullPointerException
```

### Strings:<a id="strings" />

```Kotlin
val myString = "This is a string in Kotlin"
```

- **Length of a string:**

```Kotlin
println(myString.length) // 26
```

- **Concatenating strings:**

```Kotlin
val firstName = "Lomas"
val lastName = "Singh"

println(str1 + " " + str2) // Lomas Singh 
```

- **Appending values to string:**

The + also works for appending values of different types to string. The value is automatically converted to a ``String``
and then concatenated.

```Kotlin
val str = "abc" + 10 + true
println(str) // abc10true 
```

Here expression must start with a ``String``.

```Kotlin
val str1 = 10 + "abc"  // Error because first operand is a number
```

- **Escape sequences:**

There are some special characters starting with an escaping backslash `` \ ``.

The following escape sequences are supported:  
```\n``` new line character  
```\t``` tab character  
```\r``` carriage return character  
```\b``` backspace and carriage return  
```\'``` single quote mark  
```\"``` double quote mark  
```\\``` backslash character  
```\$``` dollar character

- **Raw String:**

A raw string is delimited by a triple quote (```"""```), contains no escaping and can contain newlines and any other
characters:

```Kotlin
val text = """
   Hi there!
        I am Lomas...
"""
println(text)

/* Result:
_____________________
   Hi there!
        I am Lomas...
_____________________
*/
```

To remove leading whitespace from raw strings, use the ```trimMargin()``` function:

```Kotlin
val text = """
    |Empty your mind, be formless, shapeless, like water.
    |If you put water into a cup, it becomes the cup.
    |You put water into a bottle and it becomes the bottle.
    |You put it in a teapot, it becomes the teapot.
    |Now, water can flow or it can crash.
    |Be water, my friend.
    |(Bruce Lee)
    """.trimMargin()
```

By default, ```|``` is used as margin prefix, but you can choose another character and pass it as a parameter,
like ```trimMargin(">")```.

- **String template:**  
  It is used when you need to put the value of variables in a text. Kotlin allows you to refer to local variables in
  string literals by putting ```$``` sign before the name of variable.

```Kotlin
val name = "Lomas"
val temperature = 30
println("My name is $name.\nThe current temperature in my city is $temperature degree Celsius")

/* Result:
________________________________________________________
My name is Lomas.
The current temperature in my city is 30 degree Celsius.
________________________________________________________
*/
```

- **String template for expressions:**  
  To put the result of an arbitrary expression in a string, include the entire expression in curly braces ```{...}```
  after the ```$``` sign.

```Kotlin
val name = "Lomas"
println("My name is ${name.uppercase()}.")  // My name is LOMAS.
```

### Operators:<a id="operators" />

- **Basic operators:**

```*``` - multiplication  
```/``` - division  
```+``` - addition  
```%``` - modulus (Remainder)  
```-``` - subtraction  
```=``` - assignment

- **Relational operators:**

```>```  - greater than  
```<```  - less than  
```==```  - equal  
```!=```  - not equal  
```>=```  - greater than or equal  
```<=```  - less than or equal
```===``` - referential equality (Two references pointing to the same object)  
```!==``` - negated referential equality (Two references not pointing to the same object)

- **Augmented assignment operator:**

```+=``` assignment after addition: ```A += B equals A = A + B```  
```-=``` assignment after subtraction: ```A -= B equals A = A - B```  
```*=``` assignment after multiplication: ```A *= B equals A = A * B```  
```/=``` assignment after division: ```A /= B equals A = A / B```  
```%=``` assignment of the remainder after division: ```A %= B equals A = A % B```

- **Increment and decrement operators:**

```--```  used when decreasing by one  
```++```  used when increasing by one

```Kotlin
// Prefix form: first increases or decreases then assigns
var a = 2
val l = ++a
println(a)  // 3
println(l)  // 3

// Postfix form: first assigns then increases or decreases
var l = 5
val a = l--
println(l)  // 4
println(a)  // 5
```

- **Logical operators:**

```!``` - NOT  
```&&``` - AND  
```||``` - OR  
```xor``` - XOR (exclusive OR)

- **Bitwise operators:**

Each of these operators goes through all bits of both operands (numbers) one by one (i.e., bitwise)
and produces and new number as a result.

```and``` - bitwise **AND**. The result digit is ```1``` if both the operand digits are ```1```, otherwise it is ```0```
.

```or``` - bitwise **OR**. The result digit is ```1``` if at least one operand digit is ```1```, otherwise it is ```0```
.

```xor``` - bitwise **XOR**. The result digit is ```1``` if exactly one operand is ```1```, otherwise it is ```0```.

```inv()``` - bitwise **NOT**, inversion, complement. A unary operator that inverses bits in the binary format of the
number, turning every ```0``` into ```1``` and vice-versa. It also changes the sign bit of the value.  
Compilers work with 2's complement of numbers so, for any positive integer ```n```, the inversion will be ```-(n + 1)```
. Therefore, inversion of negative integer ```-n``` will be ```n - 1```.

The listed operators can be applied to both integer and boolean operands. If both operands are integers, then bitwise
operations will be performed. If both operands are booleans, the corresponding logical operations are performed (
except ~).

- **Bit-shift operators:**

These operators can be used to shift the bits of an integer number from one position to another.

```shl``` - Shifts the bit representation to the left by a certain number of specified bits, and zero bits are shifted
into the lower-order positions.

```shr``` - Shifts the bit representation to the right by a certain number of specified bits and fills the empty place
with the value of sign bit.

```ushr``` - An unsigned bit-shift operator that shifts the bit pattern to the right by a certain number of specified
bits.  
The shifted values are filled up with zeros therefore the result of ```ushr``` is always positive.

When we use signed bit-shift operator, we perform multiplication or division of the left operand by 2 in the power of
the right operand.

```Kotlin
var num = 25

num = num shl 1  // 25 * 2^1 = 50
num = num shl 3  // 50 * 2^3 = 400
num = num shr 2  // 400 / 2^2 = 100 
```

- **Precedence of operators:**

Operations with higher precedence are performed before those with lower precedence.  
The following list is in decreasing order of priority:

1) Parentheses (```(expression)```);
2) Postfix increment/decrement (```expr++```, ```expr--```);
3) Unary plus/minus, prefix increment/decrement (```-expr```, ```++expr```, ```--expr```);
4) Multiplication, division, and modulus (```*```, ```/```, ```%```);
5) Addition and subtraction (```+```, ```-```);
6) Assignment operation (```=```, ```+=```, ```-=```, ```*=```, ```/=```, ```%=```);
7) bitwise and bit-shift operators (```and```, ```or```, ```xor```, ```shr```, ```shl```, ```ushr```).

- **Precedence of logical operators:**

The following list is in decreasing order of priority:

1) ```!``` - NOT
2) ```xor``` - XOR
3) ```&&``` - AND
4) ```||``` - OR

### Conditionals:<a id="conditionals" />

- **The if case:**

```Kotlin
if (condition1) {
    // do something
} else if (condition2) {
    // do something
} else if (condition3) {
    // do something
} else {
    // do something else
}
```

- **if as an expression:**

In Kotlin, ```if``` is an expression, not a statement. It returns a value. Due to this there is no ternary operator in
Kotlin.

```Kotlin
val variableName = if (condition1) value1 else value2
```

Branches of ```if``` can be blocks and last expression of the block is its value.

```Kotlin
val variableName = if (condition1) {
    // do something
    value1
} else {
    // do something else
    value2
}
```

> **Note:** *While using ```if``` as an expression, ```else``` branch is mandatory.*

- **Elvis operator:**

For null check instead of using ```if-else``` expression you can use ```?:``` operator:

```Kotlin
val loas = aslo?.lenght ?: 25

/* 
If the expression to the left of ?: is not null then, elvis operator returns it,
otherwise it returns the expression to the right.
*/
```

- **when statement:**

It is similar to switch statement in C-like languages but more powerful. It matches its arguments against all branches
sequentially until some branch condition is satisfied.

```Kotlin
when (argument) {
    value1 -> // do something 
    value2 -> // do something
    else -> // do something else
}

```

Arbitrary expressions can be used as branch conditions:

```Kotlin
when (argument) {
    expression1 -> // do something
    expression2 -> // do something
    else -> // do something else
}
```

Different use cases of ```when```:

```Kotlin
val x = someValue
when (x) {
    value1 -> statement  // Equality check
    in startPoint..endPoint -> statement  // Range check
    value2, value3, value4 -> statement   // Multiple values
    is Type -> statement  // Type check
    else -> statement
}
```

If no argument is supplied, the branch condition are simply boolean expressions, and a branch is executed when its
condition is true:

```Kotlin
when {
    condition1 -> // do something
    condition2 -> // do something
    else -> // do something else
}
```

> *Use ```when``` instead of ```if-else-if``` if there is more than two condition to improve the readability.*

- **when as an expression:**

If ```when``` is used as an expression, the value of first matching branch becomes the value of the overall expression.

```Kotlin
val variableName = when (argument) {
    condition1 -> value1
    condition2 -> value2
    else -> value3
}
```

Result of an expression can be immediately passed to a function without declaring an additional variable.

```Kotlin
println(
    when (argument) {
        condition1 -> value1
        condition2 -> value2
        else -> value3
    }
)
```

> *This notation is used when the result is not used somewhere else to keep the code short.*

### Loops:<a id="loops" />

- **Repeat loop:**

Here ```n``` is a positive integer that determines the number of times to repeat the statement.

```Kotlin
// Syntax
repeat(n) {
    // statement
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
// example
repeat(2) {
    println("Hi! I'm Lomas...")
}
/* Result
________________
Hi! I'm Lomas...
Hi! I'm Lomas...
----------------
*/
```

> *If ```n``` is zero or a negative number, Kotlin will ignore the loop. If ```n```
is one, the statement will be executed only once.*

- **While loop:**

```Kotlin
while (condition) {
    // statement
}
```

- **Do-while loop:**

```Kotlin
do {
    // statement
} while (condition)
```

> *You can set a variable in the loop body and then use it in the condition.*

- **For loop:**

```for``` loops iterates through anything that provides an iterator. It can be used to iterate through ranges, arrays,
map and other collection of elements.

```Kotlin
// Syntax
for (item in collection) {
    // body of the loop
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
// Example:
for (i in 1..5) {
    println("Repetition $i: Hi! I'm Lomas")
}

/* Result
___________________________
Repetition 1: Hi! I'm Lomas
Repetition 2: Hi! I'm Lomas
Repetition 3: Hi! I'm Lomas
Repetition 4: Hi! I'm Lomas
Repetition 5: Hi! I'm Lomas
___________________________
*/
```

- **Different ways to iterate through a range using ```for``` loop:**

Iterating through a closed range:

```Kotlin
for (i in 1..5) {
    print("$i ")
}

/* Result
_________
1 2 3 4 5
_________
*/
```

Iterating through half-open range:

```Kotlin
for (i in 1 until 5) {
    print("$i ")
}

/* Result
_________
1 2 3 4
_________
*/
```

Iterate from endpoint to initial point:

```Kotlin
for (i in 1 downTo 6) {
    print("$i ")
}

/* Result
___________
6 5 4 3 2 1
___________
*/
```

Iterate up every other one from initial point to endpoint (inclusive):

```Kotlin
for (i in 1..6 step 2) {
    print("$i ")
}

/* Result
_________
1 3 4 6
_________
*/
```

Iterate through an array or a list with an index:

```Kotlin
val numArray = arrayOf(2, 7, 8, 4, 2)
for (i in numArray.indices) {
    print("${numArray[i]} ")
}

/* Result
_________
2 7 8 4 2
_________
 */
```

Iterate over a map:

```Kotlin
val numbersMap = mapOf("key1" to 1, "key2" to 2, "key3" to 3, "key4" to 4)
for ((key, value) in map) {
    println("[$key]: $value")
}

/* Result
_________
[key1]: 1
[key2]: 2
[key3]: 3
[key4]: 4
_________
*/
```

- **Single expression ```for``` loop:**

If there is only one expression then curly braces can be omitted in the ```for``` loop.

```Kotlin
for (i in 1..6) print("$i ")

/* Result
_________
1 2 3 4 5
_________
 */
```

- **Break, continue and return:**

Kotlin supports traditional ```break```, ```return``` and ```continue```.

```return``` by default returns from the nearest enclosing function or anonymous function.

```break``` terminates the nearest enclosing loop.

```continue``` proceeds to the next step of the nearest enclosing loop.

- **Break and continue labels:**

In Kotlin label is just an identifier with the ```@``` sign at the end. To label an expression, just add a label in
front it. Any word can be used apart from reserved words in Kotlin.  
We can qualify ```break``` and ```continue``` with a label.

A ```break``` qualified with a label jumps to the execution point right after the loop marked with that label.  
A ```continue``` qualified with a label proceeds to the next iteration of that loop marked with that label.

```Kotlin
// Qualifying break with label
loop@ for (i in 1..6) {
    for (j in 1..6) {
        println("i = $i, j = $j")
        if (j == 3) break@loop
    }
}

/* Result
____________
i = 1, j = 1
i = 1, j = 2
i = 1, j = 3
____________
*/

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

// Qualifying continue with label
loop@ for (i in 1..3) {
    for (j in 1..3) {
        for (k in 1..3) {
            if (k == 2) continue@loop
            println("i = $i, j = $j, k = $k")
        }
    }
}

/* Result
___________________
i = 1, j = 1, k = 1
i = 2, j = 1, k = 1
i = 3, j = 1, k = 1
___________________
*/
```

### Functions:<a id="functions" />

- **Declaration:**

```Kotlin
// Syntax
fun functionName(parameter1: Type1, parameter2, Type2, ...): ReturnType {
    // body
    return result
}
```

There are two ways to declare a function that returns nothing:  
a) Omit the return type part:

```Kotlin
fun functionName(param: Type) {
    // body
}
```

b) Specify the return type as ``Unit``:

```Kotlin
fun functionName(param: Type): Unit {
    // body
}
```

- **Variable number of arguments (vararg):**

You can mark a parameter of a function (usually the last one) with the ```vararg```
modifier to pass a variable number of arguments to the function:

```Kotlin
fun functionName(vararg parameter: Type) {
    for (i in parameter) print("$i ")
}

functionName(2, 7, 8, 4, 2)

/* Result
_________
2 7 8 4 2
_________
*/
```

- Single expression function:

If a function returns a single expression, you can write it without curly braces:

```Kotlin
fun functionName(parameter: Type): ReturnType = return statement

// Specifying the return type is optional, as it can be inferred automatically:
fun functionName(parameter: Type) = return statement
```

### Arrays:<a id="arrays" />

- **Creating an array with specified elements:**

```Kotlin
// a generic array
val myArray = arrayOf(1, 2, 'a', 's', "Lomas")

// Explicit type declaration of items in generic array
val myArray = arrayOf<String>("Loas", "Aslo", "abc", "bla-bla-bla")

// empty array
val myArray = emptyArray<String>()  // Specification of type of element to be filled later is mandatory

// Byte array
val myArray = byteArrayOf(2, 7, 8, 4, 2)

// Short array
val myArray = shortArrayOf(2, 7, 8, 4, 2)

// Int array
val myArray = intArrayOf(2, 7, 8, 4, 2)

// Long array
val myArray = longArrayOf(2L, 7L, 8L, 4L, 2L)

// Float array
val myArray = floatArrayOf(2.0f, 7.0f, 8.0f, 4.0f, 2.0f)

// Double array
val myArray = doubleArrayOf(2.0, 7.0, 8.0, 4.0, 2.0)

// Boolean array
val myArray = booleanArrayOf(true, false, true, true, true)

// Char array
val myArray = charArrayOf('4', '5', '8', 'a', 's', 't')
```

When you initialize an array (or anything else) with a sequence of arguments, you can add a trailing comma. It can be
useful if you want to add or change some values:

```Kotlin
val myArray = arrayOf(2, 7, 8, 4, 2,)
```

- **Creating an array of specified size:**

These arrays are going to have a predefined size. They are filled by the default values of the corresponding types
(```0``` for numeric types). You cannot change the size of an array, but you can modify the elements.

```Kotlin
// Byte array
val myArray = ByteArray(25)

// Short array
val myArray = ShortArray(25)

// Int Array
val myArray = IntArray(25)

// Double Array
val myArray = DoubleArray(25)

// Char Array
val myArray = CharArray(25)
```

You can also specify the default values of these arrays:

```Kotlin
/* input
2
7
8
4
2
 */

val myArray = IntArray(5) { readLine()!!.toInt() }  // on each line single numbers
print(myArray.joinToString())

/* Result
_____________
2, 7, 8, 4, 2
_____________
 */
```

You can:  
access strings in the array through their indexes;  
use ```joinToString()``` to create a single string from the array and output it;  
use ```contentEquals()``` to compare two arrays.

### Classes:<a id="classes" />

- **Classes:**

```Kotlin
// Declaration
class MyClass {
    var property1: Type = value1
    var property2: Type = value2
    var property3: Type = value3
}
```

When class has empty body, curly braces can be omitted.

```Kotlin
class MyEmptyClass
```

- **Object creation:**

```Kotlin
val variableName: MyClass = MyClass()

// OR SIMPLY

val variableName = MyClass()
```

- **Accessing properties:**

```Kotlin
println(variableName.property1)
println(variableName.property2)
```

- **Constructors:**

1) Default constructor:

Every class needs to have a constructor and if it isn't explicitly defined then compiler automatically generates a
default constructor, which only creates an object and doesn't have any logic inside.

```Kotlin
val variableName = MyClass()
```

2) Primary constructor:

Primary constructor does not contain any code, it just initializes an instance of a class and its properties. Each class
can have only one primary constructor.

```Kotlin
class MyClass constructor(val property1: Type1, var property2: Type2) {
    // body
}
```

If the primary constructor does not have any annotation or visibility modifiers, the ```constructor``` keyword can be
omitted:

```Kotlin
class MyClass(var property1: Type1, val property2: Type2) {
    // body
}
```

***Init block***

The primary constructor cannot contain any code. Initialization code can be placed in initializer blocks prefixed with
the ```init``` keyword. The keyword ```init``` signifies the block of code that serves as an extension of the primary
constructor.

```Kotlin
class MyClass(val property1: Type1, var property2: Type2) {
    init {
        println("First property is $property1, second property is $property2")
    }

    init {
        println("This is the second initializer block")
    }
}
```

You can have multiple initializer blocks in the class body. During the initialization of an instance, the initializer
blocks are executed in the same order as they appear in the class body, interleaved with the property initializers.

*If the constructor has annotations or visibility modifiers, the ```constructor``` keyword is required and the modifiers
go before it:*

```Kotlin
class MyClass @annotation public constructor(property: Type) {
    // body
}
```

3) Secondary constructors:

Secondary constructors are created using ```constructor``` keyword. They allow initialization of variables as well as to
provide some logic to the class.

```Kotlin
class MyClass {
    constructor(val property1: Type1, var property2: Type2) {
        // body
    }
}
```

> *The secondary constructor first calls the primary constructor, the property initialization and ```init``` block executes then finally secondary constructor is executed.*

### Inner class:<a id="inner-class" />

```Kotlin
class MyClass {
    inner class MyInnerClass {
        // body
    }
}
```

A regular nested class cannot access the member of outer class but a nested class prefixed with ```inner``` keyword
can.

To access the inner class, you need to instantiate the outer class first.

```Kotlin
val inner = MyClass().MyInnerClass()
```

### Inheritance:<a id="inheritance" />

By default, Kotlin classes are final and can't be inherited. To make a class inheritable, prefix it with the ```open```
keyword.

```Kotlin
open class MyBaseClass(parameter: Type) {
    // body
}

class MyDerivedClass(parameter1: Type) : MyBaseClass(parameter1) {
    // body
}
```

If a derived class doesn't have a primary constructor then each secondary constructor has to initialize the base type
using the ```super``` keyword.

```Kotlin
class MyDerivedClass : MyBaseClass {
    constructor(parameter1: Type) : super(parameter1)
}
```

### Abstract class:<a id="abstract-class" />

Abstract classes are always open. You don't need to explicitly use ```open``` keyword to inherit from them.

```Kotlin
abstract class MyAbsClass {
    // body
}
```

### Interface:<a id="interface" />

Interface in kotlin can contain declaration of abstract methods as well as method implementations but it cannot contain
any state i.e., they may have a property but it needs to be abstract or has to provide accessor implementations.

```Kotlin
interface MyInterface {
    // body
}
```

### Type check and type cast:<a id="typecheck-typecast" />

### Package specification:<a id="package-specification" />

````Kotlin
package com.lomas.kotlin
````

Package is a group of similar types of classes, interfaces and sub-packages