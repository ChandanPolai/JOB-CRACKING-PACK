

| **Concept**                | **Definition**                                                                 | **Example**                                                                                      |
|----------------------------|-------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|
| **Encapsulation**           | Data ko class ke andar wrap karna, private/protected banake secure rakhna.    | `BankAccount` class ke andar `balance` aur `withdraw()` method ko secure rakhna.               |
| **Abstraction**             | Sirf essential details dikhana, unnecessary complexity ko chhupana.           | `Car` ka `startEngine()` method, internal implementation hide hota hai.                        |
| **Inheritance**             | Parent class ke features ko child class me reuse karna.                       | `Animal` class se `Dog` aur `Cat` inherit karna.                                               |
| **Polymorphism**            | Same name ke methods ka alag behavior ho sakta hai.                           | Method overriding aur dynamic binding (`draw()` for `Circle` and `Square`).                    |
| **Association**             | Ek object ka dusre object ke saath loosely connected hona.                    | `Teacher` aur `Student` ka ek class ke andar relation.                                         |
| **Composition**             | "Part-of" relationship, dependent objects.                                    | `Car` class ke andar `Engine` object (car bina engine nahi chalti).                            |
| **Aggregation**             | "Has-a" relationship, independent objects.                                    | `Team` class ke andar `Player` objects (players bina team exist karte hain).                   |
| **Dependency**              | Ek class temporarily dusri class ke method ka use kare.                       | `Order` class ka `PaymentGateway` ke process method ko call karna.                             |
| **Generalization**          | Ek generic class jo specific subclasses inherit karti hain.                   | `Animal` class se `Dog` aur `Cat`.                                                             |
| **Realization**             | Ek class kisi interface ko implement karke behavior define karti hai.         | `Vehicle` interface me `Car` aur `Bike` ka apna method `drive()`.                              |
| **Message Passing**         | Objects ke beech communication via methods.                                   | `User` class me `sendMessage()` method se message bhejna.                                       |
| **Static Binding**          | Compile-time par decide hota hai method call.                                 | `Animal a; a.staticBinding();`                                                                 |
| **Dynamic Binding**         | Runtime par decide hota hai method call.                                      | `Animal* a = new Dog(); a->dynamicBinding();`                                                  |
| **Overloading**             | Same method name, alag arguments.                                             | `add(int a, int b)` aur `add(double a, double b)`.                                             |
| **Overriding**              | Parent class ke method ko child class me redefine karna.                      | `show()` method ko Parent aur Child class me alag tarike se implement karna.                   |
| **Delegation**              | Ek class apna kaam dusri class ke object ko pass kar deti hai.                | `Printer` class printing ke liye `FileManager` se data leti hai.                               |

---

Yeh table tumhare interview preparation ke liye helpful rahega! Kisi specific concept me doubt ho to batao, aur detail me explain karunga. 😊

Haan, **virtual class** ka concept bhi hota hai, lekin **virtual class** ek alag concept hai jo **virtual inheritance** se related hota hai. Isse samajhne ke liye, humein **inheritance** aur **virtual inheritance** ke baare mein thoda samajhna padega.

### **Virtual Class in C++ (Virtual Inheritance)**:

1. **Virtual Inheritance** ka use tab hota hai jab ek class do ya zyada base classes se inherit karti hai, aur dono base classes apne common **parent class** ko inherit kar rahi hoti hain.
   
2. Agar hum **normal inheritance** use karte hain, to dono base classes apne **parent class** ka alag-alag copy bana deti hain. Yeh problem create kar sakta hai, jise **diamond problem** kehte hain.

3. **Virtual inheritance** ka use karke hum **diamond problem** ko solve kar sakte hain. Yeh ensure karta hai ki common parent class ka **sirf ek copy** ho, na ki multiple copies.

---

### **Virtual Class (Virtual Inheritance) Example:**

```cpp
#include <iostream>
using namespace std;

class A {
public:
    void show() {
        cout << "Class A" << endl;
    }
};

class B : virtual public A {  // Virtual inheritance
public:
    void showB() {
        cout << "Class B" << endl;
    }
};

class C : virtual public A {  // Virtual inheritance
public:
    void showC() {
        cout << "Class C" << endl;
    }
};

class D : public B, public C {
public:
    void showD() {
        cout << "Class D" << endl;
    }
};

int main() {
    D obj;
    obj.show();  // This will call A's show() function (only one copy)
    obj.showB();  // Calls B's showB() function
    obj.showC();  // Calls C's showC() function
    obj.showD();  // Calls D's showD() function
    return 0;
}
```

### **Explanation:**
- **Class A** is inherited by both **Class B** and **Class C** using **virtual inheritance**.
- **Class D** inherits both **B** and **C**, and since **B** and **C** are virtually inheriting from **A**, **Class D** will have only **one copy of Class A**.
- **show()** from **Class A** will be called only once, avoiding the diamond problem.

### **Key Points**:
- **Virtual Inheritance** ka use tab hota hai jab ek class ko multiple inheritance se access hota hai, aur unke common parent ko **ek hi copy** mein access karwana hota hai.
- **Diamond problem** ko avoid karne ke liye virtual inheritance ka use kiya jata hai.

---

**Conclusion:**
- **Virtual class** ek aisa class nahi hota, balki yeh **virtual inheritance** ka part hota hai, jo multiple inheritance ke case mein common parent class ki ek hi copy ko access karne ke liye use hota hai.