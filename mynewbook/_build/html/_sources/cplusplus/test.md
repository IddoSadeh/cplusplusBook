Certainly! Here's the revised version, removing `std::`, adding context for each section, and introducing a random function.

# Standard Libraries, Common Libraries, and Useful Functions

## Table of Contents:
```{contents}
```

## Introduction to Libraries

Libraries in C++ provide predefined functions, classes, and objects that can be used in your programs. They extend the functionality of C++ and can save significant time and effort. You've already encountered libraries such as `<iostream>` and `<vector>`, and now we'll dive deeper into other essential libraries and their functions.

## Common Libraries and Functions

### Input and Output - `<iostream>`

Handling input and output is fundamental in programming. With `<iostream>`, you can display data to the screen or read input from the user.

[...Examples as before...]

### Mathematical Functions - `<cmath>`

Whether you're designing a scientific application, a financial model, or a game, mathematical functions are crucial. The `<cmath>` library offers a variety of mathematical operations.

#### Examples:
```c++
#include <cmath>

double squareRoot = sqrt(25); // 5.0
double power = pow(2, 3); // 8.0
double sineValue = sin(M_PI / 2); // 1.0
double logarithm = log(2.7182); // 1.0 (natural logarithm)
```

### String Manipulation - `<string>`

Strings are used to represent text. The `<string>` library allows you to manipulate strings easily, which can be essential in text processing, file handling, and user interaction.

#### Examples:
```c++
#include <string>

string name = "Alice";
string fullName = name + " Johnson"; // Concatenation

int length = name.size(); // Gets the length of the string

string upperName = name;
transform(upperName.begin(), upperName.end(), upperName.begin(), ::toupper); // Converts to uppercase
```

### Working with Time - `<ctime>`

In many applications, including logging, scheduling, and real-time monitoring, handling time is vital. The `<ctime>` library allows you to manipulate and format time.

#### Examples:
```c++
#include <ctime>

time_t now = time(0); // Get current time in seconds since epoch
tm* localTime = localtime(&now); // Convert to local time

int year = localTime->tm_year + 1900; // Get the year
int month = localTime->tm_mon + 1; // Get the month
int day = localTime->tm_mday; // Get the day
```

### Generating Random Numbers - `<cstdlib>`

Random numbers are used in various applications, such as games, simulations, and cryptography. You can generate random numbers using the `<cstdlib>` library.

```c++
#include <cstdlib>
#include <ctime>

srand(time(0)); // seed the random number generator
int randomValue = rand() % 100; // generates a random number between 0 and 99
```

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

In this chapter, we have delved into some common and useful standard libraries in C++. These libraries expand the functionalities of C++, allowing you to perform tasks ranging from basic arithmetic to file handling with ease.

By leveraging these libraries, you are equipping yourself with powerful tools that will enhance your programming capabilities and make your coding journey more enjoyable.

In the next chapter, we'll explore the concept of object-oriented programming, a paradigm that further elevates the structure and maintainability of your code.

## Bibliography
```{bibliography}
```

## Practice Problems

[...Same as before...]

These libraries are the building blocks that will enable you to create more complex and dynamic applications. Experiment with them, explore their documentation, and try to integrate them into your projects. Happy coding!