# More on Variables and Types
In the previous chapter I introduced you to variables and data types. In this chapter we will dive deeper into these topics. By the end of the chapter you will:
- Familiarize yourself with some more vocabulary and ways to use variables.
- Learn variable naming conventions.
- Know about constant variables.
- Understand Binary, Decimal and Hexidecimal counting systems.
- See the diifferent types in their constraints.

## Table of Contents

```{contents}
```

## Variables
We learned a bit about variables in the previous chapter. You may recall that if we want to store new data we will use the notation:

```C++
type name = newData;
```

However, there is a bit more to learn about variables before we can get started on writing more complex programming.


### Variable Declaration and Assignment Continued
So far we saw that variables can be declared in the following ways:

```C++
type name = newData; /* Declare and assign anew variable at the same type */

type name2; /* Declare a variable for future use*/
```

Variable declaration however is not limited to declaring only one variable. We can also declare mutliple variables on the same line in the following way:

```C++
type name1 = newData1, name2 = newData2, name 3 = newData3; /* Declare and assign mutliple variables at the same type */

type name4, name5, name6, name7; /* Declare multiple variables for future use*/
```

Another handy trick is the ability to assign the same value to multiple variables as such:

```C++
name4 = name2 = name7 = newData4;
```

Fruthermore, you can actually also save data from variable in to another:

```C++
name3 = name2;
```

All the examples above may seem a bit abstract. Try running the following example, and then change the code to use the new declaration and assignment methods we learned makiung sure the code functionality stays the same. If you want to challenge yourself, try and make the code inside the `main` function no more than 4 lines long.

```C++
#include <iostream> 
using namespace std;

int main() 
{ 
    double radius;
    double pi = 3.14; 
    double volume;
    double input;
    cout << "enter a radius of a sphere to get its volume" << endl;
    cin >> input;
    radius = input;
    volume = (4/3)*radius*radius*radius*pi;
    cout << volume;
} 
```
### Constants

I your still reading, there is one more variable concept that is very useful. In this stage of the coding journey it may not seem so, but in the future, it will ensure your code is secure when you write projects with thousands of lines. 

You may recall that I mentioned that variables can be changed throughout the program. However, some variables *should not* be changed. For example, pi is a constant that mostly hasn't changed in a few hundred years. In such cases `C++` has a keywoard that ensures a variable can never be changed. If you wish to create such a variable use the keyword `const`, for example:

```C++
const double PI = 3.14;
```
I encourage you, the reader, to see for yourself that adding the const keyword before a variable declaration does in fact make it read-only. You can do so by trying to play with the following program:

```C++
#include <iostream> 
using namespace std;

int main() 
{ 
    const double PI = 3.14;
    PI= 3;
    cout >> PI;
} 
```

### Naming Conventions

You probably noticed something odd when I declared the constant variable in the previous example. I opted to use uppercase letters for the variable name, but why?

In programming, the way you name your variables, functions, classes, and other entities is known as a naming convention. The convention adopted can vary between programming languages, projects, or even between different programmers on the same team. However, they all serve the same goal: to make the code more readable and understandable, not just for others, but also for your future self.

One such, widely accepted, convention is to use uppercase letters for the names of constant variables. This practice is a convention that comes from an older language called C, in which constants were often defined using a preprocessor directive #define, which by convention was always written in uppercase.

Another naming convention typically followed in C++ involves the use of "camel case" or "snake case".

In camel case, each new word starts with a capital letter, and there are no underscores between words. For example:

```C++
int myAwesomeVariable;
```
In snake case, all letters are lowercase, and underscores separate words. For example:

```C++
int my_awesome_variable;
```
These conventions are not mandated by the C++ language itself, but they have become standard practice in many codebases. It is important to note that while the language doesn't require you to follow these conventions, many C++ style guides and coding standards do. They make your code more readable and easier to maintain.

**Consistency Is Key**

The most important aspect of any naming convention is consistency. When working on a project, especially in a team, it is crucial to agree on a naming convention and stick to it throughout the project. If one part of the code uses snake case and another uses camel case, it can make the codebase harder to read and understand.

Naming conventions can also extend beyond just variable names. They can cover function names, class names, file names, and other entities in your code. In subsequent sections, we will cover these in detail and explore the commonly followed conventions in C++.

Remember, code is more often read than written, so clarity should always be a priority. Good naming conventions, well-applied, are a significant step in that direction.

### Naming Rules

Aside from naming conventions, there are also naming rules that **must** be followed. The general rules are:
- Names contain letters, digits and underscores. Nothing else.
- Names must begin with either a letter or an underscore (_).
- Names are case sensitive (pi and PI are different variables).
- Reserved words cannot be used as names.

## Types

In the previous chapter, we discussed some of the basic types in C++ such as `int`, `double`, `char`, `string`, and `bool`. In this chapter, we will delve deeper into these types, introduce some concepts related to how data is represented in computers, and understand the implications of these representations.

### Counting Systems: Binary, and Decimal
Before diving into specific types, it's important to understand the number systems that computers use to store and manipulate data: binary, decimal, and hexadecimal.

**Decimal**

The decimal system is the base-10 system we use in everyday life, comprises ten digits, from 0 to 9. This is the system we are most familiar with.

**Binary**

Computers fundamentally understand only two states—on and off, represented by 0 and 1. This is the binary system, or base-2. All computer data is ultimately represented as a series of these binary digits, or "bits". A group of 8 bits is commonly referred to as a byte.

We can convert from binary to decimal using the positional values. Each bit in a binary number represents 2 raised to an exponent, based on its position starting at the right most value.

For example, if we wanted to convert the binary number 11011 to decimal we can do the following:


|               |   Bit 4   | Bit 3 | Bit 2 | Bit 1 | Bit 0 |
|---------------|:---------:|:-----:|:-----:|:-----:|:-----:|
| Binary (B)    |     1     |   1   |   0   |   1   |   1   |
| Position (P)  |     4     |   3   |   2   |   1   |   0   |
| 2^P           |     16    |   8   |   4   |   2   |   1   |
| B*2^P         |     16    |   8   |   0   |   2   |   1   |
Then, to find the decimal equivalent of the binary number 11011, we sum up the values in the last row (B*2^P):

16 + 8 + 0 + 2 + 1 = 27

### Integers
 
 In C++, integers are stored in binary. Depending on the system and the compiler, an `int` in C++ is typically 32 bits, or 4 bytes. That means it can represent 2^32 unique values.

#### Signed vs Unsigned
By default, an `int` in `C++` is **signed**, meaning it can represent both positive and negative numbers. Half of the 2^32 unique values represent negative numbers, and the other half represent positive numbers.

If only positive values are needed, the **unsigned** keyword can be used. An `unsigned int` can represent twice as many positive numbers because all 2^32 values are used for positive numbers.

#### Max and Min Integers

in a 32-bit integer in C++, one of those 32 bits is used for the sign. This representation is known as two's complement, which is widely used for integer representation in computers.

Here is a breakdown:

- The most significant bit (MSB), or the leftmost bit in the bit string, is typically used as the sign bit.
- When the sign bit is 0, the number is positive or zero. The remaining 31 bits are used to represent the magnitude (size) of the number.
- When the sign bit is 1, the number is negative. In two's complement representation, the negative number is not just the positive representation with the sign bit flipped. Instead, to get a negative number, you take the positive number, flip all the bits (this is the one's complement), and then add 1.

This approach allows for simple and efficient arithmetic operations and also neatly solves the issue of representing zero and negatives. It does, however, mean that the range of integers that can be represented is not symmetric. A 32-bit integer in C++ can represent numbers in the range of -2,147,483,648 (-2^31) to 2,147,483,647 (2^31 - 1).

If this is a bit confusing, here are two examples:

**Example 1**

A 2-bit system provides a good simple example. In a 2-bit system, we can represent numbers from -2 to 1.

Let's take the number 1 as an example. In a 2-bit binary format, it would be:


```01```

To find the negative of this number, i.e., -1, we first find the one's complement (flip every bit):


``10``

Next, we add 1 to get the two's complement:

```
10
+1
--
11
```

So -1 is represented as 11 in a 2-bit system.

Here is the complete 2-bit two's complement table for reference:


```
00 = 0
01 = 1
10 = -2 (two's complement of 10 is 01+1=10, represents -2)
11 = -1 (two's complement of 01 is 10+1=11, represents -1)
```

**Example 2**

In binary, let's say we have the number 5, which is represented as follows in an 8-bit binary format (I'm using 8 bits for simplicity):

```0000 0101```

To get the negative of this number, i.e., -5, in the two's complement representation, we don't just flip the sign bit (the leftmost bit). We first get the one's complement of the number, i.e., we flip every bit:

``1111 1010``

This gives us the one's complement of 5. However, in two's complement representation, we don't stop here. We then add 1 to this result:


```
1111 1010
         +1
---------
1111 1011
```

So, -5 is represented as `1111 1011` in two's complement.

This method may seem counter-intuitive at first, but it has several advantages, including making the addition and subtraction of positive and negative numbers more straightforward for computers. For example, if you add 0000 0101 (5) and 1111 1011 (-5) together, you get 1 0000 0000 (256 in unsigned 8-bit, but due to overflow in signed 8-bit, the leftmost 1 is discarded), resulting in 0000 0000, which is zero, as expected.

#### Integer Overflow

Integer overflow happens when an integer value is computed that is outside the permissible range of the integer type. This can lead to unexpected behavior, as the integer value will wrap around.

**Wrap Around**

Consider an unsigned 32-bit integer. It can hold values from 0 to 4,294,967,295 (2^32 - 1). If we have a maximum unsigned 32-bit integer, 4,294,967,295, and add 1 to it, the result would logically be 4,294,967,296, which is outside the range of an unsigned 32-bit integer. This situation is what causes an overflow.

However, in the binary world, this operation doesn't result in an error or an exception, but rather it wraps around back to the start of the range. So, if we add 1 to an unsigned integer at its maximum limit, the result will be zero.

```C++
unsigned int maxUnsignedInt = 4294967295;
unsigned int overflowedUnsignedInt = maxUnsignedInt + 1; // this results in 0
```

A similar case happens for signed integers but includes the sign bit. For a signed 32-bit integer, the range is -2,147,483,648 to 2,147,483,647. If we add 1 to a variable at the maximum limit (2,147,483,647), we get -2,147,483,648, not an error or exception. This is because it wraps around to the start of the range.

```C++
signed int maxSignedInt = 2147483647;
signed int overflowedSignedInt = maxSignedInt + 1; // this results in -2147483648
```

**Implications**

Integer overflow can lead to both program logic errors and potential security vulnerabilities. These problems occur when programmers make incorrect assumptions about the possible values an integer can have.

Some programming languages have built-in mechanisms to deal with integer overflow, by throwing an exception when it occurs. But C++ is not one of them. The behavior of overflowing signed integers is technically undefined according to the C++ standard. This means that different compilers or systems can handle it differently, although in practice most use the wraparound behavior described above.

Therefore, as a developer, you should always be cautious when performing integer arithmetic. Ensure you consider the boundaries and accurately predict the behavior of the code in these edge cases. Check for potential overflows, especially when dealing with user input or any data that could potentially be crafted to exploit an overflow vulnerability.

#### Mathematical Operations with Integers

In C++, we can perform various mathematical operations with integers using operators. These include addition, subtraction, multiplication, division, and modulus operations.

Basic Operators
Here are the basic arithmetic operators in C++:

- +: addition
- -: subtraction
- *: multiplication
- /: division
- %: modulus (remainder of division)

```C++
int a = 10;
int b = 3;

int sum = a + b;    // 13
int diff = a - b;   // 7
int prod = a * b;   // 30
int div = a / b;    // 3, note that this performs integer division
int mod = a % b;    // 1, this is the remainder of 10 / 3
```

Note that the / operator performs integer division if both operands are integers. This means that the result is also an integer, and any fractional part is discarded. If you want a floating-point result, one or both of the operands must be a floating-point number.

Assignment Operators
In addition to the basic operators, C++ also provides combined assignment operators. These are shortcuts for performing an operation on a variable and then storing the result back in the same variable.

Here are the combined assignment operators:

- +=: addition assignment
- -=: subtraction assignment
- *=: multiplication assignment
- /=: division assignment
- %=: modulus assignment

Here are some examples of these operators in action:

```C++
int c = 10;
c += 5;  // equivalent to c = c + 5; now c is 15
c -= 3;  // equivalent to c = c - 3; now c is 12
c *= 2;  // equivalent to c = c * 2; now c is 24
c /= 6;  // equivalent to c = c / 6; now c is 4
c %= 3;  // equivalent to c = c % 3; now c is 1
```

These combined assignment operators are a very useful shortcut and can make your code more concise and easier to read.

In the next section, we'll discuss the double type in C++, which is used for representing floating-point numbers.

### Double

The `double` type in C++ is used to represent floating-point numbers, i.e., numbers with a fractional part. These could be very large numbers, very small numbers, or numbers between integers.

#### Floating-Point Representation
double in C++ typically occupies 64 bits, or 8 bytes, of memory. It is based on the IEEE 754 standard for floating-point arithmetic. This standard represents floating-point numbers in three parts:

- **Sign bit**: This bit indicates whether the number is positive or negative. 0 indicates a positive number and 1 indicates a negative number.

- **Exponent**: This is an 11-bit field that represents the exponent in the floating-point number. It is used to calculate the magnitude of the number.

- **Mantissa** (or fraction): This is a 52-bit field that represents the actual number (the significant digits).

The value of the floating-point number is calculated as: ``(-1)^sign_bit x (1 + mantissa) x (2^(exponent - 1023))``. The subtraction of 1023 from the exponent is to allow both small (less than 1) and large numbers to be represented.

This representation allows `double` to represent a very wide range of values, but it comes with a trade-off in precision.

**Precision Issues**
While double can represent a wide range of values, it can't always represent them precisely. This is because the mantissa part of the floating-point representation is a binary fraction, and some decimal fractions can't be precisely represented as binary fractions.

For example, the decimal number 0.1 can't be exactly represented in binary. As a result, operations involving such numbers may lead to tiny rounding errors. In most cases, these errors are insignificant and can be ignored, but in cases where high precision is required, they can lead to problems. This is sometimes referred to as floating-point error or round-off error.

#### Mathematical Operations with Doubles
Similar to `int`, the `double` type supports all basic arithmetic operations:

```C++
double d1 = 10.5;
double d2 = 3.2;

double sum = d1 + d2;    // 13.7
double diff = d1 - d2;   // 7.3
double prod = d1 * d2;   // 33.6
double div = d1 / d2;    // 3.28125
```
Note that there is no modulus operator for `double`.

The combined assignment operators (`+=`, `-=`, `*=`, `/=`) also work with double.

```C++
double d = 10.5;
d += 1.5;  // now d is 12.0
d -= 2.0;  // now d is 10.0
d *= 2.0;  // now d is 20.0
d /= 5.0;  // now d is 4.0
```

In the next section, we'll discuss the char type in C++, which is used for representing individual characters.

### Char

The `char` type in C++ is used to represent individual characters. This can include anything that can be typed on a keyboard, such as letters, numbers, punctuation marks, and control characters like \n (newline) or \t (tab).

**Character Representation**

A `char` in C++ occupies 8 bits, or 1 byte, of memory, which means it can represent 2^8 (or 256) unique values. These values are used to represent different characters according to a character set. The most commonly used character set is ASCII (American Standard Code for Information Interchange).

ASCII is a 7-bit character set that defines 128 unique values, which include:

- Control characters like newline, carriage return, and tab
- Printable characters:
    - Digits from 0 to 9 (ASCII values 48 to 57)
    - Uppercase letters from A to Z (ASCII values 65 to 90)
    - Lowercase letters from a to z (ASCII values 97 to 122)
    - Punctuation marks and special characters

Here is a small subset of the ASCII table:

|Character|	ASCII Value|
|--------|---------|
|0|	48|
|A|	65|
|a|	97|
|$|	36|
|@|	64|

The remaining values from 128 to 255 (when a `char` is considered as unsigned `char`) are used for extended character sets, which can represent additional characters such as accented letters or characters from non-English alphabets.


```C++
char c1 = 'A';   // Stores the character 'A'
char c2 = 65;    // Also stores the character 'A', because 65 is the ASCII value for 'A'
```


**Mathematical Operations with Chars**

Although char is mainly used to store characters, since it is essentially a small integer, you can perform arithmetic operations with char variables. For example, you can add or subtract integers from a char to get another char:


```C++
char c = 'A';
c = c + 1;   // Now c is 'B'
c += 1;      // Now c is 'C'
c -= 2;      // Now c is 'A' again
```

Note that you need to be careful when performing arithmetic operations with `char`. If you go beyond the range of the character set (either below 0 or above 127 for signed `char`, or above 255 for unsigned `char`), you'll get unexpected results due to overflow or underflow.

In the next section, we'll discuss the `string` type in C++, which is used for representing sequences of characters.

### String
The `string` type in C++ is used to represent sequences of characters. It is a part of the C++ Standard Library.

**String Representation**

A `string` in C++ is essentially a collection of `char` values stored sequentially in memory. The length of a `string` is not fixed and can change during the execution of the program.

In C++, you can `declare` a string and initialize it with a sequence of characters enclosed in double quotes:

```C++
string s = "Hello, World!";
```

**String Operations**
 
C++ provides a rich set of operations for manipulating strings:

- Concatenation: You can concatenate, or join, two strings using the + operator:
```C++
string s1 = "Hello, ";
string s2 = "World!";
string s3 = s1 + s2;  // "Hello, World!"
```
- Length: You can get the length (number of characters) of a string using the length() method:
```C++
string s = "Hello, World!";
int len = s.length();  // 13
```

- Substring: You can get a substring (part of the string) using the substr() method:
```C++
string s = "Hello, World!";
string sub = s.substr(7, 5);  // "World"
```
- Find: You can find the position of a substring within a string using the find() method:

```C++
string s = "Hello, World!";
int pos = s.find("World");  // 7
```
- Accessing Characters: You can access individual characters within a string with square brackets `[]` and the position of the letter you would like :
```C++
string s = "Hello, World!";
char c = s[0];  // 'H'
```
*Note that the first character is at position 0.*

These are just some of the basic operations provided by the C++ string class. There are many more methods for comparing strings, replacing parts of strings, and other string manipulations.

In the next section, we'll discuss the bool type in C++, which is used for representing boolean values.

### Boolean

The `bool` type in C++ is used to represent boolean values: `true` and `false`.

#### Boolean Representation

In C++, `bool` values are represented as `true` and `false`. Behind the scenes, `true` corresponds to an integer value of `1`, and `false` corresponds to `0`.

To declare a boolean variable and assign a value to it:

```C++
bool isReady = true;
```

#### Boolean Operations

C++ provides several operators to work with boolean values:

- Logical AND (&&): Returns `true` if both operands are `true`.
- Logical OR (||): Returns `true` if at least one operand is `true`.
- Logical NOT (!): Returns the inverse of the operand.

Here's an example of how these can be used:

```C++
bool isReady = true;
bool isSet = false;
bool result;

result = isReady && isSet;  // result will be false
result = isReady || isSet;  // result will be true
result = !isReady;  // result will be false
```

The bool type is also the type returned by relational operators (`<`, `<=`, `>`, `>=`, `==`, `!=`), which compare two values and return a bool result:


```C++
int x = 5;
int y = 10;
bool result = x < y;  // true
```

In this example, the `<` operator checks if `x` is less than `y`. Since 5 is indeed less than 10, the result is `true`.

#### Truth Tables

A truth table is a mathematical table used in logic to compute the result of a logical expression for each possible values of its variables. For the boolean operations AND, OR, and NOT, the truth tables are as follows:

##### AND (`&&`)

| Operand A | Operand B | Result |
|-----------|-----------|--------|
| true      | true      | true   |
| true      | false     | false  |
| false     | true      | false  |
| false     | false     | false  |

##### OR (`||`)

| Operand A | Operand B | Result |
|-----------|-----------|--------|
| true      | true      | true   |
| true      | false     | true   |
| false     | true      | true   |
| false     | false     | false  |

##### NOT (`!`)

| Operand | Result |
|---------|--------|
| true    | false  |
| false   | true   |

#### De Morgan's Laws

In boolean logic, De Morgan's Laws define how the three basic operations (AND, OR, NOT) can be interchanged without changing the truth of the statement. They are as follows:

1. The negation of a conjunction is the disjunction of the negations.
    - NOT (A AND B) is the same as (NOT A) OR (NOT B)

2. The negation of a disjunction is the conjunction of the negations.
    - NOT (A OR B) is the same as (NOT A) AND (NOT B)

De Morgan's Laws can be applied in programming to simplify complex logical expressions.

In the next section, we'll cover the important topic of type conversions in C++, which allow us to change the type of a value under certain circumstances.

### Type Conversions

In C++, we often need to convert values from one type to another. This is known as type conversion. There are two main types of conversion in C++: **implicit conversion** and **explicit conversion**.

#### Implicit Conversion

Implicit conversion, also known as automatic or "coercion", is performed by the compiler without the programmer explicitly requesting it. This happens when the context requires a value of a certain type, but a value of a different, compatible type is provided.

For instance, consider this example:

```C++
int i = 5;
double d = i;  
```
Here, an `int` value is being assigned to a `double` variable. Since the `double` type is capable of representing all `int` values with no loss of information, the compiler automatically converts `i` to `double` and assigns it to `d`.

#### Explicit Conversion

Explicit conversion, or type casting, occurs when the programmer explicitly requests a conversion using the cast operator. Here is an example:
```C++
double d = 5.7;
int i = (int)d;  
```
Here, the `double` value 5.7 is being cast to an `int`. Since `int` values can't have fractional parts, the decimal portion of the `double` value is truncated (not rounded), and only the whole number part is assigned to `i`.

It's important to note that explicit conversions can result in loss of information, such as in the example above where the fractional part of the double value was lost. As such, they should be used with care.

#### Conversion Functions

C++ also provides a few functions for converting values from one type to another. These include static_cast, dynamic_cast, const_cast, and reinterpret_cast. We will discuss these in a future chapter when we delve into more advanced C++ topics.

## Summary
- We learned about different types in C++, including `int`, `double`, `char`, `string`, and `bool`.
- We explored number systems used by computers including binary and decimal systems.
- We discussed the signed and unsigned variants of `int`, and how integer overflow occurs.
- We learned about the floating-point representation used by the `double` type and the concept of precision errors.
- We explored how `char` is used to represent characters and how it relates to ASCII encoding.
- We covered how `string` is used to manipulate sequences of characters.
- We examined how `bool` is used to represent boolean values `true` and `false`.
- We discussed implicit and explicit type conversions.

In the next chapter, we will delve deeper into the operations in C++ and learn about control structures like loops and conditional statements.

## Practice Questions - Booleans

1. Create a truth table for the expression A OR NOT B.
2. Using De Morgan's Laws, write the equivalent expression for NOT (A AND B).
3. Using De Morgan's Laws, write the equivalent expression for NOT (A OR (B AND C)).
4. Given the boolean variables `a = true`, `b = false`, and `c = true`, compute the values of the following expressions:
    - a OR b
    - NOT a AND c
    - NOT (a AND (b OR c))
    - a AND b OR NOT c
5. Rewrite the following expressions using De Morgan's Laws:
    - NOT (a OR b)
    - NOT (a AND b OR c)
    - NOT (a OR (b AND NOT c) OR (NOT a AND c))


## Practice Questions - General

1. How would you represent the binary number `1101` as a decimal?
2. What value would a `double` variable have if you assign it the result of the integer division of 10 by 3?
3. If `char c = 'z';`, what will the value of `c` be after the following statement: `c = c - 'a' + 'A';`?
4. Given the string "Learning C++ is fun!", write a piece of code that extracts the word "C++" from this string using the substr() function.
5. Given a `bool` variable `b` initialized with `false`, what will be the output of the following expression: `cout << !b;`?
6. Write a piece of code that demonstrates an explicit type conversion from `double` to `int`. What will be the output of this code if the `double` variable was initialized with `3.14`?

7. **Variable Swap:** Write a program that declares two integer variables, `a` and `b`, and swaps their values without using a third variable. Print the values of `a` and `b` before and after the swap.

8. **Case Converter:** Write a program that takes a lowercase letter as input and prints the uppercase version of the letter.


Remember to solve these exercises yourself and compare your solutions to the expected output. The key to learning programming is practice. You'll get comfortable with the syntax and logic as you write more code.


## Bibliography
```{bibliography}
:filter: docname in docnames
``` 