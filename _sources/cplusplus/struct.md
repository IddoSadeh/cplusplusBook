# Chapter: Structs and Enums

## Introduction

Structs, or structures, are a way to group variables under a single name. They are simpler versions of classes and can be incredibly useful for organizing data. In this chapter, we will explore what structs are and how to use them effectively.

```cpp
using namespace std;
```

## Defining Structs

To define a struct, you use the `struct` keyword followed by the name you wish to give to this new type and its elements enclosed in braces.

```cpp
struct Person {
    string name;
    int age;
};
```

## Creating Struct Instances

You can instantiate a struct similarly to how you instantiate a class.

```cpp
Person john;
john.name = "John";
john.age = 30;
```

Or, using a constructor-like syntax:

```cpp
Person john = {"John", 30};
```

## Accessing Struct Members

Accessing the members of a struct is straightforward; you use the dot (`.`) operator.

```cpp
cout << "Name: " << john.name << ", Age: " << john.age << endl;
```

## Structs vs Classes

The key differences between structs and classes are:

- By default, members of a struct are `public` while members of a class are `private`.
- Structs are generally used for passive objects that hold data, while classes have both data and functions.

## Nested Structs

Structs can be nested within other structs.

```cpp
struct Address {
    string street;
    string city;
};

struct Employee {
    string name;
    Address address;
};
```

## Structs and Functions

You can pass structs as arguments to functions and return them.

```cpp
void printPersonInfo(Person p) {
    cout << "Name: " << p.name << ", Age: " << p.age << endl;
}

Person createPerson() {
    Person p;
    p.name = "Alice";
    p.age = 25;
    return p;
}
```

## Summary

- **Struct**: A simple way to group variables under a single name.
- **Defining**: Use `struct` followed by the name and elements.
- **Instantiation**: Create an instance using the struct name.
- **Accessing Members**: Use the dot (`.`) operator to access struct members.
- **Structs vs Classes**: Structs are simpler and their members are public by default.
- **Nested Structs**: One struct can be nested within another.
- **Structs and Functions**: Can be passed as arguments and returned from functions.



### Practice Problems

#### Problem 1: Basic Structs

Define a struct named `Book` with three fields: title (string), author (string), and pages (int). Create an instance of the struct, set its fields, and print them out.

#### Problem 2: Structs and Functions

Write a function that takes a `Person` struct (from the chapter example) as a parameter and prints out the information in a formatted manner. Use this function in your `main()`.

#### Problem 3: Conditional Structs

Write a program that takes an array of `Book` structs. Use a loop and conditionals to find and print the book with the most pages.

#### Problem 4: Structs and Pointers

Modify the `Book` struct to include a pointer to another book. Make it so that you can create a sequence of books where each book points to the next one. Traverse the sequence using pointers.

#### Problem 5: Nested Structs and References

Use the `Employee` and `Address` structs from the chapter. Write a function that takes an `Employee` struct by reference and updates the city in the address. Verify that the original `Employee` object is updated.

#### Problem 6: Dynamic Structs

Dynamically allocate an array of `Person` structs using the `new` operator. Fill in the details for each person and then deallocate the memory using `delete`.

#### Problem 7: Structs, Enums, and Control Structures

Define an enum for account types (Savings, Current, Joint). Add this enum to the `BankAccount` struct. Write a switch-case statement that processes an array of `BankAccount` structs differently based on the account type.

#### Problem 8: Polymorphism with Structs

Create a `Vehicle` struct with a virtual function `fuelEfficiency()`. Create derived structs `Car` and `Bike` and override the function. Create an array of pointers to `Vehicle` and use it to call `fuelEfficiency()` polymorphically.

#### Problem 9: Operator Overloading

Overload the `==` and `<` operators for the `Book` struct. The `==` should compare the titles and the `<` should compare the number of pages.

#### Problem 10: Structs and I/O

Create a function that reads a list of `Person` structs from a file and another function that writes a list of `Person` structs to a file.

---

These problems should give you a good mix of challenges involving structs and various other C++ topics.