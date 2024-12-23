### **SQL Triggers:**

**SQL Triggers** ek predefined set of instructions hain jo automatically execute hote hain jab kisi table par specific events occur hote hain. Triggers ko database me integrity maintain karne aur repetitive tasks automate karne ke liye use kiya jata hai. 

---

### **Key Characteristics of Triggers:**

1. **Automatic Execution**: Trigger automatically fire hota hai when a specified event occurs (e.g., INSERT, UPDATE, DELETE).
2. **Event-Driven**: Specific database operations par execute hota hai.
3. **Defined for a Table**: Triggers hamesha kisi particular table ke saath associated hote hain.
4. **Execution Timing**: 
   - **BEFORE**: Trigger event ke hone se pehle execute hota hai.
   - **AFTER**: Trigger event ke hone ke baad execute hota hai.

---

### **Syntax of Triggers:**
```sql
CREATE TRIGGER trigger_name
AFTER | BEFORE INSERT | UPDATE | DELETE
ON table_name
FOR EACH ROW
BEGIN
    -- Trigger logic
END;
```

---

### **Types of Triggers:**

1. **Before Triggers**:
   - Event hone se pehle execute hota hai.
   - Example: Validate data before inserting it into a table.

2. **After Triggers**:
   - Event hone ke baad execute hota hai.
   - Example: Audit logging ke liye data store karna after an operation.

3. **Instead of Triggers** (Supported by some databases like SQL Server):
   - Event ke hone ki jagah trigger execute hota hai.
   - Example: Views par operations implement karna.

---

### **Trigger Events:**
1. **INSERT Trigger**: Jab table me naya data insert hota hai.
2. **UPDATE Trigger**: Jab table ke existing data me modification hota hai.
3. **DELETE Trigger**: Jab table se data delete hota hai.

---

### **Examples of Triggers:**

#### **1. AFTER INSERT Trigger (Audit Logging Example):**
```sql
CREATE TRIGGER after_employee_insert
AFTER INSERT
ON employees
FOR EACH ROW
BEGIN
    INSERT INTO audit_log (action, employee_id, timestamp)
    VALUES ('INSERT', NEW.employee_id, NOW());
END;
```
**Explanation**:
- Jab employees table me koi nayi entry insert hoti hai, audit_log table me ek record save hota hai.

---

#### **2. BEFORE UPDATE Trigger (Data Validation Example):**
```sql
CREATE TRIGGER before_employee_update
BEFORE UPDATE
ON employees
FOR EACH ROW
BEGIN
    IF NEW.salary < 0 THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Salary cannot be negative';
    END IF;
END;
```
**Explanation**:
- Jab salary ko update kiya jata hai aur value negative hoti hai, trigger error throw karega.

---

#### **3. AFTER DELETE Trigger (Backup Deleted Records):**
```sql
CREATE TRIGGER after_employee_delete
AFTER DELETE
ON employees
FOR EACH ROW
BEGIN
    INSERT INTO deleted_employees (employee_id, name, deleted_at)
    VALUES (OLD.employee_id, OLD.name, NOW());
END;
```
**Explanation**:
- Jab employees table se record delete hota hai, wo record deleted_employees table me backup ke liye save ho jata hai.

---

### **Use Cases of Triggers:**

1. **Audit Logs**:
   - Automatically record who made changes and when.
2. **Data Validation**:
   - Validate incoming data before inserting or updating it.
3. **Backup Management**:
   - Backup data before it is deleted.
4. **Complex Business Rules**:
   - Implement rules like cascading updates or notifications.

---

### **Advantages of Triggers:**

1. **Automation**: Repetitive tasks ko automate karta hai.
2. **Data Integrity**: Data consistency aur validation ensure karta hai.
3. **Reduced Application Code**: Business logic ko database level par implement karta hai.

---

### **Disadvantages of Triggers:**

1. **Complex Debugging**: Triggers ka execution flow trace karna difficult ho sakta hai.
2. **Performance Overhead**: Complex triggers query performance ko slow kar sakte hain.
3. **Limited Scope**: Triggers sirf table level events par work karte hain, application-level logic implement nahi karte.

---

### **Best Practices for Triggers:**
1. Avoid using triggers for simple tasks; prefer constraints or stored procedures.
2. Keep the trigger logic simple and efficient.
3. Always test triggers for unintended side effects.
4. Document triggers properly, as they may not be apparent in schema design.

Agar tumhe specific triggers ke use case ya implementation ka example chahiye, to batao! 😊