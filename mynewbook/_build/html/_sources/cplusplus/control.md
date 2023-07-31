# Control Structres

In the last chapter we got technical and learned about Variables and Data types. In this chapter we will tone it down a notch and learn how to write more functional programs using control structures. Control structures dictate the order in which lines of code are executed in a program. In C++, as with most other programming languages, the basic control structures are selection (making decisions) and repetition (loops). By the end of this chapter you should know how to use:
- If statments.
- Switch statements.
- For loops.
- While loops.
- Do-While loops.

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

## Loops: `while` and `for`

Loops are used when you want a section of code to be repeated several times. In C++, `while` and `for` loops are used for this purpose.

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
int i = 1;
do {
    cout << "i is: " << i << "\n";
    i++;
} while (i < 6);
```
In this case, the condition is also `a < 6`, but the output will be slightly different because our condition is at the end of the loop. Please run this code and see for yourself.

### `for`

The `for` loop is used when you want to loop through a block of code a known number of times.

```c++
for (int a = 1; a < 6; a++) {
    cout << a;
}
```

In this case, the `for` loop is set up with three statements: the initialization (`int a = 1`), the condition (`a < 6`), and the increment (`a++`). The code within the `for` loop is executed until `a` is no longer less than 6.


## Switch Statement

The `switch` statement is used to select one of many blocks of code to be executed.

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

Each `case` ends with a `break` statement, which is used to exit the `switch` statement. If the `break` is not included, the next `case` will be executed even if the condition is not met. This behavior is called fallthrough. If you want to intentionally use the fallthrough behavior, you can omit the `break`.

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


Remember to solve these exercises yourself and compare your solutions to the expected output. The key to learning programming is practice. You'll get comfortable with the syntax and logic as you write more code.