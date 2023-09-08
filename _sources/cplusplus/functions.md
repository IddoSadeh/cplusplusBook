# Functions
In the last chapter we learned about conditional statements as control structures. Now that are code is getting bigger and more complicated we need to get to know about functions. By the end of this chapter you will know:
- What makes up a function.
- How to create your own function.
- Encapsulation and why functions are important.

## Table of Contents

```{contents}
```

## Functions in C++

In any programming language, functions serve as an essential tool for structuring and organizing code. In C++, this is no exception. Functions play a vital role in the creation of efficient, manageable, and coherent code. 

Functions offer numerous advantages:

1. **Encapsulation:** This principle refers to the idea of bundling related operations into a single unit, i.e., a function. Encapsulation enables programmers to create modular pieces of code that perform specific tasks independently from the rest of the code base. This not only improves code readability and reusability but also makes maintenance and debugging processes more manageable. 

2. **Code Reusability:** Functions allow code to be reused. Instead of writing the same code repeatedly, a function encapsulates that code which can be called multiple times whenever needed.

3. **Abstraction:** Functions provide a level of abstraction; they allow us to conceal the complex details of what's happening inside the function, offering a simpler interface for use.

Understanding and effectively utilizing functions is a key step in becoming proficient in C++. In this chapter, we will delve deeper into the nature and usage of functions in C++, exploring different aspects such as function declaration, definition, calls, and more.


## Understanding Functions

In C++, a function is a group of statements that is given a name, and which can be called from some point of the program. The main function (`main()`) is the starting point of every C++ program.

The syntax for defining a function in C++ is as follows:

```C++
return_type function_name( parameter list ) {
   body of the function
}
```

Where:
- `return_type`: This is the data type of the value the function returns. If the function doesn't return a value, `void` is used.
- `function_name`: This is the identifier by which the function can be called.
- `parameter list`: This includes the type, order, and number of parameters of a function. Parameters are optional; that is, a function may contain no parameters.
- `body of the function`: This is a collection of statements that define what the function does.



## Function Definition and Declaration

To use a function in C++ we must first **declare** it. A function declaration differs from a function defenition as its only role is to tell the compiler about the function's name, return type, and parameters, but it doesn't provide the actual body of the function.

In a way, you can think of a function definition as a way to give our computer a "heads up" that we will eventually have a function in our program with a given return type, name and parameters.

To declare a function we use the following syntax:
```C++
return_type function_name( parameter list );
```

The function declaration ALWAYS comes before the definition. For example see the code below:

```C++
#include <iostream>
using namespace std;

// function declaration
void printMessage();

// main function
int main() {
    printMessage(); //function call
}

// function definition
void printMessage() {
   cout << "Hello, World!" << endl;
}
```

## Function Call

Once you've declare and defined you function, how do you use it? functions are used by invoking a **function call**. A function call is how we execute a function in C++. We specify the function name and the values (if any) for its parameters. Here's an example:

```C++
int main() {
   // function call
   printMessage();  // outputs: Hello, World!
   return 0;
}
```

## Function Parameters and Arguments

In your math class, you may have learned about functions of the form `f(x)=ax+b`. If you recall, mathematical functions map inputs to outputs. In programming, this is the same case. 

In the above `printMessage` example we have no inputs (which is an input in itself), and the same output everytime (print hellow world to our console). 

To add inputs to our functions we will use what is referred to as **parameters**. 

Parameters are the variables listed inside the parentheses in the function declaration and definition. When a function is invoked, you pass a value to the parameter. This value is referred to as an argument. Here's an example:

```C++
// function declaration
void printSum(int a, int b);

int main() {
   // function call
   printSum(5, 10);  // outputs: The sum is: 15
   return 0;
}

// function definition
void printSum(int a, int b) {
   int sum = a + b;
   cout << "The sum is: " << sum << endl;
}
```

In this example, `a` and `b` are parameters, and `5` and `10` are arguments.

## Scope and a Note About Parameters and Arguments

New programmers often strugle with differentiating between parameters and arguments.

Lets change the above example slightly to make this distinction clearer, and introduce a new concept - **scope**.

```C++
// function declaration
void printSum(int a, int b); // declared in the global scope

int c = 20; // variable in global scope

int main() {
   int a = 5;
   int b = 10;
   int d = 15;
   cout << c;
   cout << d; // declared in a local scope
   printSum(a, b);  // outputs: The sum is: 15
   return 0;
}

// function definition
void printSum(int a, int b) {
   int sum = a + b;
   cout << "The sum is: " << sum << endl;
   cout << c;
   cout << d; // d does not exist in this scope, will not compile
}
```
In the above example we see the variables `int a` and `int b` declared three times. Once in the function declaration, once in the function definition, and onse in `main()`.

You may recall from the chapter about variables, that we are only allowed to declare variables ONCE. This is still the case, but it is true only within a given **scope**. 

A scope is the part of a program where a name can be used to refer to some entity in our program. In the above example, we have three scopes: the global scope, and two local scopes.

- The global scope, in short, is the whole file. Anything declared here will be available in all parts of the file, i.e., we can use or print `c` form the above code anywhere in the code. 

- A local scope, in short, is the piece of code enclosed between two curly brackets. Any variable declared in a local scope will only be accesible with in that scope, i.e., `d` from the above code will only be accesible in `main()`.


So why do we do declare `a` and `b` three times?
- In the function declaration, as mentioned before, we are giving a heads up to the compiler that the function `printSum` exists, and once we use it we will need to create two new integer variables.
- In the function definition, we declare two variables to be used as our parameters. These parameters will hold the data passed to them until we are done using the function. They cease to exist when the function finishes it's duty.
- In `main()` we declare the variables for the sake of this example and to confuse you a bit. The variables will hold data, that will be passed as arguments to our function. These arguments will be saved in to the function parameters until the function finishes it's duty. The key here is to understand that `a` and `b` from `main()` are not the same `a` and `b`from `printSum`.



## Return Values

We talked about inputs in the previous subsection, but what about outputs? In the `printSum` and `printMessage` example our output was of type `void`. `void` outputs mean that the function output will be some sort of internal computational operation. In the given examples this was printing to the console.

Sometimes, we want our function output to be some data that we can use later in our program. To do so we use need to `return` the data.

A C++ function can return a value using the `return` statement in conjunction with a value or object. This value is considered the "output" of the function. Here's an example:

```C++
// function declaration and definition
int add(int a, int b) {
   int sum = a + b;
   return sum;
}

int main() {
   // function call
   int result = add(5, 10);  // result = 15
   cout << "The sum is: " << result << endl;
   return 0;
}
```

In this example, the `add()` function returns the sum of `a` and `b`, which is stored in the `result` variable in the `main()` function.


## Function Overloading

After exploring the fundamentals of functions, let's delve into a more advanced concept that can increase the flexibility of our code: function overloading.

Function overloading is a feature in C++ that allows multiple functions to have the same name, but with different parameters (either a different number of parameters or different types). The compiler selects the correct function based on the arguments passed during the function call.

Here's an example:

```C++
void print(int i) {
  cout << "Integer: " << i << endl;
}

void print(double d) {
  cout << "Double: " << d << endl;
}

int main() {
  print(5);    // Calls the function with an integer parameter
  print(5.5);  // Calls the function with a double parameter
  return 0;
}
```

Function overloading helps in writing flexible code, where a function's name succinctly expresses its purpose, while its varying parameters handle different specific cases. It allows programmers to write functions that can handle different data types and numbers of arguments, without needing to create a unique name for each variation.

## Summary

With our understanding of functions, we've added a transformative tool to our coding arsenal. It's time to review what we've covered in this chapter, highlighting the crucial takeaways before embarking on our next programming adventure.

- **Functions** are fundamental building blocks in C++ programming. They provide a way to structure programs effectively, enabling code reuse, abstraction, and modularity.

- A **function** in C++ is defined with a return type, a function name, and a list of parameters enclosed in parentheses. The code to be executed is placed within curly braces `{}`.

- **Function calls** are used to invoke functions. The function name is written followed by parentheses, with any required arguments placed inside the parentheses.

- **Parameters** are specified in the function declaration within the parentheses following the function name. They act as placeholders for the values that are passed into the function when it is called.

- The **return type** of a function defines the type of value the function will return. It can be any valid data type. If the function does not return a value, the return type should be `void`.


- The **function body** contains the block of code that performs the specific task of the function.

- **Scope** is a section of a program in which a declared variable or function can be called.

- The **main()** function is a special function that serves as the entry point of the C++ program. Execution of the program begins and ends with the main function.

- The use of functions encourages the principle of **encapsulation**, allowing for easier debugging and increased readability of code.

- **Function Overloading** allows multiple functions to have the same name but with different parameters, enabling the same function name to perform different tasks based on the arguments passed.

## Practice Problems

1. Write a function named add that takes two integers as input parameters and returns their sum.

2. Write a function named multiply that takes two integers as input parameters and returns their product.

3. Write a function named greet that takes no parameters and doesn't return a value. The function should just print a predefined message to the screen, such as "Hello, World!"

4. Write a function named divide that takes two doubles as input parameters. The function should return the result of the first number divided by the second number.

5. Write a function named compare that takes two integers. The function should return true if the first integer is greater than the second integer, and false otherwise.

6. Implement a set of overloaded functions named `calculateArea` that return the area of different geometric shapes (e.g., circle, rectangle). Use the appropriate parameters for each shape (e.g., radius for the circle, length, and width for the rectangle).


Remember to test your functions thoroughly with different inputs to make sure they work as expected.

 
## Bibliography
```{bibliography}
:filter: docname in docnames
```