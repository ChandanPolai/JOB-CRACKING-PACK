

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