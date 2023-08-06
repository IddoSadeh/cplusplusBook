# Arrays and Containers
In the previous chapters, we explored the basic building blocks of programming in C++, from writing your first program to understanding types and variables. Now, we'll extend our knowledge to store multiple values efficiently. By the end of this chapter you will be able to:
- Use arrays.
- Use vectors.
- use for-each loops.

## Table of Contents:
```{contents}
```

## Arrays

An array is a collection of elements (values or variables) that are accessed by indexing. Think of it as a numbered list where you can store multiple values of the same type.

### Declaring an Array

You can declare an array in C++ by specifying its type, followed by its name, and the number of elements it can hold inside square brackets:

```c++
int numbers[5]; // declares an array of 5 integers
```

### Initializing an Array

You can also initialize an array at the time of declaration:

```c++
int numbers[5] = {10, 20, 30, 40, 50}; 
```

If you choose to initialize an array at the time of declaration, you are allowed to declare it without defining its size:

```c++
int numbers[] = {10, 20, 30, 40, 50}; // size will be 5
```

### Accessing Elements

You can access the elements of an array using their index, starting from 0:

```c++
int firstNumber = numbers[0]; // accesses the first element
```
### Multi-Dimensional Arrays
Arrays can be multi-dimensional, allowing you to create structures like matrices, which can be found in applications ranging from mathematical computations to image processing. Essentially, a multi-dimensional array is an array of arrays. In a 2-dimensional array, for example, each element of the main array is itself an array. This concept can be extended to create 3-dimensional arrays and beyond.

Here's how you might declare and initialize a 2-dimensional array in C++:

```c++
Copy code
int matrix[2][3] = {
  {1, 2, 3},
  {4, 5, 6}
};
```

In the above example, `matrix` is a 2D array consisting of 2 rows and 3 columns. Notice the structure created by the curly brackets; it represents one large array that contains two elements, and each of these elements is itself an array containing 3 elements. This nested arrangement allows for the efficient storage and manipulation of complex data structures, opening up a wide range of possibilities in programming. 

### Strings as Arrays of Characters

You may recall from the variables chapter that we used similar syntaxe for accesing characters in a string to that we use for awways. Essentialy, in C++, strings can be treated like arrays of characters. You can access each character of a string using its index:


```c++
string name = "Alice";
char firstLetter = name[0]; // 'A'
```


## Containers

While arrays are powerful and simple to use, they have a limitation: their size is fixed at the time of declaration. What if we need a collection that can grow or shrink in size as needed? That's where containers come into play.

Containers are dynamic data structures that can expand or contract as required. C++ provides several container classes, and one of the most commonly used is `vector`. A vector is similar to an array but can change in size, providing greater flexibility.

### Declaring and Initializing a Vector

Declaring a vector is similar to declaring an array, but you need to include the `<vector>` header. Here's how you can declare and initialize a vector:

```c++
#include <vector>

vector<int> numbers = {10, 20, 30, 40, 50};
```

### Accessing Elements

Like arrays, you can access elements of a vector using an index:

```c++
int firstNumber = numbers[0]; // accesses the first element
```

### Useful Functions with Vectors

Vectors come with some handy functions that allow you to manage the elements within them:

- **Adding Elements**: You can add elements to the end of a vector using the `push_back` method.

```c++
numbers.push_back(60); // adds 60 to the end of the vector
```

- **Removing Elements**: You can remove elements from the end of a vector using the `pop_back` method.

```c++
numbers.pop_back(); // removes the last element
```

- **Size of Vector**: You can get the number of elements in a vector using the `size` method.

```c++
int size = numbers.size(); // gets the size of the vector
```

These functions enhance the usability of vectors, making them a versatile choice for storing collections of data that might need to change in size. With vectors, you gain more control and flexibility compared to fixed-size arrays.


## For-Each Loops

Iterating over arrays or containers can be simplified using a for-each loop. It allows you to traverse the entire collection without dealing with the index.

```c++
int numbers[] = {10, 20, 30, 40, 50}; 
for(int number : numbers) {
    cout << number << ' ';
}
// Output: 10 20 30 40 50
```

Please explore for each loops in your IDE.


## Summary

In this chapter, we have expanded our understanding of C++ by learning how to store multiple values using arrays and containers like vectors. We also learned a new way to iterate over these collections using for-each loops.

By getting familiar with these concepts, you are equipping yourself with essential tools that will come in handy as you delve further into programming. Practice using arrays and containers in different scenarios to deepen your understanding.

In the next chapter, we'll talk more about C++ standard libraries.


## Practice Problems

1. **Basic Array Manipulation**: Declare an array of integers with 5 elements. Initialize it with the values 1, 2, 3, 4, 5. Write a program to reverse the array and print the reversed array.

2. **Vector Operations**: Create a vector of `double` and use a loop to add the first ten even numbers to it. Then, use a for-each loop to print the contents.

3. **String Characters**: Write a program that takes a string as input and prints the characters at all the odd indices. (Hint: Remember, strings can be treated as arrays of characters!)

4. **Self Learning Required - Size of an Array**: Declare an array of float with 10 elements. Write a code snippet to print the size of the array using the `sizeof` function, and explain the result.

5. **Self Learning Required - Multi-Dimensional Arrays**: Create a 3x3 matrix (2-dimensional array) and initialize it with values of your choice. Write a program that prints the transpose of the matrix.

6. **Multi-Dimensional Vectors**: Write a program that defines a 2D vector with 3 rows and 4 columns. Initialize the vector and print its contents.

7. **Challenging - Simulation of Tic-Tac-Toe Board**: Use a 2-dimensional array to simulate a Tic-Tac-Toe board. Initialize the board with empty characters and write functions to display the board, place a mark, and check for a win. You may use 'X' and 'O' to represent the players.

8. **Challenging - Dynamic Resizing with Vectors:** Write a program that starts with an empty vector of integers. Allow the user to continuously add numbers to the vector until they enter a specific sentinel value (such as -1). After that, print the entire vector and its size. Then, allow the user to remove numbers from the end until they enter the sentinel value again.

Remember to refer back to the concepts and examples in this chapter as you work on these problems. Happy coding!
## Bibliography
```{bibliography}
:filter: docname in docnames
```