SQL me **relationships** ka matlab hai tables ke beech ka connection ya association. Yeh relationships **relational databases** ka core feature hain, jisme alag-alag tables ko logically ek doosre se connect kiya jaata hai.

### **Types of Relationships in SQL:**

#### 1. **One-to-One Relationship**
   - Ek record ek table me sirf ek record ke saath linked hota hai doosre table me.
   - Example:
     - **Use Case**: Ek user ke ek hi profile detail ho sakti hai.
     - Tables:
       - `Users (user_id, name)`
       - `Profiles (profile_id, user_id, bio)`
   - **Query**:
     ```sql
     SELECT Users.name, Profiles.bio
     FROM Users
     INNER JOIN Profiles ON Users.user_id = Profiles.user_id;
     ```

#### 2. **One-to-Many Relationship**
   - Ek record ek table me multiple records ke saath linked ho sakta hai doosre table me.
   - Example:
     - **Use Case**: Ek customer ke multiple orders ho sakte hain.
     - Tables:
       - `Customers (customer_id, name)`
       - `Orders (order_id, customer_id, product)`
   - **Query**:
     ```sql
     SELECT Customers.name, Orders.product
     FROM Customers
     INNER JOIN Orders ON Customers.customer_id = Orders.customer_id;
     ```

#### 3. **Many-to-Many Relationship**
   - Ek table ke multiple records doosre table ke multiple records ke saath linked hote hain.
   - Example:
     - **Use Case**: Students aur courses ke beech ka relation (ek student multiple courses kar sakta hai aur ek course multiple students ke liye ho sakta hai).
     - Tables:
       - `Students (student_id, name)`
       - `Courses (course_id, course_name)`
       - **Bridge Table**: `Enrollments (student_id, course_id)`
   - **Query**:
     ```sql
     SELECT Students.name, Courses.course_name
     FROM Students
     INNER JOIN Enrollments ON Students.student_id = Enrollments.student_id
     INNER JOIN Courses ON Enrollments.course_id = Courses.course_id;
     ```

#### 4. **Self-Referencing Relationship**
   - Ek table apne hi records ke saath linked hota hai.
   - Example:
     - **Use Case**: Employees aur unke managers ka relation.
     - Table:
       - `Employees (employee_id, name, manager_id)`
   - **Query**:
     ```sql
     SELECT E1.name AS Employee, E2.name AS Manager
     FROM Employees E1
     LEFT JOIN Employees E2 ON E1.manager_id = E2.employee_id;
     ```

---

### **Use Cases of SQL Relationships:**
1. **E-commerce Systems**: Products aur Orders ka relation (One-to-Many).
2. **School/College Database**: Students aur Courses ka relation (Many-to-Many).
3. **Social Media**: Users aur Profiles ka relation (One-to-One).
4. **Employee Management**: Employees aur Managers ka relation (Self-Referencing).

### **Importance of Relationships:**
- Data redundancy ko reduce karta hai.
- Data ko logically organize karta hai.
- Query execution aur analysis ko easy banata hai.