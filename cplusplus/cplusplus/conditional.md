# Conditional Statements

In the last chapter we got technical and learned about Variables and Data types. In this chapter we will tone it down a notch and learn how to write more functional programs using control structures. Control structures dictate the order in which lines of code are executed in a program. In C++, as with most other programming languages, the basic control structures are selection (making decisions) and repetition (loops). By the end of this chapter you should know how to use:
- If-else statements.
- Switch statements.
- While loops.
- Do-While loops.
- For loops.
- Continue and Break keywords.

## Table of Contents
```{contents}
```

## Intro

Control structures manage the execution flow of your program. They allow your code to make decisions based on conditions or repeat an operation multiple times. C++ has several control structures, which we will cover in this chapter: `if`, `else`, `while`, `for`, and `switch`.

## Conditional Statements: `if` and `else`

Conditional statements are used to perform different actions based on different conditions. In C++, `if` and `else` are used for this purpose.

### `if`

The `if` statement is used to specify a block of code to be executed if a specified condition is true.

```c++
int a = 10;
if (a > 5) {
    cout << "a is greater than 5";
}
```

In this case, the condition is `a > 5`. If the condition is true, the code within the curly braces `{}` is executed.

### `else`

The `else` statement is used to specify a block of code to be executed if the condition in the `if` statement is false.

```c++
int a = 2;
if (a > 5) {
    cout << "a is greater than 5";
} else {
    cout << "a is not greater than 5";
}
```

In this case, since `a` is not greater than 5, the condition `a > 5` is false, so the code within the `else` statement is executed.

### `if-else-if`

In situations where you have multiple conditions to test, you can use the `if-else-if` construct. This allows you to check several conditions one after the other, and the first condition that is true will have its associated code block executed. Once a true condition is found, the rest of the conditions will be skipped.

Here's an example:

```c++
int score = 85;

if (score >= 90) {
    cout << "Grade A";
} else if (score >= 80) {
    cout << "Grade B";
} else if (score >= 70) {
    cout << "Grade C";
} else {
    cout << "Grade D";
}
```

In this case, the program will check the conditions in order. Since `score` is 85, the second condition (`score >= 80`) is true, so "Grade B" will be printed, and the rest of the conditions will not be checked.

The `if-else-if` construct provides a way to create more complex conditional logic, allowing for finer control over the flow of your program. It's essential to place these conditions in a logical order, as the first true condition will exit the entire construct, leaving the subsequent conditions untested.

## Switch Statement

While `if-else-if` constructs offer flexibility in handling multiple conditions, they can become cumbersome when dealing with a large number of specific values or cases. In scenarios where you are comparing a single variable against several constant values, C++ provides a more structured and readable construct known as the `switch` statement. In the following section, we'll explore how to use `switch` statements, which can simplify code and enhance clarity when working with multiple distinct cases.

```c++
int day = 3;
switch (day) {
    case 1:
        cout << "Monday";
        break;
    case 2:
        cout << "Tuesday";
        break;
    case 3:
        cout << "Wednesday";
        break;
    // You can have any number of case statements.
    default: 
        cout << "Invalid day";
        // Optional
        break;
}
```

In this case, the `switch` statement checks the value of `day`. If `day` equals 1, it prints "Monday", if `day` equals 2, it prints "Tuesday", and so on. The `default` case is executed if none of the `case` conditions are met. 

Each `case` ends with a `break` statement, which is used to exit the `switch` statement. If the `break` is not included, the next `case` will be executed even if the condition is not met. This behavior is called fallthrough. Take a minute to explore this behaviour in your IDE of choice by omitting the `break` statement in the provided code. 

## Loops: `while` and `for`

After understanding how to control the flow of a program through conditional statements like `if-else` and `switch`, it's essential to explore another fundamental concept in programming: loops. Loops allow repetitive execution of a block of code, making them a powerful tool for performing tasks multiple times efficiently. In the next section, we'll delve into the various types of loops in C++, including `for`, `for-each`, `while`, and `do-while`, and understand how they can be used in different scenarios.

### `while`

The `while` loop is used when you want to loop through a block of code an unknown number of times until a specified condition is met.

```c++
int a = 1;
while (a < 6) {
    cout << a;
    a++;
}
```

In this case, the condition is `a < 6`. The code within the `while` loop is executed until `a` is no longer less than 6.

### `do-while`
A `do-while` loop is similar to a `while` loop but with one key difference: the condition is checked at the end of the loop, so the loop is guaranteed to run at least once.

```C++
int a = 1;
do {
    cout << "a is: " << a << "\n";
    a++;
} while (a < 6);
```
In this case, the condition is also `a < 6`, but our condition is at the end of the loop. To get a better grasp for the difference between `while` and `do-while` loops, try running both pieces of code with `a` initially equaling 6.

### `for`

The `for` loop is used when you want to loop through a block of code a known number of times.

```c++
for (int a = 1; a < 6; a++) {
    cout << a;
}
```

In this case, the `for` loop is set up with three statements: the initialization (`int a = 1`), the condition (`a < 6`), and the increment (`a++`). The code within the `for` loop is executed until `a` is no longer less than 6.


## The `continue` and `break` Keywords

Within the context of conditional statemetns and loops, two specific keywords allow us to control the flow more precisely: `continue` and `break`. While we introduced the `break` statement earlier in the context of `switch` statements, the `continue` statement is new and has a specific role within loops.

- **`continue`**: The `continue` statement is used to skip the current iteration of the loop and proceed to the next one. This can be useful for skipping specific cases within a loop without interrupting the entire looping process.

- **`break`**: The `break` keyword is used to exit a loop entirely, breaking out of it and continuing with the code that follows the loop.

Here are examples demonstrating both keywords:

```c++
for (int i = 1; i <= 10; i++) {
    if (i % 2 == 0) {
        continue; // Skips even numbers
    }
    cout << i << " "; // Prints only odd numbers from 1 to 10
}

for (int i = 1; i <= 10; i++) {
    if (i > 5) {
        break; // Exits the loop when i is greater than 5
    }
    cout << i << " "; // Prints numbers from 1 to 5
}
```

The `continue` keyword allows us to control the execution of specific iterations, while the `break` keyword provides a way to exit the loop altogether. These two keywords offer greater control over the execution flow within loops and can be used to write more flexible and efficient code.

Understanding both `continue` and `break` is essential for handling complex looping scenarios and crafting robust, maintainable code.

## Summary

- **Conditional Statements (`if`, `else if`, `else`):** Enables program to make decisions based on conditions.
- **Looping Structures (`for`, `while`, `do-while`):** Executes code repeatedly as long as a certain condition is true.
  - `for`: Ideal when the number of iterations is known.
  - `while` and `do-while`: Useful when continuation depends on a condition that changes during loop execution.
- **`switch` Statement:** Provides cleaner, more readable way to handle multiple conditions based on a single variable.
- Control structures form the logical backbone of coding, from simple scripts to complex applications.
- Practice exercises provided for hands-on learning experience.

In the next chapter, we will talk about functions in C++, which are a way of packaging code into reusable modules.

## Practice Questions

1. **Question:** Write a program that reads a single character from the user. If the character is a lowercase letter, print "Lowercase". If it's an uppercase letter, print "Uppercase". If it's a digit, print "Digit". Otherwise, print "Other".

2. **Question:** Write a program that uses a `for` loop to print numbers from 1 to 10.

3. **Question:** Write a program that uses a `while` loop to print numbers from 10 to 1 in descending order.

4. **Question:** Write a program that asks the user to input a number. If the number is less than 10, print "This number is too small". If the number is exactly 10, print "Perfect number". If the number is greater than 10, print "This number is too large".

5. **Question:** Write a program using a `switch` statement that simulates a simple calculator. The program should take an operator (`+`, `-`, `*`, `/`) and two numbers from the user and then perform the appropriate operation.


6. **Hard Question:** Write a program that reads a binary number (as a string) from the user and prints its decimal representation.

7. **Hard Question:** Write a program that accepts a string and convert all the lowercase letters in the string to uppercase.

8. **Hard Question:** Write a program that reads a binary number (as an integer) from the user and prints its decimal representation. *Hint: use % and / operators*

Remember to solve these exercises yourself and compare your solutions to the expected output. The key to learning programming is practice. You'll get comfortable with the syntax and logic as you write more code.
 
## Bibliography
```{bibliography}
:filter: docname in docnames
```