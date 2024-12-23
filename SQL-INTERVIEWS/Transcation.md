### **SQL Transactions**  

SQL transactions ek **logical unit of work** hai jo ek ya ek se zyada SQL operations ka group hota hai, jo ek saath execute hote hain. Transaction ka purpose yeh ensure karna hai ki ya to sab operations successfully execute ho (commit), ya koi bhi execute na ho (rollback).  

---

### **Features of Transactions (ACID Properties)**  
Transactions ko reliable banane ke liye **ACID properties** use hoti hain:  

1. **Atomicity:**  
   Transaction ka har operation ya to pura execute hoga ya kuch bhi nahi hoga.  
   **Example:** Agar ek account se paise deduct ho rahe hain aur doosre me add, to dono operations complete hone chahiye, warna rollback ho jata hai.

2. **Consistency:**  
   Transaction ke baad database ka state consistent rehna chahiye.  

3. **Isolation:**  
   Multiple transactions ek saath execute hone par ek doosre ko affect nahi karte.  

4. **Durability:**  
   Ek baar transaction commit hone ke baad, changes permanent ho jate hain, chahe system crash ho jaye.  

---

### **Use Cases of Transactions**  
1. **Banking Systems:**  
   - Fund transfer karte time (debit aur credit operations).  
   - Ensure karta hai ki paise ya to dono accounts me reflect karein ya kahin bhi nahi ho.  
   
2. **E-Commerce Platforms:**  
   - Inventory management ke liye (product stock reduce karna aur order update karna).  

3. **Data Integrity:**  
   - Multiple dependent tables ko update karte time atomicity maintain karta hai.  

4. **Batch Processing:**  
   - Large datasets pe updates, inserts, or deletes ek consistent state me rakhte hain.

---

### **Syntax for Transactions**  
SQL me transactions ko manage karne ke liye `BEGIN TRANSACTION`, `COMMIT`, aur `ROLLBACK` keywords use hote hain.  

#### **Basic Example:**
```sql
BEGIN TRANSACTION;
    UPDATE accounts SET balance = balance - 1000 WHERE account_id = 1; -- Debit
    UPDATE accounts SET balance = balance + 1000 WHERE account_id = 2; -- Credit
COMMIT;
```
Agar koi error hota hai, to `ROLLBACK` use hota hai:  
```sql
BEGIN TRANSACTION;
    UPDATE accounts SET balance = balance - 1000 WHERE account_id = 1; 
    UPDATE accounts SET balance = balance + 1000 WHERE account_id = 2; 
ROLLBACK; -- In case of error
```

---

### **Advantages of Transactions**  
1. **Data Consistency:** Multiple operations ke beech consistency ensure karta hai.  
2. **Error Handling:** Agar koi ek operation fail ho jaye, to changes rollback ho jate hain.  
3. **Concurrency Control:** Isolation ke through multiple users ke access ko properly handle karta hai.  

---

### **Problems Solved by Transactions**  
1. **Data Corruption:** Agar ek system crash ho jaye, to partially updated data avoid karta hai.  
2. **Concurrency Issues:** Isolation ensure karta hai ki ek transaction doosre ke intermediate state ko affect na kare.  
3. **Dependency Handling:** Related operations ko ek atomic block me execute karta hai.  

---

### **Problems Created by Transactions**  
1. **Deadlocks:**  
   Jab do transactions ek doosre ke locked resources ko access karne ka wait karte hain, to deadlock ho sakta hai.  
   **Solution:** Timeout mechanism ya resource ordering.  

2. **Performance Overhead:**  
   Transactions slow ho sakte hain agar bahut saari locks lagayi jayein.  

3. **Resource Usage:**  
   Long-running transactions zyada resources occupy karte hain, jo system slowdown ka karan ban sakte hain.  

---

### **Types of Transactions**
1. **Implicit Transactions:**  
   SQL automatically transaction boundaries decide karta hai.  
   **Example:** `INSERT`, `DELETE`, or `UPDATE` single statement ke liye implicit hota hai.

2. **Explicit Transactions:**  
   Developer manually transaction boundaries define karta hai (`BEGIN`, `COMMIT`, `ROLLBACK`).  
   **Example:** Banking systems me fund transfer operations.  

3. **Distributed Transactions:**  
   Multiple databases ke beech execute hone wale transactions.  
   **Example:** E-commerce platforms me payment gateway aur order database synchronization.  

4. **Nested Transactions:**  
   Parent transaction ke andar ek aur transaction execute hota hai.  

---

### **Real-World Example**  
#### **Fund Transfer in Banking System:**  
```sql
BEGIN TRANSACTION;

-- Deduct amount from sender
UPDATE accounts 
SET balance = balance - 1000 
WHERE account_id = 1;

-- Add amount to receiver
UPDATE accounts 
SET balance = balance + 1000 
WHERE account_id = 2;

-- Commit if all operations are successful
COMMIT;
```
