# Object-Oriented Programming

In this chapter, we will explore the paradigm of Object-Oriented Programming (OOP) in C++. OOP is a cornerstone of modern software development, allowing for code that is both modular and reusable. Although the concept might seem daunting at first, mastering OOP will open new dimensions in how you approach programming problems.

By the end of this chapter, you should be able to:
- Understand the key principles of Object-Oriented Programming: encapsulation, inheritance, and polymorphism.
- Define and use classes and objects in your C++ programs.
- Implement encapsulation through access specifiers and getter/setter methods.
- Grasp the importance and utility of operator overloading.
- Understand how inheritance and polymorphism allow for extensible and maintainable code.



## Table of Contents:
```{contents}
```


## Classes and Objects

Imagine you're a software developer for a local bank, tasked with creating a system to manage customer accounts. Previously, you've used variables to store individual pieces of data like names, account numbers, and balances. However, it's quickly becoming a headache to manage these separate variables for each customer. What you need is a more efficient way to bundle these variables together and attach relevant functionalities like depositing and withdrawing money.

Welcome to the world of classes and objects, your solution to these complex scenarios. When programming becomes complex, and you need a "container" that can hold multiple types of data and even functions, that's when classes come into play. In essence, a class acts as a blueprint for creating such complex variables, which we refer to as "objects."  In this section, we will walk you through building a `BankAccount` class that will serve as the backbone of our bank management system.

### Defining Classes

In a C++ program, you can define a class either within the main code file or in a separate file with a `.h` or `.cpp` extension. Placing classes in separate files is common when the codebase becomes larger, but for small programs or learning exercises, defining them in the main code file is often sufficient.

The class body holds the members of the class, which can be variables or functions. The keyword `public` defines what can be accessed from outside the class. Later we will learn about other keywords so we can control what can be accessed form the class.

In our example we will start of by creating the basic structure of our class:

```cpp
class BankAccount {
public:
    // Class body here
};
```

If you're following along with your code editor, you should have a file that looks like this:

```cpp
#include <iostream>
using namespace std;

class BankAccount {
public:
    
};

int main(){

}

```

Great! We've now set up a basic structure for our banking software.

### Member Variables and Functions

Now let's make our class useful by adding common data a bank account may need to remember and functionalities a customer may need:


```cpp
class BankAccount {
public:
    string accountNumber;
    string accountHolder;
    double balance;

    void deposit(double amount) {
        balance += amount;
    }

    void withdraw(double amount) {
        if (amount <= balance) {
            balance -= amount;
        } else {
            cout << "Insufficient funds" << endl;
        }
    }
};
```
In our banking example, the class now has three member variables: `accountNumber`, `accountHolder`, and `balance`. We've also added two member functions, `deposit()` and `withdraw()`, to handle basic banking operations.

### Constructors and Destructors

When a new account is created at the bank, there's a specific procedure to follow: identification checks, initial deposit, and so on. Constructors in a class serve a similar purpose; they are functions that are called when an object is created. They usually initialize member variables.

We usually also create destructors which erase the object from memory if needed, think of the destructor as the procedure you'd follow when closing the account.

A class can have multiple constructors. Each constructor initializes objects in different ways. A constructor without parameters is called a default constructor. 

```cpp
public:
    // default constructor
    BankAccount() { 
        balance = 0.0;
        accountNumber = "Undefined";
        accountHolder = "Undefined";
    }
    
    BankAccount(double initialBalance, string acctNumber, string holder) {
        balance = initialBalance;
        accountNumber = acctNumber;
        accountHolder = holder;
    }
    
    ~BankAccount() {
        // Destructor to clean up resources, if any.
    }

```


### Instantiating Objects

With the blueprint ready, it's time to create an account. We can now treat a `BankAccount` object very similar to a `int` or `string` variable. 

Creating a new bank account is as simple as writing:

```cpp
int main(){
    BankAccount myAccount;
}
```

Since we haven't saved anything to `myAccount`, it will use the instructions from our default constructor for intilization. i.e. running the following code will print `0` and `Undefined`:

```cpp
cout << myAccount.balance << endl;
cout << myAccount.accountNumber << endl;
```

You may have noticed that we used the notation `myAccount.balance`, this is called the dot operator and it is used to access member function and variables.

Other uses of the dot operator may look like:

```cpp
myAccount.balance = 100.0;
myAccount.deposit(50);  // Increases balance to 150.0
myAccount.withdraw(20); // Decreases balance to 130.0

```

This may look familiar, we have infact seen the dot operator before when learning about strings. `string` is essentialy a class which stores a list of `char` variables, and therefore it has functionalaties as with our bank account class. 

Unlike strings, when you create our own class, if you want to instantiate a object with your own data, you do it by utilizing the non default constructor you wrote as follows:

```cpp
BankAccount anotherAccount(500.0, "12345", "Jane Doe");
```




## Encapsulation and Abstraction

In the previous section, we allowed all member functions and variables to be accessed anywhere in our codebase by using the `public` keyword.

As your banking software grows more complex, you realize you don't want it to be so easy to directly access a customer's balance or account number for security reasons. This concept of hiding the internal details of the class and only exposing what is necessary is known as encapsulation.

### Access Specifiers

You can restrict access to certain parts of your `BankAccount` class by using the `private` keyword. For example:

```cpp
class BankAccount {
private:
    double balance;
public:
    string accountNumber;
    string accountHolder;
    // ... rest of the code
};
```

But why is this useful? Say we **don't** use the `private` keyword and the customer interacts with the bank through the `main()` function as follows:

```cpp
int main(){
    // customer A creates a new account with our bank with an initial deposit of $500:
    BankAccount accountA(500.0, "12345", "Jane Doe"); 
    // customer A wants to withdraw money to buy a playstation:
    accountA.withdraw(650); 
    // The customer finds that he has insufficient funds
    // The customer really wants the playstation so they find a security breach. They will just change their balance without anyone knowing:
    accountA.balance = 1000;
    // now the customer can withdraw the money they need:
    accountA.withdraw(650); 
}
```

The bank will be angry when they find out a customer has more money in there account then they ever deposited. It is our ethical responsibility to make this impossible. We do this by using the `private` keyword to restrict access to member variable `balance`. 
Doing so will make the code above would throw an error when we try to access the `balance` in the `main` function.


### Getter and Setter Functions

Restricting access to `balance` has another issue, what if the customer just want's to see how much money they have? They can't do that anymore with the state of our code.

So, how can we securely access the balance? This is where getter and setter functions come in. A getter function allows us to view data from within an object, setter functions allow us to change data within an object. In our code these functions will be:

```cpp
public:
    double getBalance() {
        return balance;
    }

     void deposit(double amount) {
        balance += amount;
    }

    void withdraw(double amount) {
        if (amount <= balance) {
            balance -= amount;
        } else {
            cout << "Insufficient funds" << endl;
        }
    }

```

Note, that this code is still with in the scope of the class definition, hence `private` members can still be accessed.

### Reducing Complexity with an Interface

As your codebase grows, you realize that your `BankAccount` class is getting too complicated and unreadable. To manage this complexity, you decide to separate the code in to separate files. You decided to transition your code base from one file `main.cpp` to utilize source files and header files.

#### Using Source Files

If you chose to use a source file, you would define the class and implement its member functions within a single `.cpp` file. Any other `.cpp` files that wanted to use this class would need to include a declaration of the class and its members.

Here's how your single `.cpp` file for the `BankAccount` class might look like:

##### BankAccount.cpp
```cpp
#include <iostream>
#include <string>
using namespace std;

class BankAccount {
private:
    double balance;
public:
    string accountNumber;
    string accountHolder;
    
    BankAccount() {
        balance = 0.0;
        accountNumber = "Undefined";
        accountHolder = "Undefined";
    }
    
    BankAccount(double initialBalance, string acctNumber, string holder) {
        balance = initialBalance;
        accountNumber = acctNumber;
        accountHolder = holder;
    }
    
    double getBalance() {
        return balance;
    }

    void deposit(double amount) {
        balance += amount;
    }

    void withdraw(double amount) {
        if (amount <= balance) {
            balance -= amount;
        } else {
            cout << "Insufficient funds" << endl;
        }
    }
};

// Main function to test the class
int main() {
    BankAccount myAccount;
    myAccount.deposit(100);
    cout << "Balance after deposit: " << myAccount.getBalance() << endl;
    myAccount.withdraw(50);
    cout << "Balance after withdrawal: " << myAccount.getBalance() << endl;

    return 0;
}
```

##### AnotherFile.cpp (that wants to use `BankAccount`)
```cpp
#include <iostream>
#include <string>
using namespace std;

// You would need to declare the class again here
class BankAccount {
private:
    double balance;
public:
    string accountNumber;
    string accountHolder;
    BankAccount();
    BankAccount(double initialBalance, string acctNumber, string holder);
    double getBalance();
    void deposit(double amount);
    void withdraw(double amount);
};

int main() {
    // Usage of BankAccount
    BankAccount anotherAccount(500, "12345", "Jane Doe");
    anotherAccount.deposit(100);
    cout << "Balance: " << anotherAccount.getBalance() << endl;
    
    return 0;
}
```

As you can see, if you choose to use a source file, you would need to declare the class `BankAccount` again in every `.cpp` file that uses it. Even though we have not included the implementation in `AnotherFile.cpp`, the necessity to include the declarations everywhere could be a maintainability issue as the project grows. This is where interfaces come in.

#### What Are Header Files and Why Use Them?

In programming, an interface serves as a contract that defines the interactions or functions that are available for a particular class or module. The interface lists function declarations but doesn't contain any information about how these functions are implemented. When you look at an interface, you see what a class can do, not how it does it.

Header files effectively serve as the "interface" of your class. They contain the function prototypes (declarations) and data members but not the actual implementation of the functions, which goes into the `.cpp` files.

By adhering to this structure, your code becomes more modular, maintainable, and easier to read, setting a strong foundation for scalable software development.



#### Current Codebase Layout
If you kept everything we learned in this chapter in a single file (let's call it `main.cpp`), it should look like this:

```cpp
#include <iostream>
#include <string>
using namespace std;

class BankAccount {
private:
    double balance;
public:
    string accountNumber;
    string accountHolder;

    double getBalance() {
        return balance;
    }

    void deposit(double amount) {
        balance += amount;
    }

    void withdraw(double amount) {
        if (amount <= balance) {
            balance -= amount;
        } else {
            cout << "Insufficient funds" << endl;
        }
    }
};

int main() {
    // Some example usage
    BankAccount account;
    account.deposit(100);
    cout << "Balance: " << account.getBalance() << endl;
}
```

#### New Codebase Layout with Separate `.h` and `.cpp` files

Now, let's break this code into separate `.h` and `.cpp` files to reduce the complexity. We will now have three files in our program:

- **BankAccount.h** (Header file containing the blueprint)
- **BankAccount.cpp** (Source file containing the construction details)
- **main.cpp** (Main file to run code)

##### BankAccount.h
The `.h` file usually contains only declarations, not implementations. It serves as an interface to your class.

```cpp
// BankAccount.h

#include <iostream>
#include <string>
using namespace std;

class BankAccount {
private:
    double balance;
public:
    string accountNumber;
    string accountHolder;

    double getBalance();  // Declaration only
    void deposit(double amount);  // Declaration only
    void withdraw(double amount);  // Declaration only
};
```

##### BankAccount.cpp
This `.cpp` file includes `BankAccount.h` and provides the actual implementations of the `BankAccount` methods.

```cpp
// BankAccount.cpp

#include "BankAccount.h"

double BankAccount::getBalance() {
    return balance;
}

void BankAccount::deposit(double amount) {
    balance += amount;
}

void BankAccount::withdraw(double amount) {
    if (amount <= balance) {
        balance -= amount;
    } else {
        cout << "Insufficient funds" << endl;
    }
}
```

##### main.cpp
Finally, your `main.cpp` file will include `BankAccount.h` and proceed as normal.

```cpp
// main.cpp

#include <iostream>
#include "BankAccount.h"  // Include the header file

int main() {
    BankAccount account;  // Create a BankAccount object
    account.deposit(100);  // Use its methods
    cout << "Balance: " << account.getBalance() << endl;  // Output should be "Balance: 100"
}
```

#### Some Notes
Notice we only declared `using namespace std;` in our header file. Every `.cpp` file the includes a `.h` file that has the code `using namespace std;` forces that `using` directive on the `.cpp` file that includes the `.h` file. This is generally bad practice as it can lead to name clashes. 

On the topic of good and bad practice, we generally also want to include gaurds in our header file. These gaurds would look like this:
```cpp
#ifndef BANKACCOUNT_H  // If BANKACCOUNT_H has not been defined yet
#define BANKACCOUNT_H  // Define BANKACCOUNT_H

// Your actual class definition and other code go here

#endif // Close the ifndef condition
```

In this example:

- The `#ifndef BANKACCOUNT_H` checks if `BANKACCOUNT_H` has been defined.
- If it has not been defined, the code proceeds to the `#define BANKACCOUNT_H`, defining `BANKACCOUNT_H`.
- The actual code for the class and other functionalities is written after this.
- Finally, `#endif` closes the conditional inclusion.

Essentially, when the compiler encounters this header file for the first time, `BANKACCOUNT_H` will not be defined, so it defines it and includes the rest of the file. If our code ends up having subsequent inclusions of `BankAccount.h`, `BANKACCOUNT_H` will already be defined, so the compiler will skip to the `#endif`, effectively ignoring the contents of the header file, thus preventing multiple inclusions.

As such, if you wan't to keep your code well written it should now look like this:

##### BankAccount.h
```cpp
// BankAccount.h
#ifndef BANKACCOUNT_H  // If BANKACCOUNT_H has not been defined yet
#define BANKACCOUNT_H  // Define BANKACCOUNT_H

#include <iostream>
#include <string>

class BankAccount {
private:
    double balance;
public:
    std::string accountNumber;
    std::string accountHolder;

    double getBalance();  // Declaration only
    void deposit(double amount);  // Declaration only
    void withdraw(double amount);  // Declaration only
};

#endif // Close the ifndef condition
```

##### BankAccount.cpp
```cpp
// BankAccount.cpp
#include "BankAccount.h" // Include the header file

using namespace std; // This is okay here, because it's a source file

double BankAccount::getBalance() {
    return balance;
}

void BankAccount::deposit(double amount) {
    balance += amount;
}

void BankAccount::withdraw(double amount) {
    if (amount <= balance) {
        balance -= amount;
    } else {
        cout << "Insufficient funds" << endl;
    }
}

```

##### main.cpp
```cpp
// main.cpp
#include <iostream>
#include "BankAccount.h"  // Include the header file

using namespace std; // This is okay here, because it's a source file

int main() {
    BankAccount account;  // Create a BankAccount object
    account.deposit(100);  // Use its methods
    cout << "Balance: " << account.getBalance() << endl;  // Output should be "Balance: 100"
}

```

## Operator Overloading

In practical applications like this one, you might frequently find yourself needing to print account details or compare bank accounts. Using operator overloading can streamline these repetitive tasks, making your code easier to read and manage.


### What Is Operator Overloading?

In C++, operators like `+`, `-`, `==`, and others are pre-defined for built-in data types like `int`, `double`, and `string`. But what if you want these operators to work with user-defined classes like `BankAccount`? This is where operator overloading comes into play. You can redefine or "overload" the built-in operators to perform specific operations for your custom types.

For example, the `==` operator is used to compare integers, floating-point numbers, or even strings. By overloading this operator, you can define what it means for two `BankAccount` objects to be "equal" (e.g., having the same account number).

Similarly, the `<<` operator is commonly used for output streams to display built-in types. You can overload this operator to easily print out the details of a `BankAccount` object.

### How Does It Work?

Overloading an operator involves defining a function that provides the new behavior for the operator. The function's name is constructed using the keyword `operator` followed by the symbol you want to overload. For instance, `operator==` for overloading the `==` operator or `operator<<` for overloading the `<<` operator.


### Integrating Overloaded Operators in Source and Header Files

To maintain the modular structure of your code, it's best to define these overloaded operators in the appropriate header and source files.
With the following changes, your application will support intuitive comparison and straightforward printing of `BankAccount` objects, enhancing both its usability and maintainability.

#### Updating `BankAccount.h`

In your `BankAccount.h` file, declare the overloaded operators like so:

```cpp
// BankAccount.h

#ifndef BANKACCOUNT_H
#define BANKACCOUNT_H

#include <iostream>
#include <string>

using namespace std;

class BankAccount {
private:
    double balance;
public:
    string accountNumber;
    string accountHolder;
    
    double getBalance();
    void deposit(double amount);
    void withdraw(double amount);

    // Declaration for the overloaded equality operator
    friend bool operator==(const BankAccount& a, const BankAccount& b);
    
    // Declaration for the overloaded stream output operator
    friend ostream& operator<<(ostream &output, const BankAccount &account);
};

#endif
```

#### Updating `BankAccount.cpp`

In your `BankAccount.cpp` file, provide the implementations of these overloaded operators:

```cpp
// BankAccount.cpp

#include "BankAccount.h"

// Existing method implementations...

bool operator==(const BankAccount& a, const BankAccount& b) {
    return a.accountNumber == b.accountNumber;
}

ostream& operator<<(ostream &output, const BankAccount &account) {
    output << "Account Number: " << account.accountNumber;
    return output;
}
```

#### Using the Overloaded Operators in `main.cpp`

Finally, you can use these overloaded operators in your `main.cpp`:

```cpp
// main.cpp

#include <iostream>
#include "BankAccount.h"

int main() {
    BankAccount account1(100, "123", "Alice");
    BankAccount account2(200, "456", "Bob");

    // Using the overloaded equality operator
    if (account1 == account2) {
        cout << "Both accounts are the same.\n";
    } else {
        cout << "The accounts are different.\n";
    }

    // Using the overloaded stream output operator
    cout << "Details of account1: " << account1 << endl;
    cout << "Details of account2: " << account2 << endl;

    return 0;
}
```




## Inheritance and Polymorphism


As your bank's services grow, so do the types of accounts it offers. Adding entirely new classes for each account type—Savings, Current, and Joint—would lead to a lot of duplicated code. Inheritance allows you to create new types of accounts that inherit common functionalities from the `BankAccount` class, thereby promoting code reuse.

Similarly, polymorphism enables these different account types to provide their own specialized behaviors (like displaying monthly statements) without altering the code that interacts with them. This makes the system more extensible and easier to maintain.

### Inheritance: The Basics

Inheritance is a feature in object-oriented programming where a new class inherits properties and behavior (methods) from an existing class. The existing class is known as the "base class," and the new class is known as the "derived class."

#### Creating Derived Classes

In C++, you create a derived class using the `:` symbol followed by an access specifier (`public`, `protected`, `private`) and the name of the base class. Let's create a `SavingsAccount` class that adds an interest rate feature.

```cpp
class SavingsAccount : public BankAccount {
public:
    double interestRate;
};
```

### Polymorphism: Dynamic Behavior

Polymorphism allows objects of different types to be treated as objects of a common type. One way to achieve polymorphism in C++ is through the use of virtual functions.

#### Virtual Functions and Dynamic Dispatch

Imagine the bank wants a feature where any type of account can display its own version of a monthly statement. You can declare a virtual function in the base class and then override it in each derived class. 

In the `BankAccount` class:

```cpp
public:
    virtual void displayMonthlyStatement() {
        cout << "General account statement.";
    }
```

Now, in derived classes, you can provide specialized implementations for this function.

### Safeguarding Polymorphism: `override` and `final` Specifiers

Errors can occur when implementing polymorphism. For instance, you may accidentally mistype the function signature in the derived class, leading to unexpected behaviors. The `override` and `final` specifiers serve as safeguards.

#### Using the `override` Specifier

The `override` specifier ensures that the function in the derived class correctly overrides a virtual function in the base class.

In the `SavingsAccount` class:

```cpp
public:
    void displayMonthlyStatement() override {
        cout << "Savings account statement.";
    }
```

Using `override` prompts the compiler to check if this function indeed overrides a function in the base class, catching any errors early.
#### Using the `final` Specifier
Sometimes, you may want to restrict further overriding of a virtual function in derived classes. This can be useful for ensuring that certain behaviors defined in a derived class stay consistent and aren't altered unintentionally in future subclasses. The `final` specifier in C++ allows you to indicate that a virtual function should not be overridden in derived classes.

For example, let's say that the `SavingsAccount` class should be the last in the inheritance chain to modify the `displayMonthlyStatement()` method. We can specify this method as `final`.

```cpp
#include "BankAccount.h"

class SavingsAccount : public BankAccount {
public:
    double interestRate;

    void displayMonthlyStatement() override final;  // Notice the 'final' keyword
};
```

Now, if someone tries to derive a new class from `SavingsAccount` and attempts to override `displayMonthlyStatement()`, the compiler will generate an error, preventing this action. This ensures that the behavior defined for `displayMonthlyStatement()` in `SavingsAccount` remains consistent and isn't inadvertently modified by subclasses.

### New Codebase Layout with Inheritance and Polymorphism

With the concepts of inheritance and polymorphism in mind, let's extend our codebase to include multiple types of accounts and to enable dynamic behavior. We'll start with header files and source files for the base class and the derived class.

#### BankAccount.h

This remains largely the same as before but now includes a virtual function for displaying monthly statements.

```cpp
// BankAccount.h

#include <iostream>
#include <string>
using namespace std;

class BankAccount {
private:
    double balance;
public:
    string accountNumber;
    string accountHolder;

    virtual double getBalance();
    void deposit(double amount);
    void withdraw(double amount);
    virtual void displayMonthlyStatement();
};
```

#### BankAccount.cpp

Same as before, but with the implementation of the new virtual function.

```cpp
// BankAccount.cpp

#include "BankAccount.h"

// ... Previous method implementations ...

void BankAccount::displayMonthlyStatement() {
    cout << "General account statement." << endl;
}
```

#### SavingsAccount.h

This is our new derived class with an extra field for interest rate.

```cpp
// SavingsAccount.h

#include "BankAccount.h"

class SavingsAccount : public BankAccount {
public:
    double interestRate;

    void displayMonthlyStatement() override final;
};
```

#### SavingsAccount.cpp

Here we provide the specific implementation for displaying a monthly statement for a savings account.

```cpp
// SavingsAccount.cpp

#include "SavingsAccount.h"

void SavingsAccount::displayMonthlyStatement() {
    cout << "Savings account statement. Interest rate: " << interestRate << "%" << endl;
}
```
#### SuperSavingsAccount.cpp
If you were to try to create another class that inherits from `SavingsAccount` and tries to override the `displayMonthlyStatement()` method, you'd get a compile-time error.
```cpp
// SuperSavingsAccount.cpp
// This will produce a compile-time error
class SuperSavingsAccount : public SavingsAccount {
public:
    void displayMonthlyStatement() override {  // Error because the method is marked as 'final' in SavingsAccount
        cout << "Super Savings account statement.";
    }
};
```
The `final` specifier ensures that critical functionality in a base or derived class cannot be modified further, safeguarding your code's integrity.
#### main.cpp
A practical example showing inheritance and polymorphism in action.

```cpp
// main.cpp

#include <iostream>
#include "BankAccount.h"
#include "SavingsAccount.h"

int main() {
    BankAccount genericAccount;
    SavingsAccount savingsAccount;

    // Set interest rate for savings account
    savingsAccount.interestRate = 2.5;

    // Declare a BankAccount pointer and use it for dynamic dispatch
    BankAccount* accountPtr;

    // Point it to genericAccount
    accountPtr = &genericAccount;
    accountPtr->displayMonthlyStatement();  // Output: "General account statement."

    // Now point it to savingsAccount
    accountPtr = &savingsAccount;
    accountPtr->displayMonthlyStatement();  // Output: "Savings account statement. Interest rate: 2.5%"

    return 0;
}
```


This layout shows how your codebase would evolve to incorporate the new object-oriented concepts of inheritance and polymorphism.


## Summary

### Class and Object Basics
- **Class**: A blueprint for creating objects. Defined using the `class` keyword.
- **Object**: An instance of a class.
- **Instantiating Objects**: Creating an instance of a class using its constructor.

### Constructors and Destructors
- **Constructor**: Special function that gets called when an object is instantiated.
  - **Default Constructor**: A constructor that takes no arguments.
  - **Parameterized Constructor**: A constructor that takes one or more arguments.
- **Destructor**: Special function that gets called when an object is destroyed.

### Access Specifiers
- **Public**: Accessible from anywhere.
- **Private**: Accessible only within the class.
- **Protected**: Accessible within the class and its subclasses.

### Member Functions and Variables
- Functions and variables that are part of a class.

### Code Structure
- **Header Files**: Declare classes, functions, and variables. Serve as an interface.
- **Source Files**: Contain implementations of functions declared in header files.

### Interfaces
- Define what methods a class should have but not how they are implemented.

### #include Guards
- `#ifndef`, `#define`, and `#endif`: Used to prevent double inclusion of header files.

### Operator Overloading
- Allows you to redefine the meaning of operators for user-defined types.
- Example for `==`: `bool operator==(const ClassName& a, const ClassName& b);`

### Stream Operators
- `<<` for output and `>>` for input can be overloaded to handle user-defined types.

### Inheritance
- Allows a class to use methods and variables of an existing class.
- Use `public` keyword to specify inheritance.

### Polymorphism
- **Virtual Functions**: Allow a function in the base class to be overridden in the derived class.
- **Dynamic Dispatch**: The ability to call the correct function implementation at runtime, based on the object's actual type.
- **Override Specifier**: Ensures the function is meant to override a virtual function in the base class.
- **Final Specifier**: Prevents further overriding of a method in future derived classes.


## Practice Problems

1. **Create Your Own Class**: Design a class representing a `Student` with fields for name, grade, and GPA. Implement this in separate header and source files.

2. **Implement Operator Overloading**: For the `Student` class, overload the `==` operator to compare students by GPA.

3. **Implement Stream Operators**: Overload the `<<` and `>>` operators to output and input `Student` information, respectively.

4. **Inheritance Exercise**: Create a `HighSchoolStudent` class that inherits from the `Student` class and adds a field for the high school name.

5. **Polymorphism Exercise**: Add a virtual function `displayInfo()` in the `Student` class and override it in the `HighSchoolStudent` class to display student information differently.

6. **Final Specifier**: Modify the `HighSchoolStudent` class such that it is the last class in the inheritance chain that can modify the `displayInfo()` method.
