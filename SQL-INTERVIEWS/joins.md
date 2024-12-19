

## **Joins in SQL**
### **Definition**:  
SQL Joins ka use hota hai **dono tables ke data ko combine karne ke liye**, jaha rows ek doosre ke saath kuch common column ke basis pe match karti hain. Joins ka use tab hota hai jab aap relational databases ke tables me se related data ko fetch karna chahte ho.

---

### **Types of Joins**:  
1. **INNER JOIN**  
2. **LEFT JOIN (LEFT OUTER JOIN)**  
3. **RIGHT JOIN (RIGHT OUTER JOIN)**  
4. **FULL JOIN (FULL OUTER JOIN)**  
5. **CROSS JOIN**  
6. **SELF JOIN**  

---

## **1. INNER JOIN**  
- **Definition**:  
  INNER JOIN sirf un rows ko dikhata hai jo **dono tables ke beech match karti hain**. Non-matching rows ignore ho jati hain.

- **Use Case**:  
  Jab tumhe **sirf matching data chahiye**, jaise "Kaunse customers ne order diya hai?"  

- **Example Tables**:  
  **Customers**:  
  | Customer_ID | Name  |  
  |-------------|-------|  
  | 1           | Ram   |  
  | 2           | Shyam |  
  | 3           | Mohan |  

  **Orders**:  
  | Order_ID | Customer_ID |  
  |----------|-------------|  
  | 101      | 1           |  
  | 102      | 2           |  

- **Query**:  
  ```sql
  SELECT Customers.Name, Orders.Order_ID
  FROM Customers
  INNER JOIN Orders
  ON Customers.Customer_ID = Orders.Customer_ID;
  ```
- **Result**:  
  | Name  | Order_ID |  
  |-------|----------|  
  | Ram   | 101      |  
  | Shyam | 102      |  

---

## **2. LEFT JOIN (LEFT OUTER JOIN)**  
- **Definition**:  
  LEFT JOIN left table ke **sabhi rows dikhata hai**, chahe right table me match ho ya na ho. Agar match nahi hota, toh NULL dikhata hai.

- **Use Case**:  
  Jab tumhe **left table ka pura data chahiye**, aur dekhna ho ki kaunse rows right table me nahi hain.  
  Example: "Kaunse customers ne order nahi diya?"  

- **Example Tables**:  
  **Customers**:  
  | Customer_ID | Name  |  
  |-------------|-------|  
  | 1           | Ram   |  
  | 2           | Shyam |  
  | 3           | Mohan |  

  **Orders**:  
  | Order_ID | Customer_ID |  
  |----------|-------------|  
  | 101      | 1           |  
  | 102      | 2           |  

- **Query**:  
  ```sql
  SELECT Customers.Name, Orders.Order_ID
  FROM Customers
  LEFT JOIN Orders
  ON Customers.Customer_ID = Orders.Customer_ID;
  ```
- **Result**:  
  | Name  | Order_ID |  
  |-------|----------|  
  | Ram   | 101      |  
  | Shyam | 102      |  
  | Mohan | NULL     |  

---

## **3. RIGHT JOIN (RIGHT OUTER JOIN)**  
- **Definition**:  
  RIGHT JOIN right table ke **sabhi rows dikhata hai**, chahe left table me match ho ya na ho. Agar match nahi hota, toh NULL dikhata hai.

- **Use Case**:  
  Jab tumhe **right table ka pura data chahiye**, aur dekhna ho ki left table me kaunse rows missing hain.  
  Example: "Kaunse orders aise hain jinka customer record nahi hai?"  

- **Example Tables**:  
  **Customers**:  
  | Customer_ID | Name  |  
  |-------------|-------|  
  | 1           | Ram   |  
  | 2           | Shyam |  

  **Orders**:  
  | Order_ID | Customer_ID |  
  |----------|-------------|  
  | 101      | 1           |  
  | 102      | 2           |  
  | 103      | 3           |  

- **Query**:  
  ```sql
  SELECT Customers.Name, Orders.Order_ID
  FROM Customers
  RIGHT JOIN Orders
  ON Customers.Customer_ID = Orders.Customer_ID;
  ```
- **Result**:  
  | Name  | Order_ID |  
  |-------|----------|  
  | Ram   | 101      |  
  | Shyam | 102      |  
  | NULL  | 103      |  

---

## **4. FULL JOIN (FULL OUTER JOIN)**  
- **Definition**:  
  FULL JOIN dono tables ke **sabhi rows dikhata hai**, chahe match ho ya na ho. Non-matching rows NULL ke saath dikhayi jati hain.

- **Use Case**:  
  Jab tumhe **poora data chahiye** dono tables ka, aur dekhna ho ki kaunse rows match nahi karte.  
  Example: "Kaunse customers ka order nahi hai aur kaunse orders ka customer nahi hai?"

- **Example Tables**:  
  **Customers**:  
  | Customer_ID | Name  |  
  |-------------|-------|  
  | 1           | Ram   |  
  | 2           | Shyam |  
  | 3           | Mohan |  

  **Orders**:  
  | Order_ID | Customer_ID |  
  |----------|-------------|  
  | 101      | 1           |  
  | 103      | 3           |  

- **Query**:  
  ```sql
  SELECT Customers.Name, Orders.Order_ID
  FROM Customers
  FULL JOIN Orders
  ON Customers.Customer_ID = Orders.Customer_ID;
  ```
- **Result**:  
  | Name  | Order_ID |  
  |-------|----------|  
  | Ram   | 101      |  
  | NULL  | 103      |  
  | Shyam | NULL     |  
  | Mohan | NULL     |  

---

## **5. CROSS JOIN**  
- **Definition**:  
  CROSS JOIN har row ko doosri table ki **har row ke saath combine karta hai**. Sabhi possible combinations dikhata hai.

- **Use Case**:  
  Jab tumhe **sabhi combinations dikhane ho**, jaise "Har customer ka har product ke saath pairing."

- **Example Tables**:  
  **Customers**:  
  | Name  |  
  |-------|  
  | Ram   |  
  | Shyam |  

  **Products**:  
  | Product  |  
  |----------|  
  | Pen      |  
  | Pencil   |  

- **Query**:  
  ```sql
  SELECT Customers.Name, Products.Product
  FROM Customers
  CROSS JOIN Products;
  ```
- **Result**:  
  | Name  | Product  |  
  |-------|----------|  
  | Ram   | Pen      |  
  | Ram   | Pencil   |  
  | Shyam | Pen      |  
  | Shyam | Pencil   |  

---

## **6. SELF JOIN**  
- **Definition**:  
  SELF JOIN ek table ko **khud ke saath join karta hai**. Ek hi table ke andar relationships dhoondhne ke liye use hota hai.

- **Use Case**:  
  Jab tumhe ek table ke andar **hierarchical relationships** dikhane ho, jaise "Employee aur unke managers."

- **Example Table**:  
  **Employees**:  
  | Emp_ID | Name   | Manager_ID |  
  |--------|--------|------------|  
  | 1      | Ram    | NULL       |  
  | 2      | Shyam  | 1          |  
  | 3      | Mohan  | 1          |  
  | 4      | Sohan  | 2          |  

- **Query**:  
  ```sql
  SELECT E1.Name AS Employee, E2.Name AS Manager
  FROM Employees E1
  LEFT JOIN Employees E2
  ON E1.Manager_ID = E2.Emp_ID;
  ```
- **Result**:  
  | Employee | Manager |  
  |----------|---------|  
  | Ram      | NULL    |  
  | Shyam    | Ram     |  
  | Mohan    | Ram     |  
  | Sohan    | Shyam   |  

---

Aapko sab clear ho gaya? Agar kuch aur doubt ho toh zarur poochhna mere senior! 😊