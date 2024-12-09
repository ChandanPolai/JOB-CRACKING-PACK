### **Encapsulation: Introduction**

Encapsulation is one of the four key pillars of Object-Oriented Programming (OOP). It refers to the concept of **binding data (variables)** and the **methods (functions)** that operate on that data together into a single unit called a class. Additionally, encapsulation helps in **hiding the internal details** of an object from the outside world and only exposing what is necessary.

---

### **Key Features of Encapsulation**
1. **Data Hiding**: Encapsulation hides the implementation details (using `private` or `protected` access specifiers).
2. **Controlled Access**: Access to class data is controlled through **getter** and **setter** methods.
3. **Improved Maintainability**: Encapsulation keeps the code modular and manageable.
4. **Security**: Encapsulation ensures that sensitive data cannot be accessed or modified directly.

---

### **How Encapsulation is Implemented?**
Encapsulation is implemented through:
1. **Access Specifiers**: 
   - `private`, `protected`, `public`
   - These control the visibility of class members.
   
2. **Getter and Setter Methods**:  
   - To provide controlled access to private variables.  

---

### **Topics Within Encapsulation**

#### 1. **Data Hiding**  
   - Prevents external access to class data directly.  
   - Access is granted only through methods.

   **Example**:  
   ```cpp
   class BankAccount {
       private:
           double balance; // Data hidden from outside
       public:
           void setBalance(double amount) { // Controlled access
               if (amount >= 0) {
                   balance = amount;
               }
           }
           double getBalance() { // Read-only access
               return balance;
           }
   };

   int main() {
       BankAccount account;
       account.setBalance(1000); // Access through setter
       cout << "Balance: " << account.getBalance(); // Access through getter
       return 0;
   }
   ```

---

#### 2. **Access Specifiers**  
Encapsulation heavily relies on access specifiers for restricting access. These define the visibility of data within the class:
   - **Private**: Data accessible only within the class.  
   - **Protected**: Accessible in derived classes too.  
   - **Public**: Accessible everywhere.

   **Example**:  
   ```cpp
   class Example {
       private:
           int privateVar; // Not directly accessible outside the class
       protected:
           int protectedVar; // Accessible in derived classes
       public:
           int publicVar; // Accessible everywhere
   };
   ```

---

#### 3. **Getter and Setter**  
Encapsulation ensures controlled access through getter and setter methods. 

   **Example**:
   ```cpp
   class Student {
       private:
           string name;
           int age;
       public:
           void setName(string n) {
               name = n;
           }
           string getName() {
               return name;
           }
           void setAge(int a) {
               if (a > 0) age = a; // Validation
           }
           int getAge() {
               return age;
           }
   };
   ```

---

#### 4. **Constructor and Encapsulation**  
Encapsulation is also achieved using constructors to initialize private data at the time of object creation.

   **Example**:
   ```cpp
   class Employee {
       private:
           string empName;
           int empID;
       public:
           Employee(string name, int id) {
               empName = name;
               empID = id;
           }
           void display() {
               cout << "Name: " << empName << ", ID: " << empID << endl;
           }
   };

   int main() {
       Employee emp("John Doe", 101);
       emp.display();
       return 0;
   }
   ```

---

### **Types of Encapsulation**  
Encapsulation is often classified based on how it's applied in code:

1. **Member Encapsulation**:  
   Protecting individual class variables using private/protected.  

2. **Class Encapsulation**:  
   Bundling data and methods within a class.  

3. **Object Encapsulation**:  
   Encapsulation applied at the object level, controlling how objects interact with each other.

---

### **Encapsulation Connection with Other Pillars of OOPS**

#### 1. **Encapsulation and Abstraction**  
   - Encapsulation **hides the internal data** by restricting access.  
   - Abstraction focuses on **hiding implementation details** and only exposing functionality.
   - **Example**: A car class hides the working of the engine (encapsulation) but provides methods like `startCar()` (abstraction).

#### 2. **Encapsulation and Inheritance**  
   - Protected members allow derived classes to reuse and modify encapsulated data.  
   - **Example**: Base class has private data, but derived class can access through protected methods.

#### 3. **Encapsulation and Polymorphism**  
   - Encapsulation ensures private data is accessed only through specific methods. Polymorphism allows these methods to have multiple implementations in derived classes.  

---

### **Benefits of Encapsulation**
1. **Code Security**: Private members protect sensitive information.
2. **Code Flexibility**: Changes in the implementation don’t affect external code.
3. **Improved Readability**: Well-defined access methods make code easier to understand.

---

### **Real-Life Example**
A **smartphone** is an example of encapsulation:  
- **Private data**: Hardware details like processors, circuits.  
- **Public methods**: Apps or UI for interacting with the phone.  
- Encapsulation ensures the user interacts with the phone without worrying about the internal workings.

---


### **Constructor and Destructor in OOPS**

---

### **1. Constructor**
**Definition**:  
A constructor is a special method used to initialize the data members of a class. It is automatically called when an object is created.  

**Features**:  
- **Automatic invocation**: No need to call explicitly.  
- **Same name as the class**.  
- **No return type**, not even `void`.  
- Used to set initial values for object attributes.

---

**Types of Constructors**:  
1. **Default Constructor**:  
   - Automatically provided if no constructor is defined.  
   - Initializes members with default values.  
   **Example**:  
   ```cpp
   class Student {
   public:
       int age;
       Student() { // Default constructor
           age = 18;
       }
   };
   Student s1; // Default constructor is invoked.
   ```

2. **Parameterized Constructor**:  
   - Accepts parameters to initialize members.  
   **Example**:  
   ```cpp
   class Student {
   public:
       int age;
       Student(int a) { // Parameterized constructor
           age = a;
       }
   };
   Student s1(21); // Constructor with parameter is invoked.
   ```

3. **Copy Constructor**:  
   - Creates a new object by copying an existing object.  
   **Example**:  
   ```cpp
   class Student {
   public:
       int age;
       Student(const Student &s) { // Copy constructor
           age = s.age;
       }
   };
   Student s1(21);
   Student s2(s1); // Copy constructor is invoked.
   ```

---

### **2. Destructor**
**Definition**:  
A destructor is a special method called automatically when an object goes out of scope or is deleted. Its purpose is to release resources or perform cleanup tasks.

**Features**:  
- Same name as the class, preceded by a tilde (`~`).  
- Automatically invoked when the object is destroyed.  
- No return type or parameters.  
- Used to free memory, close files, or release other system resources.

**Example**:  
```cpp
class Student {
public:
    ~Student() { // Destructor
        cout << "Object destroyed";
    }
};
Student s1; // Destructor called when `s1` goes out of scope.
```

---

### **Constructor vs Destructor**
| **Feature**         | **Constructor**                   | **Destructor**                   |
|----------------------|-----------------------------------|-----------------------------------|
| **Purpose**          | Initializes object attributes.    | Cleans up resources.             |
| **Invocation**       | Called when object is created.    | Called when object is destroyed. |
| **Parameters**       | Can have parameters.              | No parameters.                   |
| **Return Type**      | No return type.                   | No return type.                  |

---

### **Which OOPS Pillar Includes These?**
- **Constructor**: Comes under **Encapsulation**, as it initializes private/protected data in a controlled manner.  
- **Destructor**: Also falls under **Encapsulation**, as it ensures proper cleanup of resources.  

---

### **Use Cases** (Hinglish Explanation):  
1. **Constructor**:
   - Jab object banate ho aur turant kuch values initialize karni ho.  
   - Example: Bank account ka balance set karna.  
   ```cpp
   Account acc1(5000); // Constructor balance set karega.
   ```

2. **Destructor**:
   - Jab memory, file, ya resources free karni ho object ke destroy hone pe.  
   - Example: File close karna.  
   ```cpp
   FileHandler f;
   // Destructor ensure karega file close ho jaye.
   ```
### **Real-World Use Cases of Constructor and Destructor**

---

### **1. Constructor: Practical Use Cases**

**Why it is Needed?**  
Constructors help **initialize objects with predefined values** or **set up the environment** needed for an object to function properly.

#### **Examples**:

1. **Bank Account Initialization**:  
   - Jab ek bank account create hota hai, uska **account number**, **balance**, aur **user details** automatically set karna hota hai.  
   ```cpp
   class BankAccount {
   public:
       string accountNumber;
       double balance;
       BankAccount(string accNo, double bal) { // Parameterized Constructor
           accountNumber = accNo;
           balance = bal;
       }
   };
   BankAccount acc("12345", 1000.0); // Constructor se account initialize.
   ```

2. **Game Character Setup**:  
   - Game mein player ka naam, health, aur level set karna.  
   ```cpp
   class Player {
   public:
       string name;
       int health;
       Player(string playerName, int playerHealth) {
           name = playerName;
           health = playerHealth;
       }
   };
   Player p("Warrior", 100); // Constructor automatically invoke hota hai.
   ```

3. **Database Connection**:  
   - Constructor ka use database connection open karne ke liye hota hai.  
   ```cpp
   class Database {
   public:
       Database() { // Default Constructor
           cout << "Database connection opened!" << endl;
       }
   };
   Database db; // Connection open as object is created.
   ```

---

### **2. Destructor: Practical Use Cases**

**Why it is Needed?**  
Destructors ensure **cleanup** of resources like memory, files, or connections when an object is no longer needed.

#### **Examples**:

1. **File Handling**:  
   - File open karne ke baad ensure karna ki close bhi ho.  
   ```cpp
   class FileHandler {
   public:
       ~FileHandler() { // Destructor
           cout << "File closed!" << endl;
       }
   };
   {
       FileHandler fh; // File opened.
   } // Destructor automatically called to close file.
   ```

2. **Memory Cleanup**:  
   - Jab dynamic memory allocation hoti hai, destructor ensure karta hai ki memory leak na ho.  
   ```cpp
   class Array {
   private:
       int* arr;
   public:
       Array(int size) {
           arr = new int[size]; // Allocate memory.
       }
       ~Array() {
           delete[] arr; // Free memory.
           cout << "Memory cleaned up!" << endl;
       }
   };
   Array a(10); // Memory allocated and then released.
   ```

3. **Network Connections**:  
   - Server ya API connections close karne ke liye.  
   ```cpp
   class Network {
   public:
       ~Network() { // Destructor
           cout << "Network connection closed!" << endl;
       }
   };
   Network conn; // Automatically closes connection.
   ```

---

### **Real-Life Analogy (Hinglish)**:
1. **Constructor**: 
   - Imagine a **new car delivery**. The constructor is like setting up the car with fuel, tires, and keys when it's delivered.  
   - Without the constructor, car ready nahi hoti.

2. **Destructor**: 
   - Jab car ko service ke baad garage se wapas lete ho aur ensure karte ho ki engine off aur parking brake laga diya gaya hai. Destructor ensures everything is cleaned up before shutting down.

---

### **Why They Are Useful?**
1. **Constructor** ensures objects are initialized **properly** with necessary values, reducing errors.  
2. **Destructor** ensures resources like memory or files are **properly released**, avoiding leaks or corruption.

---

Chalo step by step samajhte hain. Pehle **pointer** ka concept samajhte hain, phir uske baad **deep copy aur shallow copy** explain karte hain, real-life examples ke sath.  

---

## **1. Pointers: What Are They?**  
Pointer ek variable hota hai jo kisi aur variable ke memory address ko store karta hai. Matlab yeh ek "address holder" hota hai.  

### **English Explanation**:  
- Instead of holding a value like a normal variable, a pointer "points to" the memory address where the value is stored.  
- This helps in working with memory directly.  

---

### **Basic Example (English + Hinglish)**:
```cpp
int a = 10;       // A normal integer variable
int* p = &a;      // 'p' is a pointer that stores the address of 'a'

cout << "Value of a: " << a << endl;      // Outputs: 10
cout << "Address of a: " << &a << endl;   // Memory location of 'a'
cout << "Value stored in p: " << p << endl;  // Same address as &a
cout << "Value pointed by p: " << *p << endl; // Dereferencing p, outputs: 10
```

- **`int* p;`**: Means `p` is a pointer that can hold the address of an integer.  
- **`&a`**: Means "address of a".  
- **`*p`**: Means "value at the address `p` is pointing to" (called dereferencing).  

---

### **Real-Life Analogy**:
Imagine a pointer is like a house address written on a piece of paper.  
- **Normal variable**: The actual house.  
- **Pointer**: The paper with the house address.  
- **Dereferencing**: Using the paper to visit the house and get the contents inside.  

---

## **2. Shallow Copy and Deep Copy**  

When you copy an object, there are two ways it can happen:
1. **Shallow Copy**: Copies the reference (address) of the data.  
2. **Deep Copy**: Creates a new independent copy of the actual data.  

---

### **Shallow Copy**  
- **Definition**: Only the pointer's address is copied, so both objects share the same data.  
- **Issue**: Changes in one object affect the other.  

### **Example**:
```cpp
class Shallow {
public:
    int* data;
    Shallow(int val) {
        data = new int(val); // Dynamically allocate memory
    }
    ~Shallow() {
        delete data; // Free the memory
    }
};

int main() {
    Shallow obj1(5);     // obj1 points to a memory containing 5
    Shallow obj2 = obj1; // obj2 points to the same memory as obj1

    *(obj2.data) = 10;   // Changing obj2 affects obj1 as well
    cout << *(obj1.data); // Output: 10
}
```

**Real-Life Analogy**:  
Imagine two people sharing the same phone number. If one changes the number, the other automatically gets affected.  

---

### **Deep Copy**  
- **Definition**: Copies the data itself into a new memory location.  
- **Advantage**: Changes in one object don't affect the other.  

### **Example**:
```cpp
class Deep {
public:
    int* data;
    Deep(int val) {
        data = new int(val); // Dynamically allocate memory
    }
    Deep(const Deep& obj) { // Deep copy constructor
        data = new int(*(obj.data)); // Allocate new memory and copy value
    }
    ~Deep() {
        delete data; // Free the memory
    }
};

int main() {
    Deep obj1(5);         // obj1 points to a memory containing 5
    Deep obj2 = obj1;     // obj2 gets a new memory with the same value

    *(obj2.data) = 10;    // Changing obj2 does not affect obj1
    cout << *(obj1.data); // Output: 5
    cout << *(obj2.data); // Output: 10
}
```

**Real-Life Analogy**:  
Imagine two people having their own separate phone numbers. Changing one does not impact the other.  

---

## **3. Key Differences Between Shallow and Deep Copy**

| **Aspect**        | **Shallow Copy**                                | **Deep Copy**                                |
|--------------------|-------------------------------------------------|----------------------------------------------|
| **Definition**     | Copies the address (reference) of the data.    | Creates a new copy of the data in memory.    |
| **Memory Sharing** | Both objects share the same memory location.   | Each object has its own memory location.     |
| **Impact**         | Changes in one affect the other.               | Changes in one don't affect the other.       |
| **Complexity**     | Faster but risky (data corruption).            | Slower but safe (data isolation).            |

---

### **Use Cases**:
1. **Shallow Copy**: Used when copying large datasets to save memory and you are okay with shared changes.  
   - Example: Copying references in a program with a read-only dataset.  

2. **Deep Copy**: Used when you need data independence and data security.  
   - Example: Duplicating a customer object in a banking system where each copy should be isolated.  

---



Bilkul bhai, yeh lo examples:

### 1. **Friend Function**:
**Definition**: Friend function ek aisa function hota hai jo kisi class ke private aur protected members ko access kar sakta hai, even though wo class ka member nahi hota.

**Example**:
```cpp
#include <iostream>
using namespace std;

class Box {
private:
    int length;

public:
    Box() : length(10) {}  // Constructor

    // Friend function declaration
    friend void printLength(Box& b);
};

// Friend function definition
void printLength(Box& b) {
    cout << "Length of box: " << b.length << endl;  // Accessing private member
}

int main() {
    Box b;
    printLength(b);  // Calling friend function
    return 0;
}
```
**Explanation**: `printLength()` ek friend function hai jo `Box` class ke private variable `length` ko access kar raha hai, even though wo class ka part nahi hai.

---

### 2. **Friend Class**:
**Definition**: Friend class ek aisi class hoti hai jo doosri class ke private aur protected members ko access kar sakti hai.

**Example**:
```cpp
#include <iostream>
using namespace std;

class Box;  // Forward declaration

class Display {
public:
    void showLength(Box& b);  // Declaration of function
};

class Box {
private:
    int length;

public:
    Box() : length(20) {}  // Constructor

    // Making Display class a friend
    friend class Display;
};

// Friend class method
void Display::showLength(Box& b) {
    cout << "Length of box: " << b.length << endl;  // Accessing private member
}

int main() {
    Box b;
    Display d;
    d.showLength(b);  // Calling friend class function
    return 0;
}
```

**Explanation**: `Display` class ko `Box` class ka friend banaya gaya hai, isliye `Display` class ka `showLength()` method `Box` class ke private variable `length` ko access kar sakta hai.

---


