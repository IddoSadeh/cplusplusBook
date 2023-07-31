# Control Structres

In the last chpater we got technical and learned about Variables and Data types. In this chapter we will tone it down a notch and learn how to write more functional programs using control structures. Control structures dictate the order in which lines of code are executed in a program. In C++, as with most other programming languages, the basic control structures are selection (making decisions) and repetition (loops). By the end of this chapter you should know how to use:
- If statments.
- Switch statements.
- For loops.
- While loops.
- Do-While loops.

## Table of Contents
```{contents}
```

### Selection

Selection control structures allow your program to make decisions based on conditions. The primary selection control structures in C++ are the `if` statement, `if-else` statement, and `switch` statement.

#### If Statement

An `if` statement allows the program to execute a block of code only if a certain condition is met.

```C++
int x = 10;
if (x > 5) {
    cout << "x is greater than 5.";
}
```
In this example, because `x` is indeed greater than 5, "x is greater than 5." will be printed to the console.

#### If-Else Statement

An `if-else` statement allows the program to execute one block of code if a condition is true and another block if the condition is false.

```C++
int x = 3;
if (x > 5) {
    cout << "x is greater than 5.";
} else {
    cout << "x is not greater than 5.";
}
```
In this case, "x is not greater than 5." will be printed because `x` is not greater than 5.

#### Switch Statement

A `switch` statement allows a program to choose between multiple blocks of code based on the value of an expression.

```C++
int day = 3;
switch (day) {
    case 1:
        std::cout << "Monday";
        break;
    case 2:
        std::cout << "Tuesday";
        break;
    case 3:
        std::cout << "Wednesday";
        break;
    // Cases for other days would go here...
    default:
        std::cout << "Invalid day";
}
```
This program will print "Wednesday" because `day` equals 3. If `day` did not match any of the cases, the `default` case would be executed, and "Invalid day" would be printed.

Repetition
Repetition control structures allow your program to execute a block of code multiple times. The primary repetition control structures in C++ are the for loop, while loop, and do-while loop.

For Loop

A for loop is useful when you know exactly how many times you want to repeat a block of code.

C++
Copy code
for (int i = 0; i < 5; i++) {
    std::cout << "i is: " << i << "\n";
}
This will print the numbers 0 through 4, each on a new line.

While Loop

A while loop is useful when you want to repeat a block of code an unknown number of times until a certain condition is met.

C++
Copy code
int i = 0;
while (i < 5) {
    std::cout << "i is: " << i << "\n";
    i++;
}
This will print the same output as the previous for loop example.

Do-While Loop

A do-while loop is similar to a while loop but with one key difference: the condition is checked at the end of the loop, so the loop is guaranteed to run at least once.

C++
Copy code
int i = 0;
do {
    std::cout << "i is: " << i << "\n";
    i++;
} while (i < 5);
Once again, this will print the same output as the for loop and while loop examples.