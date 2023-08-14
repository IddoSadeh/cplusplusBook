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


### Multi-Dimensional Vectors

Multi-dimensional vectors are vectors of vectors, allowing you to create structures like matrices or other complex data arrangements. They can be declared and initialized in various ways, depending on the compiler and C++ standard used.

#### Declaring and Initializing a 2D Vector

Here's how you might declare and initialize a 2D vector in C++:

```cpp
vector<vector<int>> matrix = {
    {1, 2, 3, 4},
    {5, 6, 7, 8},
    {9, 8, 7, 6}
};
```

In some compiler environments or older C++ standards, you may encounter an error that requires a space between consecutive right angle brackets. In this case, the correct syntax would be:

```cpp
vector<vector<int> > matrix; // Note the space between the angle brackets
```

#### Alternative Method for Initializing 2D Vectors

If you encounter issues or want a more explicit way to initialize a 2D vector, you can follow these steps:

1. Create a single-dimensional vector that forms each row:

```cpp
vector<int> row(num_col, 0); // A row with 'num_col' elements, all initialized to 0
```

2. Create the complete two-dimensional vector using the row:

```cpp
vector<vector<int> > matrix(num_row, row); // 2D vector with 'num_row' rows, each initialized with 'row'
```

These statements allow you to control the initialization process and ensure compatibility with different compilers and standards.


## For-Each Loops (Range-Based Loops)

In C++, range-based loops, also known as for-each loops, make iterating over elements in a sequence like an array or vector more straightforward. This structure allows you to go through the entire collection without the need to manage indexes.

#### Understanding Range-Based Loops

Here's the general structure of a for-each loop:

```cpp
for(type element_name : collection_name)
{
    loop statements
    ...
}
```

This can be read as: "For each element of type `type` in `collection_name`, give it the name `element_name`, and execute the following statements...".

This loop structure, called a range-for-loop, denotes a range as a sequence of elements. In C++, the range for a vector `v` is `[0:v.size())`, a convention used throughout the language.

#### Example

Here's an example using a for-each loop with a vector:

```cpp
vector<int> numbers = {3, 5, 7, 2, 4, 6};
for (int num : numbers) {  // for each num in numbers
    cout << num << ' ';
}
// Output: 3 5 7 2 4 6
```

This code snippet iterates over all the elements in the vector `numbers`, printing each one followed by a space.

#### When to Use Range-Based Loops

Use range-based loops for simple iterations over all elements in a sequence, examining one element at a time. For more complex scenarios, like looking at specific intervals or segments of a collection, traditional for-statements might be more appropriate.


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