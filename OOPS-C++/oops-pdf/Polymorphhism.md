**Polymorphism** OOP (Object-Oriented Programming) ka ek important concept hai, jiska mtlb hai ek hi action ko different forms mein perform karna. Polymorphism **multiple forms** mein **functionality** ko represent karta hai. Isse program ko more flexible aur reusable banaya ja sakta hai. Polymorphism ka use karke hum code ko **extend** karte hain bina purani functionality ko change kiye.

### **Types of Polymorphism**:
1. **Compile-time Polymorphism (Static Polymorphism)**
2. **Run-time Polymorphism (Dynamic Polymorphism)**

### **1. Compile-time Polymorphism (Static Polymorphism)**:
Is type mein, polymorphism ko **compile-time** par resolve kiya jata hai. Yeh **function overloading** aur **operator overloading** ke through achieve hota hai.

#### **1.1 Function Overloading**:
Jab ek hi function name ko multiple times use kiya jata hai, par function parameters different hote hain (either in number or type). Compiler ko **during compilation** pata chal jata hai ki kaunsa function call hoga.

- **Example**:
  ```cpp
  #include <iostream>
  using namespace std;

  class Calculator {
  public:
      int add(int a, int b) { return a + b; }  // Function for 2 integers
      double add(double a, double b) { return a + b; }  // Function for 2 doubles
  };

  int main() {
      Calculator calc;
      cout << "Sum of 2 integers: " << calc.add(10, 20) << endl; // Calls int version
      cout << "Sum of 2 doubles: " << calc.add(10.5, 20.5) << endl; // Calls double version
      return 0;
  }
  ```

  **Explanation**:
  - Here, we have two functions named `add()`, one for `int` parameters and another for `double` parameters.
  - The compiler decides at **compile time** which method to call based on the data types of the arguments passed.

#### **1.2 Operator Overloading**:
Operator overloading ka matlab hai ki hum operators ko apne objects ke liye redefine kar sakte hain. Isse, hum operators ko objects ke upar bhi apply kar sakte hain.

- **Example**:
  ```cpp
  #include <iostream>
  using namespace std;

  class Complex {
  private:
      int real, imag;
  public:
      Complex() : real(0), imag(0) {}

      // Overloading '+' operator
      Complex operator + (const Complex& obj) {
          Complex temp;
          temp.real = real + obj.real;
          temp.imag = imag + obj.imag;
          return temp;
      }

      void display() { cout << real << " + " << imag << "i" << endl; }
  };

  int main() {
      Complex num1, num2, sum;
      sum = num1 + num2;  // Calls overloaded '+' operator
      sum.display();
      return 0;
  }
  ```

  **Explanation**:
  - Here, we are overloading the `+` operator to add two `Complex` number objects.
  - The compiler determines at **compile time** how to perform the addition using the overloaded operator.

---

### **2. Run-time Polymorphism (Dynamic Polymorphism)**:
Is type mein polymorphism ko **runtime** par resolve kiya jata hai, jo mainly **method overriding** ke through achieve hota hai. Jab parent class ke method ko child class me override kiya jata hai, tab runtime par decide hota hai ki kis class ka method call hoga.

#### **2.1 Method Overriding**:
Method overriding ka matlab hai ki child class apne parent class ke method ko apne hisaab se redefine kar sakti hai. Jab ek object ka type **runtime** me decide hota hai, tab overridden method ko call kiya jata hai.

- **Example**:
  ```cpp
  #include <iostream>
  using namespace std;

  class Animal {
  public:
      virtual void sound() {
          cout << "Animal makes a sound" << endl;
      }
  };

  class Dog : public Animal {
  public:
      void sound() override {  // Overriding the sound() method
          cout << "Dog barks" << endl;
      }
  };

  int main() {
      Animal* animalPtr;
      Dog dog;
      
      animalPtr = &dog;
      animalPtr->sound();  // Calls Dog's overridden sound() method
      return 0;
  }
  ```

  **Explanation**:
  - Here, the `sound()` method in the `Animal` class is overridden in the `Dog` class.
  - **Runtime** me, jab `animalPtr` ko `dog` object se assign kiya jata hai, tab **dynamic polymorphism** ke through `Dog` class ka method `sound()` call hota hai, na ki `Animal` class ka.
  - Yeh `virtual` keyword ki wajah se hota hai, jisse **dynamic dispatch** enable hota hai.

---

### **Key Concepts**:

1. **Virtual Functions**:
   - Virtual functions wo functions hote hain jo parent class me **declare** kiye jaate hain aur child class me unhe **override** kiya jaata hai.
   - Yeh **runtime polymorphism** ko enable karte hain.
   
   **Example**:
   - `sound()` method ko virtual function bana kar, hum ensure karte hain ki jab parent class pointer se child class ka object call ho, tab overridden method call ho.

2. **Pure Virtual Functions**:
   - Agar parent class me ek function ko **pure virtual** declare kiya gaya ho, toh usse child class me implement karna mandatory ho jata hai.
   - Aise function ko `= 0` se define kiya jata hai.

   **Example**:
   ```cpp
   class Shape {
   public:
       virtual void draw() = 0;  // Pure virtual function
   };

   class Circle : public Shape {
   public:
       void draw() override {
           cout << "Drawing Circle" << endl;
       }
   };
   ```

---

### **Polymorphism ka Use**:
1. **Code Reusability**:
   - Polymorphism se hum apne code ko reuse kar sakte hain bina naye classes likhe, bas method ko override karke.

2. **Extensibility**:
   - Polymorphism ki wajah se aap naye behaviors ko easily add kar sakte hain, bina purane code ko modify kiye.

3. **Flexible Code**:
   - Agar aapko object types ko dynamically change karna ho toh polymorphism help karta hai.

---

### **Summary**:
- **Polymorphism** ka mtlb hai ek hi action ko different forms me perform karna.
- **Compile-time polymorphism** me function ya operator overloading hoti hai, jo **compile time** par resolve hoti hai.
- **Run-time polymorphism** me method overriding hoti hai, jo **run time** par decide hoti hai.



**Polymorphism** is an important concept in Object-Oriented Programming (OOP), which means performing the same action in different forms. Polymorphism represents functionality in multiple forms, making the program more flexible and reusable. By using polymorphism, we can extend the functionality of code without changing its existing behavior.

### **Types of Polymorphism**:
1. **Compile-time Polymorphism (Static Polymorphism)**
2. **Run-time Polymorphism (Dynamic Polymorphism)**

### **1. Compile-time Polymorphism (Static Polymorphism)**:
This type of polymorphism is resolved **at compile-time**. It is achieved through **function overloading** and **operator overloading**.

#### **1.1 Function Overloading**:
When a function is used multiple times with different parameters (either in number or type). The compiler decides at **compile time** which function to call based on the parameters passed.

- **Example**:
  ```cpp
  #include <iostream>
  using namespace std;

  class Calculator {
  public:
      int add(int a, int b) { return a + b; }  // Function for 2 integers
      double add(double a, double b) { return a + b; }  // Function for 2 doubles
  };

  int main() {
      Calculator calc;
      cout << "Sum of 2 integers: " << calc.add(10, 20) << endl; // Calls int version
      cout << "Sum of 2 doubles: " << calc.add(10.5, 20.5) << endl; // Calls double version
      return 0;
  }
  ```

  **Explanation**:
  - Here, we have two functions named `add()`, one for `int` parameters and another for `double` parameters.
  - The compiler decides at **compile time** which method to call based on the data types of the arguments passed.

#### **1.2 Operator Overloading**:
Operator overloading means we can redefine operators for our custom objects. This allows us to use operators on objects, just like we use them for basic data types.

- **Example**:
  ```cpp
  #include <iostream>
  using namespace std;

  class Complex {
  private:
      int real, imag;
  public:
      Complex() : real(0), imag(0) {}

      // Overloading '+' operator
      Complex operator + (const Complex& obj) {
          Complex temp;
          temp.real = real + obj.real;
          temp.imag = imag + obj.imag;
          return temp;
      }

      void display() { cout << real << " + " << imag << "i" << endl; }
  };

  int main() {
      Complex num1, num2, sum;
      sum = num1 + num2;  // Calls overloaded '+' operator
      sum.display();
      return 0;
  }
  ```

  **Explanation**:
  - Here, we are overloading the `+` operator to add two `Complex` number objects.
  - The compiler resolves which operator to call at **compile time** based on the operands.

---

### **2. Run-time Polymorphism (Dynamic Polymorphism)**:
This type of polymorphism is resolved **at runtime**, typically through **method overriding**. When a method in the parent class is overridden by the child class, the method to be called is decided **at runtime**.

#### **2.1 Method Overriding**:
Method overriding means that a child class can redefine a method that was already defined in its parent class. When an object’s type is determined **at runtime**, the overridden method is called.

- **Example**:
  ```cpp
  #include <iostream>
  using namespace std;

  class Animal {
  public:
      virtual void sound() {
          cout << "Animal makes a sound" << endl;
      }
  };

  class Dog : public Animal {
  public:
      void sound() override {  // Overriding the sound() method
          cout << "Dog barks" << endl;
      }
  };

  int main() {
      Animal* animalPtr;
      Dog dog;
      
      animalPtr = &dog;
      animalPtr->sound();  // Calls Dog's overridden sound() method
      return 0;
  }
  ```

  **Explanation**:
  - The `sound()` method in the `Animal` class is overridden in the `Dog` class.
  - **At runtime**, when the `animalPtr` is assigned the address of `dog`, the **dynamic polymorphism** mechanism calls the `sound()` method from the `Dog` class instead of the `Animal` class.
  - This happens because of the `virtual` keyword, which enables **dynamic dispatch**.

---

### **Key Concepts**:

1. **Virtual Functions**:
   - Virtual functions are those functions that are declared in the parent class and are overridden in the child class.
   - They enable **runtime polymorphism**.

   **Example**:
   - By marking the `sound()` method as virtual, we ensure that when the parent class pointer calls a child class object, the overridden method is called.

2. **Pure Virtual Functions**:
   - A pure virtual function is a function that is declared in the parent class but must be implemented in the child class.
   - It is defined by appending `= 0` to the function declaration.

   **Example**:
   ```cpp
   class Shape {
   public:
       virtual void draw() = 0;  // Pure virtual function
   };

   class Circle : public Shape {
   public:
       void draw() override {
           cout << "Drawing Circle" << endl;
       }
   };
   ```

---

### **Polymorphism Use Cases**:
1. **Code Reusability**:
   - Polymorphism allows us to reuse code by overriding methods without rewriting the entire codebase.

2. **Extensibility**:
   - Polymorphism allows us to easily add new behaviors to a program without modifying existing code.

3. **Flexible Code**:
   - If you need to change object types dynamically, polymorphism makes it easier to do so.

---

### **Summary**:
- **Polymorphism** means performing the same action in different forms.
- **Compile-time polymorphism** involves function or operator overloading, which is resolved at **compile time**.
- **Run-time polymorphism** involves method overriding, which is resolved at **runtime**.




### Virtual Functions in C++: Detailed Explanation

Virtual functions are an important feature of Object-Oriented Programming (OOP) that allow us to achieve **runtime polymorphism**. To understand this in detail, let's break down the concepts of virtual functions and pure virtual functions.

### **1. Virtual Functions**:
A **virtual function** is a function defined in the base class (parent class) that can be overridden by derived classes (child classes). The main purpose of a virtual function is to support **dynamic method dispatch**, i.e., the decision of which function to call is made at runtime rather than compile time.

### **Why Use Virtual Functions?**
Without virtual functions, when we use pointers or references of base class type to call a function, the function of the base class will be called even if the object is of the derived class. Virtual functions allow us to override a base class function in the derived class and ensure that the **derived class function** is called, even when using a base class pointer/reference.

### **How Virtual Functions Work**:
When a function is declared as virtual in the base class, and the derived class overrides that function, C++ uses a mechanism called a **vtable** (virtual table) to resolve which function to call. The vtable is created at runtime, allowing the correct function (overridden in the child class) to be called.

### **Example: Virtual Function**

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    // Declaring the function as virtual
    virtual void sound() {
        cout << "Animal makes a sound" << endl;
    }
};

class Dog : public Animal {
public:
    // Overriding the base class function
    void sound() override {
        cout << "Dog barks" << endl;
    }
};

int main() {
    Animal* animal;  // Pointer to base class
    Dog dog;         // Object of derived class
    
    animal = &dog;   // Pointing base class pointer to derived class object
    animal->sound(); // Calls the overridden method in the Dog class

    return 0;
}
```

### **Explanation**:
- **Virtual Function in Base Class**: The function `sound()` is declared as `virtual` in the base class `Animal`.
- **Overriding in Derived Class**: The `Dog` class overrides the `sound()` function to provide a different implementation.
- **Polymorphism**: When we use the `Animal*` pointer to point to a `Dog` object and call `sound()`, the **`Dog` class's version of the function is called**, not the `Animal` class's version, because the function is virtual.

### **How Does It Work at Runtime?**
At runtime, when the `sound()` function is called using a pointer to the base class (`Animal* animal`), C++ looks up the vtable for the class of the object (in this case, `Dog`). The vtable holds the addresses of the overridden methods in derived classes, ensuring the correct function is called.

---

### **2. Pure Virtual Functions**:
A **pure virtual function** is a function declared in the base class but has no implementation. It is defined by using `= 0` in its declaration. Any class containing a pure virtual function becomes an **abstract class**, and you cannot instantiate objects of that class. Pure virtual functions must be overridden in derived classes.

### **Why Use Pure Virtual Functions?**
The purpose of pure virtual functions is to create a common interface for all derived classes while forcing each derived class to provide its own implementation of that function.

### **Example: Pure Virtual Function**

```cpp
#include <iostream>
using namespace std;

class Shape {
public:
    // Pure virtual function
    virtual void draw() = 0;  
};

class Circle : public Shape {
public:
    // Overriding pure virtual function
    void draw() override {
        cout << "Drawing Circle" << endl;
    }
};

class Square : public Shape {
public:
    // Overriding pure virtual function
    void draw() override {
        cout << "Drawing Square" << endl;
    }
};

int main() {
    Shape* shape;  // Pointer to abstract class (Shape)

    Circle circle;
    Square square;

    shape = &circle;
    shape->draw(); // Calls draw() method of Circle

    shape = &square;
    shape->draw(); // Calls draw() method of Square

    return 0;
}
```

### **Explanation**:
- **Pure Virtual Function**: The function `draw()` is declared as a pure virtual function in the `Shape` class, indicated by `= 0`.
- **Abstract Class**: `Shape` becomes an abstract class because it contains a pure virtual function.
- **Overriding**: The derived classes `Circle` and `Square` override the `draw()` function to provide their own implementations.
- **Dynamic Dispatch**: At runtime, based on the object assigned to the `Shape*` pointer, the appropriate `draw()` method is called.

### **Why Use Pure Virtual Functions?**
- **Enforce Implementation**: Every derived class must implement the pure virtual function, ensuring that all derived classes provide specific implementations for the function.
- **Abstract Base Class**: Helps create a general interface for derived classes, while each derived class can provide its own specific behavior.

---

### **Key Differences Between Virtual Functions and Pure Virtual Functions**:
| **Feature**                 | **Virtual Function**                      | **Pure Virtual Function**                          |
|-----------------------------|-------------------------------------------|----------------------------------------------------|
| **Definition**               | Function with implementation in the base class. | Function without implementation in the base class (i.e., abstract). |
| **Implementation**           | Can have a body in the base class.        | Cannot have a body in the base class (must be overridden). |
| **Instantiability of Base Class** | Base class can be instantiated.         | Base class cannot be instantiated (it is abstract). |
| **Overriding in Derived Class** | Can be overridden in derived class.      | Must be overridden in derived class.               |
| **Usage**                    | Provides default behavior, but allows overriding. | Forces derived classes to implement the function. |

---

### **Summary**:
- **Virtual Functions**: Allow derived classes to override functions from base classes and ensure the correct function is called at runtime.
- **Pure Virtual Functions**: Declare an interface in the base class that must be implemented by derived classes, making the base class abstract and enforcing method overrides in child classes.
- Both concepts are used to implement **runtime polymorphism** in C++.

### **Benefits**:
1. **Flexibility**: Virtual and pure virtual functions allow you to write more flexible and reusable code.
2. **Design Patterns**: These concepts are widely used in design patterns, such as Factory, Strategy, and Observer, where base classes define common interfaces, and derived classes provide specific implementations.

