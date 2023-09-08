# Your First Program
In this chapter we will go over the the program we wrote at the end of the previous chapter, and use some momentum to learn some basic programming terms and concepts.
By the end of this chapter you should be able to:
- Understand the building blocks of a basic C++ program.
- Identify types of Errors in your program.
- Know the basic ways to save values in C++.

## Table of Contents:
```{contents}
```

## Hello World

In the previous chapter we wrote our first C++ program:

```c++
#include <iostream> //line 1

int main() //line 2
{ //line 3
    std::cout << "Hello World" << std::endl; //line 4
} //line 5
```

Let's make some sense of the different components of this code before we move on to new topics.

### Comments

As you may have noticed, the code block above is a bit different than from the on in the previous chapter. The difference lies in the comments I added so I can refer to the different lines of code throughout this chapter. 

Throughout your coding journey you will write a lot of code. You will read a lot of code. And others will read your code. It is therefore important to keep our code clean and legible. Comments are one way to help us do so. 

There are two ways to write comments in C++. For single line comments we use two back slashes:
```C++ 
// This is a single line comment
```

And for Multi line comments we use a sequence of the form slash, asterisk, text, asterik, slash as follows:


```C++ 
/* 
This is a multi line comment
*/
```

### Header Files

The `#include` statement in C++ is a preprocessor directive. It instructs the computer what external files or libraries are needed to run this program. These files and libraries are called **header files**  in C++ 

In line 1 we include the `iostream` library, which is needed for the Input/Output (I/O) communication with your console. In this code, we need it so the computer can understand what the standard ouput stream ``cout``, and what the endline operation ``endl`` means. In the future, you will probably also use the standard input stream ``cin``.

We wont go to deep into header files and libraries until later on in this textbook. In the next few chapters, we will use pre built header files and introduce tham as needed.

### Input and Output

The program we wrote writes to our console. If it wasn't clear from the previous section, we did this with the help of the keyword `cout`. If we want to read from the console, we will use the keyword `cin`. 

There do exist other ways to to read and write in a program, but for the next few lessons all you'll need is `cout` and `cin`.
### Standard Namespace

``std`` is an abbreviation for "standard". When we use ``std::`` we are telling the computer we want to use the standard namespace. Namespace is an advanced topic we may go over in later chapters. In short, the computer will know we are referring to the ``cout`` defined in the ``iostrem`` header when we use ``std::``.

Using this abbreviation might get tiresome in long programs. We can fix this by letting the computer know we always want to use the standard namespace in the following manner:


```c++
#include <iostream> 
using namespace std;

int main() 
{ 
    cout << "Hello World" << endl; 
} 
```

### Steam Operators

``<<`` is a stream insertion operator. You'll always want to pair this with the ``cout`` command. The input operator for ``cin`` will look similar, but backwards: ``>>``.

### Main Function

``int main()`` is a function the computer utilizes to know where to start executing your program. We'll learn all about functions very soon. 

For now, all you need to remember (but not necessarly understand) is that functions will have 5 main components:
- A *return type*, in this case int.
- The return type will be followed by the *function name*, in this case main.
- The function name is followed by *circle brackets*, which can be used to define necessary inputs required for the funciton to work. In this case we dont need any inputs so the brackets are empty.
- *Curly brackets* to associate code with a function. 
- *Code* that goes inside the brackets.

### Semicolons

The last part of the code is the semicolon. The semicolon *must* be used after any executble line of code that is not a function or a #include statement. Why? Errors 🤮.

## Errors

Errors are an integral part of building a program. You are very unlikely to write perfect code, even with years of experience. Errors act as a natural feedback loop that will allow for writing a working program. We can genarally categorize errors in to three categroies:
- Syntax Errors
- Runtime Erros
- Logic Errors

Lets build upon the code we wrote to understand the three types of errors.

### Syntax errors

The word Syntax is defined as *the rules that state how words and phrases must be used in a computer language* by the oxford learners dictionary {cite:p}`syntax`. 

A syntax error occurs *before* code execution. In other words, when you try to build your program, the computer (the compiler) will check if every word you used is defined in C++, and if you left out any important details in your code.

To truly understand syntax errros, try to build the following code and fix any errros:


```c++
using namespace std

int main[] 
{ 
    cout << "Hello World" << endl; 
} 
```



### Runtime errors
Runtime errors are errors you experience after your program is already running. A common type of runtime error is referred to as an *input error*, these types of errors occur when a user inputs a value which the program can not handle such as division by 0.

Try running the code below and inputing 0 to see what a runtime error looks like:

```c++
#include <iostream> 
using namespace std;

int main() 
{ 
    cout << "This program will divide 5 by any number you'd like" << endl; 
    int i = 5;
    cout << "Input a number to divide:" << endl;
    int j;
    cin >> j;
    cout << "the result is " << i/j;
} 
```

**Food for thought:"" How would you fix this error?

### Logic Errors
Logic errors may be the most dangerous errors because occur when a program does not do what we intend it to do. Often we won't even notice we have a logic error until we fail an exam at college or when [a mars orbiter stops transmitting signals back to earth](https://solarsystem.nasa.gov/missions/mars-climate-orbiter/in-depth/).

Can you spot the logic error in the following code:
```c++
#include <iostream> 
using namespace std;

int main() 
{ 
    cout << "This program will multiple 5 by any number you'd like" << endl; 
    int i = 5;
    cout << "Input a number to multiply:" << endl;
    int j;
    cin >> j;
    cout << "the result is " << i*j;
} 
```
The problem in the code above is the types we used 😕. But what are types?

## Types and Variables

In the section above you may have noticed the `int` keyword. To understand what an `int` is and why we saw a logic error with the code above, we will need to learn some basic terminology. 

Essentialy to do anything practical while programming, we need to be able to save and reuse data. To do so we create what is referred to as **variables**. Variables are stored in what we call **objects**. To access the objects we need a **name**, and to define constraints on what an object can and cannot do, we will give every variable a **type** as well.

If this seems a bit complex picture our computer as a warehouse filled with storage units. In this warehouse:
- The storage units are **objects**.
- To access/use the storage units we need to define a **variable**.
- When we use the storage unit we want to make sure that we do it within the constraints of the warehouse. We do this by defining a **type**.
- To find a storage unit we give it a **name** which the warehouse workers (our computer) know how to map to its physical location.

Formally, when ever we store new data we will write a line of code like this:

```C++
type name = newData;
```
### Variable Declaration

The above example can actually be split up in to two parts.  Essentialy, as you may have noticed in the logic error example, sometimes we may want to predefine a variable for later use. In the warehouse example you can think of it as securing a storage unit for later use. If we only want to define a variable we may write code of the form:

```C++
type name;
```
**Note**: In many textbooks you may find that defining a variable is also termed **variable declaration**.

### Variable Assignment
In the logic error example, we saved data into the variable using the `cin` stream operator. Another way to save data is by using the **assignment operator** `=`:

```C++
name = data;
```
Notice that the equals sign in programming is not like the equals sign in math. In programming, whenever you see the assignmnet operator `=` you can read "I am saving what is to thr right of the `=` sign in to the variable on the left of the `=` sign.

Variables, as there name suggest, can change values through out our program. So the assignment operator is actually also useful if we want to to change values midway through a program. Just make sure you only save data with in the constraints of the type your variable is!
 
### Types

The common types and their basic constraints you will see in the next few lessons are:
- `int` - Short for integers, stores a whole number value.
- `double`- Stores floating-point numbers (i.e. decimals)
- `char` - Short for character, stores individual characters.
- `string` - A "string" of characters, stores text.
- `bool` - Short for boolean, a logic type (`true` or `false`).

### Circling Back
So why did we see a logic error in the example from  section 2.3.3? The problem lies in the type we used along with the promises we made to our user. When we defined a variable as `int`, our computer expected we only store whole numbers in it. If you tried to enter a decimal in the program with the logic error, the computer will ignore any decimal input. To fix our logic error, we should have used the `double` type to insure our code will work for all inputs. 

## Bibliography
```{bibliography}
:filter: docname in docnames
```