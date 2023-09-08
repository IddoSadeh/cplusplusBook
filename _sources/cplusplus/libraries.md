# Standard Libraries, Common Libraries, and Useful Functions
In previous chapters, we ventured into some essential programming concepts, such as variables, types, arrays, and containers. We even encountered examples of C++ libraries, such as `<iostream>` for input-output operations and `<vector>` for working with dynamic arrays. Now, let's dive deeper into the world of C++ libraries, exploring standard libraries, some common libraries, and the useful functions they offer.

## Table of Contents:
```{contents}
```

## Introduction to Libraries

A library in C++ is a collection of precompiled code that you can use in your program. It contains functions, classes, and variables that allow you to perform common tasks without having to write the code yourself. By using libraries, you can save time, reduce errors, and make your code more readable and maintainable.

### Standard Libraries

C++ comes with a rich set of standard libraries that provide essential functionalities. Some examples that you've already seen include:

- `<iostream>`: Used for input and output operations.
- `<vector>`: Provides a dynamic array (vector) data structure.

### Including Libraries

To use a library in your code, you must include its header file using the `#include` directive. For example:

```c++
#include <iostream>
#include <vector>
```

## Common Libraries and Functions

### Input and Output - `<iostream>`

We've been using this library to perform input and output operations with the `cin` and `cout` objects.

#### Example:
```c++
int number;
cout << "Enter a number: ";
cin >> number;
cout << "You entered: " << number << std::endl;
```

### Mathematical Functions - `<cmath>`

This library offers functions to perform mathematical operations like square root, power, trigonometric functions, and more. Here are some examples:

#### Example:
```c++
#include <cmath>

double squareRoot = sqrt(25); // 5.0
double power = pow(2, 3); // 8.0
```

You can explore more functions in the [C++ documentation](https://cplusplus.com/reference/cmath/).

### Working with Time - `<ctime>`

In many applications, including logging, scheduling, and real-time monitoring, handling time is vital. The <ctime> library allows you to manipulate and format time.

#### Example:
```c++
#include <ctime>

time_t now = time(0); // Get the current time
```

You can explore more functions in the [C++ documentation](https://cplusplus.com/reference/cmath/).

### Generating Random Numbers - `<cstdlib>`

Random numbers are used in various applications, such as games, simulations, and cryptography. You can generate random numbers using the `<cstdlib>` libraries `rand()` function. There are two steps to doing so:
- seed the random number
- define a range for the random number

#### Seeding the Random Number Generator
Seeding is the process of initializing the random number generator. By providing a seed value (usually the current time), you ensure that the sequence of random numbers generated is different each time the program runs. Without seeding, the sequence would be the same every time. Essentialy, a "seed" is the starting point for a sequence of pseudo-random numbers.

#### Random Number Range
The `rand()` function by itself generates a random integer within a range that depends on the implementation, often between 0 and a large constant like `RAND_MAX`. To define a specific range for the random number, you can use the modulus operator (`%`) and addition. For example, `rand() % (maxValue - minValue + 1) + minValue` will generate a random number between `minValue` and `maxValue`, inclusive. This expression takes the remainder of dividing the random number by the size of the range and then offsets it by the minimum value, ensuring that the result falls within the desired bounds.

The two steps combined in code would like like this:
```c++
#include <cstdlib>
#include <ctime>

srand(time(0)); // seed the random number generator with current time
int randomValue = rand() % 100; // generates a random number between 0 and 99

// Another function - Generating a random number within a range
int minValue = 10;
int maxValue = 20;
int randomInRange = rand() % (maxValue - minValue + 1) + minValue; // generates a random number between 10 and 20

```
The `<cstdlib>` library has some more functions that may be useful in your coding journey. 
You can explore more functions in the [C++ documentation](https://cplusplus.com/reference/cstdlib/).

### File Handling - `<fstream>`

File handling is essential for data storage and retrieval. With `<fstream>`, you can read and write files, enabling persistent storage of data across program executions.

#### Examples:
```c++
#include <fstream>

// Writing to a file
ofstream outFile("example.txt");
outFile << "Writing to a file." << endl;
outFile.close();

// Reading from a file
ifstream inFile("example.txt");
string line;
while (getline(inFile, line)) {
    cout << line << endl;
}
inFile.close();
```


## Summary

In this chapter, we explored the concept of libraries in C++, focusing on standard libraries that provide a wide range of functionalities. We saw how libraries simplify development by offering prebuilt functions and classes.

By understanding and using these libraries, you're equipping yourself with powerful tools that can significantly enhance your programming capabilities. Whether it's mathematical calculations, string manipulation, or working with time, these libraries offer robust solutions.

In the next chapter, we'll look at functions, a key concept that enables you to write modular and reusable code.


## Practice Problems

1. **Random Number Game**: Write a program that generates a random number between 1 and 100 and allows the user to guess the number. The program should provide feedback like "Too high!" or "Too low!" and continue until the user guesses the number.

2. **Simple File Writing and Reading**: Using the `<fstream>` library, write a program that asks the user for their name and saves it to a text file. Then, write a separate program that reads the name from the file and prints a greeting message.

3. **Mathematical Calculations**: Create a calculator program that takes two numbers and an operator (addition, subtraction, multiplication, division, or square root) as input. Use the `<cmath>` library to perform the selected operation and print the result.


4. **Working with Files - Word Count**: Write a program that reads a text file and counts the number of words in the file. You may consider any sequence of non-space characters separated by spaces as a word.


5. **Challenge Problem - Random Maze Generator**: Create a random maze generator using the `<cstdlib>` library to generate random paths. You can represent the maze as a grid, where 0 represents an open path and 1 represents a wall. Print the maze to the console.

These practice problems will help you strengthen your understanding of various standard libraries in C++ and provide hands-on experience working with random numbers, file operations, mathematical functions, and time management.

Happy coding!



## Bibliography
```{bibliography}
:filter: docname in docnames
```
 