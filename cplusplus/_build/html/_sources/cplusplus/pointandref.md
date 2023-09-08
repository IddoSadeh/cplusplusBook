# Pointers and References
In this chapter, we will delve into the world of memory management in C++, focusing on pointers and references. These concepts are fundamental to understanding how data is stored and accessed in memory, and they enable powerful programming techniques. Many students find this topic extra difficult. See the resources section at the end of this chapter for more help.

By the end of this chapter, you should be able to:
- Understand what pointers and references are and how they work.
- Declare and use pointers and references in your code.
- Recognize the differences between pointers and references.
- Grasp the importance of memory management in C++.

## Table of Contents:
```{contents}
```

## Pointers

Previously, we imagined your computer's memory as a vast sequence of tiny compartments, each capable of holding a small piece of data. 

You can visualize this arrangement as a long shelf with numbered compartments:

```
[0] [1] [2] [3] [4] [5] [6] ... [N-1]
```

Each compartment has a unique number, known as its address. When you declare a variable in your program, such as:

```c++
double myValue = 3.14;
```

The computer reserves a specific compartment (or a series of compartments, depending on the data type) to store the value 3.14. The unique number of that compartment is the address of the variable `myValue`.

Now, what if you wanted to keep track of this address? In C++, you can use a special variable called a pointer. **A pointer holds the address of another variable.**

## Pointer Declaration and Assigment

A pointer variable can be declared the same way as a regular variable with a slight change, we put an asterix (`*`) symbol after the type declaration as follows:

```c++
double* pValue; // Reads in english as "a double pointer named pValue"
```

But how do we assign values to a pointer variable? In other words, how do we get the address of a variable? To do so we place the ampersand (`&`) symbol before the variable we want the address to in the following manner:

```c++
pValue = &myValue; // Reads in english as "assign the address of myValue to pValue"
```

At this point you may still be confused, or you understand what a pointer is but not why we need it. Before we continue and build on what we learned, take a minute to explore pointers in your IDE. Use `cout` statements to print variables (i.e. `myValue`), the address of variables (i.e. `&myValue`), and pointers to those variables (i.e. `pValue`).



## A Deep Dive into Pointers

 Let's explore the different functionalities of pointers to understand their significance and use cases. 



### Pass by Reference vs. Pass by Value

To start lets look at one of the most important functionalities pointers unlock for us.
In C++, you can pass variables to functions either by reference or by value. What does this mean?

- **Pass by Value**: This is what were used to up until know. The function receives a copy of the variable. Hence, changes inside the function do not affect the original variable. 

  ```c++
    #include <iostream>
    using namespace std;

    void modifyValue(int value);

    int main() {
        int a = 5 ;
        modifyValue(a);
        cout << a; // will print 5
    }

    void modifyValue(int value) {
        value = 99; // Does not affect the original variable
    }
  ```
  In the example above, you can see that even though the value of `a` gets passed and save to `value`, any operation done one `value` will not happen to `a`.

- **Pass by Reference**: The function receives a reference to the original variable. As shown below, changes inside the function affect the original variable. 

  ```c++
    #include <iostream>
    using namespace std;

    void modifyValue(int* value);

    int main() {
        int a = 5 ;
        int* pa = &a;
        modifyValue(pa);
        cout << a; // will print 99
    }

    void modifyValue(int* value) {
        *value = 99; // Does affect the original variable
    }
  ```

  In the code above we show what passing by reference enables in C++:
  - We pass `pa` (the pointer to `a` - the adress of `a`) to the function `modifyValue()`. 
  - Then `pa` gets stored in the pointer variable `value`, hence we have access to the location of `a` within the scope of `modifyValue`.
  - Since we have a memory location stored in `value`, we can access and change the data at the location stored in `value` by putting an asterix (`*`) before `value` - this is referred to as the **derefrencing**. 

  Any changes done in the above manner will persist in the computer memory. You will find this especially useful if you want to write clean code that utilizes functions for encapsulation and procedural abstraction.

### Derefrencing

We've just seen how derefrencing works, but lets spend a minute to make sure you understand what derefrencing is. Firs, to empahsize what derefrencing means, think of derefrencing a pointer as getting the data stored in the adress saved in the pointer.

Now, open an IDE, run the code below, and make changes as needed to explore the different behaviours weve learned up until now.:


```c++
#include <iostream>
using namespace std;

int main() {
    int a = 5 ;
    cout << "a = " << a <<endl;      // will print 5
    cout << "&a = " << &a <<endl;     // will print the location of a
    int* pa = &a;   // a pointer to the location of a
    cout << "pa = " << pa <<endl;     // will print the location of a
    int b = *pa;    // derefrence pa and save the result in b  
    cout << "*pa = " << *pa <<endl;    // will print 5
    cout << "b = " << b <<endl;     // will print 5
    cout << "*&a = " << *&a <<endl;     // will print 5
}

```

### Pointers Are Distinct From Variables

At this point, it is important to emphasize some key points about pointers:

- First recall that pointers are not interchangeable with regular data types, that is an `int` cant be saved into an `int*`. Although the type defintion looks the same, the data stored isn't.

- Unlike variables which can be dynamically casted (i.e. a `float` value can be saved into a `double` value), pointers are specific to the types they point to. A pointer to one type cannot be assigned to a pointer of another type, as this would lead to confusion about the size and structure of the data:

    ```c++
    long* pAge;
    char* pChar;
    pChar = pAge; // Error: can't assign a long* to a char*
    ```
- Pointers can be reassigned values, and pointers of the same type can be assigned to other pointers. For example:
     ```c++
    int* pAge = &age;
    int* pNum = &num;
    pNum = pAge; // This is allowed
    ```
    Keep this last point in mind for the next section.

### Memory Management

When a C++ program is initiated, the compiler divides memory into different sections. These include areas for the code itself, global variables, and function calls. The remaining memory, often referred to as the "free store" or "heap," is available for dynamic allocation.

The free store can be accessed using the `new` operator. For instance, you can allocate space for four doubles with:

```c++
double* p = new double[4];
```

This command requests room for an array of four doubles from the free store and returns a pointer to the first one. This is the first time we use a poitner to point to an array. You may be wondering what happens when we derefrence an array, and how we can access data from the array. It's pretty simple:
- `*p` returns the first value of the array.
- Surprisingly, `p[0]` also returns the first value of the array.
- The rest of the array can be accessed like a regular array i.e. `p[1]`, `p[3]`

The above syntax is a tad problemtic though. Lets explore why.

#### Free Store Allocation

The `new` operator is used to request memory from the free store, returning a pointer to the allocated space. This pointer points to an object of a specified type, **but it doesn't know how many elements it points to**.

Why did I highlight the previous sentence? 

Lets look at two dangeourous examples. Frist some code:

```c++
 // allocate memory for a new int, save the location at singleInt
 int* singleInt = new int;
// allocate memory for a new int array, save the location of the first element
int* arrayOfInts = new int[4]; 
```
And lets bring back our depiction of how are computers memory is made up of a bunch of memory compartments:

```
[0] [1] [2] [3] [4] [5] [6] ... [N-1]
```

Now, lets imagine that in the depiction above we have the following allocations:
- Compartment [0] is the C++ program minus the "free store" memory.
- Compartment [1] is the location saved in arrayOfInts at time of declaration.
- Compartments [1], [2], [3], [4]  are allocated for an array that will start at Compartment [1].
- Compartment [5] is the location saved in singleInt at time of declaration.
- Compartment [6] has very important information you dont want to lose.

##### Example 1:

Recall that we learned earlier that pointers can be reassigned values, and pointers of the same type can be assigned to other pointers. That means that the following code is allowed in C++ and will compile without issues:

```c++
int* arrayOfInts = singleInt;
```

If we decide to run the code above, what will happen is that are memory organization will change as follows:

- Compartment [0] is the C++ program minus the "free store" memory.
- Compartment [1] will no longer have any pointer pointing to it.
- Compartment [5] is now the location saved in the pointer arrayOfInts.
- Compartments [5], [6], [7], [8]  are the locations we will be accessing if we use the notation for accesing array data (i.e. `arrayOfInts[0]` will access compatment [5], `arrayOfInts[1]` will access compartment [6] etc.)
- Compartment [6] still has very important information you dont want to lose (we have onlayed iwth pointers up until now, no data was changed).

In this case, as you may see, we are in big trouble. If you naively write code like this:

```c++
arrayOfInts[1] = 5;
```
The important data you had saved in compartment [6] of your computer is now gone!

##### Example 2:
Since pointers don't know how many addresses they actually occupy, we can theoretically do something like this:
```c++
arrayOfInts[5] = 5;
```
This is called out-of-range access. Again, if we only allocated 4 compartments to `arrayOfInts` and we try to access a 5th, we may end up dealing with data we have no business in dealing with.

#### Stay Calm

Modern operating systems will protect you from corrupting important files on your computer with pointers. If you do accidently access the wrong memory address, one of two things will happen:
- your program will crash.
- unexpected behaviours and outputs.

You may be asking why even use pointers if they are so dangerous. There are f ew simple reasons:
- You run out of memory on the non "free-store" memory for your program.
- You want the memory you allocated to be accesible across different scopes (for example, return a pointer from a function)

The next question you might be asking is how to stay safe? Generally speaking try to limit the use of making pointers with the `new` keyword. And if you must use the "free-store" memory, don't forget to delete your pointers :)



### Freeing Memory with Delete

Memory allocated with `new` should be returned to the free-store when no longer needed, using the `delete` operator. This practice prevents memory leaks, which can be critical in long-running or large programs.

```c++
double* p = new double[1000];
delete[] p; // Frees the allocated memory


double* pSingle = new double;
delete pSingle; // Frees the allocated single object
```
Some notes:

- Deleting memory twice or deleting uninitialized pointers can lead to errors.
- When deleting an array, dont forget to use `[]`. 
- Attempt to delete pointers as early as possible to prevent memory leaks.
Here is what not to do:

    ```c++
    double* p = new double[1000];
    // good code here
    // code with error here
    delete[] p; // oops didnt delete in time - memory leak
    ```
    Here is an alternative:
    ```c++
    double* p = new double[1000];
    // good code here 
    delete[] p; // phew, we deleted the code before the error.
    // code with error here
   
    ```

And what is a memory leak you ask? In short, say the data you forgot to delete is your SIN, and say you were writing code on a computer at the public library. If a memory leak occurs (say your program crashes before you are able to delete memory), than your SIN will be left unprotected somewhere in the depth of the memory of the computer you were using. This is not only a privacy issue, but the you will also take up space that the computer needs for other programs. Again, stay calm, modern operating systems will make sure this doesn't actually happen - at this point in your learning if you forget to deletem your code will just be "sloppy" and may behave unexpected.


### Automatic Deletion -  Garbage Collection

In C++, memory management is typically manual, but the concept of automatic garbage collection does exist in some contexts. This method allows the system to reclaim memory automatically when it's no longer in use. However, implementing automatic garbage collection in C++ is not straightforward and may not be suitable for all applications. 




## References

We've use the word "reference" alot and now it's time to learn about references. Don't worry, this will be a lot shorter than the pointers section.

References in C++ provide a way to create an alias, or another name for a variable. Unlike pointers, references must be initialized when declared and cannot be null. They provide a more convenient and safer way to work with data.

### Creating References

A reference variable is created with the `&` operator and must be initialized with an existing variable. Here's an example that will cover most of what you need to know:

```c++
int originalValue = 42;
int &aliasValue = originalValue; // reference to originalValue

cout << originalValue << "\n"; // Outputs 42
cout << aliasValue << "\n";     // Outputs 42

aliasValue = 10; // Modifying the reference also modifies the original value
cout << originalValue << "\n"; // Outputs 10
```

Both `originalValue` and `aliasValue` refer to the same underlying data, so changes to one will affect the other.




### Range-Based For Loops and Passing Vectors to Functions

In C++, when you pass an array or vector to a function, it gets automatically converted to a pointer to its first element, losing information about the size of the array. This conversion effectively decays the array into a pointer, making constructs like range-based for loops unusable.

Essentialy, if we were to implement a function like the one below, `numbers` will be treated as a pointer with in the function. As we learned, C++ doesnt know how large an array is that is pointed to be a pointed. That means that a for-each leap like below wouldn't know when to stop:

```c++
void doubleElements(vector<int> numbers) {
    for (int number : numbers) {
        //code
    }
}
```
Similarly, even if we define the parameter to be an array, and specify it's size the code won't run and experience the same problem:
```c++
void doubleElements(int numbers[3]) {
    for (int number : numbers) {
        //code
    }
}
```
The solution is to clarify to the compiler that we want the reference . By passing the array by reference, you preserve the full type information, including the size of the array. This allows the range-based for loop to work correctly:

```c++
void doubleElements(vector<int> &numbers) {
    for (int& number : numbers) {
        number *= 2; // Modifies the original elements
    }
}
```

Here, `doubleElements` expects a reference to a vector<int>, so it operates directly on the vector passed as an argument. Notice we also use the reference operator (`&`) in the loop itself. This indicates that each `number` is a reference to the actual element in the vector, rather than a copy of it.

## Summary

Working with pointers and references brings us closer to the hardware, where we have only a few primitive operations and minimal protection from the language or standard library. While this level of programming can be challenging, it's essential for understanding how higher-level facilities are implemented and for writing specialized code.

There is still more to learn about pointers, references and memory management but for now we have enough new material to work with. 

Make sure to complete the practice problems below before moving on to the next chapter. 


## Practice Problems

1. **Pointer Basics**: Write a function that takes a pointer to an array and the array's size, then doubles each element in the array.
2. **Reference Swap**: Write a function that swaps the values of two integers using references.
3. **Range-Based Loop Modification**: Write a function that takes a vector of integers and uses a range-based for loop with `auto&` to increment each element by a given value.

5. **Math with Pointers**: Write a function that takes two pointers to integers and returns the result of a mathematical operation (e.g., addition, subtraction, multiplication) performed on the values they point to. Use functions from the `cmath` library to perform more complex operations if desired.

6. **File Handling with Pointers**: Write a program that reads numbers from a file and stores them in an array. Then, write a function that takes a pointer to the array and its size, and writes the squared values of the numbers back to a new file. Use the `fstream` library for file handling.

7. **Random Array Allocation**: Write a function that takes an integer `n` as input and returns a pointer to a dynamically allocated array of `n` random integers. Use the `rand()` function from the `cstdlib` library to generate the random numbers, and don't forget to free the memory when done.

8. **Conditional Pointer Manipulation**: Write a function that takes a pointer to an array of integers and the array's size. Use conditional statements to find and replace all even numbers in the array with their half value, and all odd numbers with their double value.



11. **Are strings palindromes**: Write a function that takes a array of strings and returns an array of all the locations of the palindromes. 



## Bibliography
```{bibliography}
:filter: docname in docnames
```