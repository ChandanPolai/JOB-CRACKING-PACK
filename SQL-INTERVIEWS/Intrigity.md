### **SQL Integrity**  
SQL me **integrity** ka matlab hai database ke data ki correctness, consistency, aur reliability ko ensure karna. Data integrity kaafi zaruri hota hai taaki database me inaccurate, incomplete, ya duplicate data store na ho.

---

### **Types of Data Integrity in SQL**  

1. **Entity Integrity**  
   - **Definition:** Ye ensure karta hai ki table ke har row ka ek unique identifier (primary key) ho.  
   - **Rule:** Primary Key null nahi ho sakti aur har row ke liye unique honi chahiye.  
   - **Example:**
     ```sql
     CREATE TABLE students (
         student_id INT PRIMARY KEY,  -- Unique and non-null
         name VARCHAR(100)
     );
     ```

2. **Referential Integrity**  
   - **Definition:** Ye ensure karta hai ki tables ke beech relationships consistent rahein. Foreign key ke values parent table ki primary key se match honi chahiye.  
   - **Rule:** Foreign key null ho sakti hai ya parent table ki primary key ke saath match karni chahiye.  
   - **Example:**
     ```sql
     CREATE TABLE orders (
         order_id INT PRIMARY KEY,
         customer_id INT,
         FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
     );
     ```
     - Agar `customer_id` kisi customer table me nahi hai, to insert/update allowed nahi hoga.  

3. **Domain Integrity**  
   - **Definition:** Ye ensure karta hai ki columns ke values allowed range ya domain ke andar ho.  
   - **Rule:** Constraints jaise **NOT NULL**, **CHECK**, aur data types use karke enforce hoti hai.  
   - **Example:**
     ```sql
     CREATE TABLE employees (
         emp_id INT PRIMARY KEY,
         age INT CHECK (age > 18),  -- Age should be greater than 18
         salary DECIMAL(10, 2) NOT NULL  -- Salary cannot be null
     );
     ```

4. **User-Defined Integrity**  
   - **Definition:** Ye custom rules set karta hai jo specific business logic ko enforce karte hain.  
   - **Rule:** Triggers ya stored procedures ke zariye implement hoti hai.  
   - **Example:**
     ```sql
     CREATE TRIGGER validate_salary
     BEFORE INSERT ON employees
     FOR EACH ROW
     BEGIN
         IF NEW.salary < 10000 THEN
             SIGNAL SQLSTATE '45000'
             SET MESSAGE_TEXT = 'Salary must be at least 10000';
         END IF;
     END;
     ```

---

### **Why SQL Integrity is Important?**
1. **Data Accuracy:** Galat ya duplicate data ko avoid karta hai.  
2. **Data Consistency:** Tables ke relationships consistent rahte hain.  
3. **Error Reduction:** Logical mistakes aur inconsistencies ko kam karta hai.  
4. **Reliable Queries:** Jo data store hota hai wo trusted hota hai, isliye queries ke results bhi accurate hote hain.  

---

### **Use Cases of Integrity in SQL**
1. **Entity Integrity:**
   - Ensuring unique identifiers in systems like student roll numbers or employee IDs.  
2. **Referential Integrity:**
   - Maintaining relationships between orders and customers.  
3. **Domain Integrity:**
   - Validating salary, age, or any input constraints.  
4. **User-Defined Integrity:**
   - Enforcing complex business logic, like discounts applicable on specific product categories.

---

### **Problems Without Integrity Rules**  
- Duplicate data (e.g., multiple rows with the same primary key).  
- Invalid relationships (e.g., an order linked to a non-existent customer).  
- Logical errors (e.g., age less than 0).  
- Data inconsistencies across related tables.

---

### **Conclusion**
SQL integrity ensures a well-structured and reliable database by enforcing rules through **primary keys**, **foreign keys**, **constraints**, and **triggers**. Ye data ko consistent aur error-free banata hai, jo kisi bhi database system ke liye essential hota hai.