# Hello World
```{contents}
```

## Your First Program

In the previous chapter we wrote our first C++ program:

```c++
#include <iostream> //line 1

int main() //line 2
{ //line 3
    std::cout << "Hello World" << std::endl; //line 4
} //line 5
```

Lets make some sense of the different components of this code before we move on to new topics.

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

### #include

The `#include` statement in C++ is a preprocessor directive. It instructs the computer what external files or libraries are needed to run this program. These files and libraries are called **header files**  in C++ 

In line 1 we include the `iostream` library, which is needed for the Input/Output (I/O) communication with your console. In this code, we need it so the computer can understand what the standard ouput stream ``cout``, and what the endline operation ``endl`` means. In the future, you will probably also use the standard input stream ``cin``.

We wont go to deep into header files and libraries until later on in this textbook. In the next few chapters, we will use pre built header files and introduce tham as needed.

### std::

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

### <<

``<<`` is a stream insertion operator. You'll always want to pair this with the ``cout`` command. The input operator for ``cin`` will look similar, but backwards: ``>>``.

### int main()

``int main()`` is a function the computer utilizes to know where to start executing your program. We'll learn all about functions very soon. 

For now, all you need to remember (but not necessarly understand) is that functions will have 5 main components:
- A *return type*, in this case int.
- The return type will be followed by the *function name*, in this case main.
- The function name is followed by *circle brackets*, which can be used to define necessary inputs required for the funciton to work. In this case we dont need any inputs so the brackets are empty.
- *Curly brackets* to associate code with a function. 
- *Code* that goes inside the brackets.

### ;

The last part of the code is the semicolon. The semicolon *must* be used after any executble line of code that is not a function or a #include statement

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


## Bibliography
```{bibliography}
```