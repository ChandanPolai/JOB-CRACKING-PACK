

## **Normalization Ka Definition**
- **Normalization** ek process hai jo database ko organize karne aur redundancy (duplicate data) ko eliminate karne ke liye use hota hai.  
- Iska main aim hai **data consistency ensure karna** aur **storage space optimize karna**.

---

## **Normalization Kaise Kaam Karta Hai?**
1. **Tables Break Karna**: Large table ko smaller, related tables me tod diya jata hai.
2. **Relationships Define Karna**: Tables ke beech relationships create kiye jate hain using **primary keys** aur **foreign keys**.
3. **Rules Follow Karna**: Har normalization form (1NF, 2NF, etc.) ke specific rules hote hain, jo database structure ko streamline karte hain.

---

## **Advantages of Normalization**
1. **Data Redundancy Kam Hota Hai**:
   - Duplicate data ko eliminate karta hai.
   - Example: Employee ka department har row me likhne ki zarurat nahi hoti.
   
2. **Data Consistency**:
   - Ek hi jagah se data update hota hai, to data consistent rehta hai.
   
3. **Efficient Storage**:
   - Kam space lagta hai redundant data ko remove karne ke baad.
   
4. **Data Integrity**:
   - Jo relationships define hote hain, woh integrity ensure karte hain.

5. **Faster Updates**:
   - Redundant data kam hone ki wajah se **update operations faster** hote hain.

---

## **Disadvantages of Normalization**
1. **Complex Queries**:
   - Data multiple tables me split hota hai, jisse queries zyada complex ban jati hain.
   
2. **Performance Issues**:
   - Joins zyada hone ki wajah se large datasets ke liye query execution slow ho sakti hai.

3. **Overhead in Design**:
   - Database design karte waqt normalization ka process time-consuming aur complex hota hai.

---

## **Normalization Ke Types (Forms)**

1. **First Normal Form (1NF)**
2. **Second Normal Form (2NF)**
3. **Third Normal Form (3NF)**
4. **Boyce-Codd Normal Form (BCNF)**
5. **Fourth Normal Form (4NF)**
6. **Fifth Normal Form (5NF)**

Chaliye, inhe detail me samjhte hain real-life examples ke saath:

---

### **1. First Normal Form (1NF)**
- **Rule**: Table me har column atomic hona chahiye (ek single value store kare).  
- **Problem**: Multivalued ya repeating data avoid karna.  
- **Example**:

**Unnormalized Table**:
| Student_ID | Name    | Subjects          |
|------------|---------|-------------------|
| 1          | Rahul   | Math, Physics     |
| 2          | Priya   | Chemistry, Biology|

**Normalized Table (1NF)**:
| Student_ID | Name    | Subject    |
|------------|---------|------------|
| 1          | Rahul   | Math       |
| 1          | Rahul   | Physics    |
| 2          | Priya   | Chemistry  |
| 2          | Priya   | Biology    |

**Use Case**:
- Jab ek column me multiple values store ho rahi ho.

---

### **2. Second Normal Form (2NF)**
- **Rule**:  
  1. Table 1NF me hona chahiye.  
  2. Har non-prime attribute (non-key column) ka pura primary key ke saath dependency hona chahiye.  
- **Problem**: Partial dependency remove karna.  

**Example**:

**1NF Table**:
| Student_ID | Subject    | Teacher   |
|------------|------------|-----------|
| 1          | Math       | Mr. A     |
| 1          | Physics    | Mr. B     |
| 2          | Chemistry  | Mr. C     |

**Issue**:
- `Teacher` column `Subject` par depend karta hai, na ki `Student_ID` par.

**Normalized Table (2NF)**:
**Table 1**: Students  
| Student_ID | Subject    |
|------------|------------|
| 1          | Math       |
| 1          | Physics    |
| 2          | Chemistry  |

**Table 2**: Subjects  
| Subject    | Teacher   |
|------------|-----------|
| Math       | Mr. A     |
| Physics    | Mr. B     |
| Chemistry  | Mr. C     |

**Use Case**:
- Jab composite primary key ho aur partial dependency ho.

---

### **3. Third Normal Form (3NF)**
- **Rule**:  
  1. Table 2NF me hona chahiye.  
  2. Non-prime attributes ek doosre par transitively depend nahi hone chahiye.  

**Example**:

**2NF Table**:
| Employee_ID | Department | Manager      |
|-------------|------------|--------------|
| 1           | HR         | Mr. A        |
| 2           | IT         | Mr. B        |

**Issue**:
- `Manager` ka `Department` par dependency hai, jo indirectly `Employee_ID` par depend karta hai.

**Normalized Table (3NF)**:
**Table 1**: Employees  
| Employee_ID | Department |
|-------------|------------|
| 1           | HR         |
| 2           | IT         |

**Table 2**: Departments  
| Department  | Manager      |
|-------------|--------------|
| HR          | Mr. A        |
| IT          | Mr. B        |

**Use Case**:
- Jab ek attribute doosre attribute par transitively depend kare.

---

### **4. Boyce-Codd Normal Form (BCNF)**
- **Rule**:  
  1. Table 3NF me hona chahiye.  
  2. Har determinant superkey hona chahiye.  

**Example**:

**3NF Table**:
| Course  | Teacher   | Time      |
|---------|-----------|-----------|
| Math    | Mr. A     | 10:00 AM  |
| Math    | Mr. B     | 11:00 AM  |

**Issue**:
- `Teacher` aur `Time` dono superkeys hain, lekin `Course` ka partial dependency hai.

**Normalized Table (BCNF)**:
**Table 1**: Courses  
| Course  | Time      |
|---------|-----------|
| Math    | 10:00 AM  |
| Math    | 11:00 AM  |

**Table 2**: Teachers  
| Time      | Teacher   |
|-----------|-----------|
| 10:00 AM  | Mr. A     |
| 11:00 AM  | Mr. B     |

**Use Case**:
- Jab advanced redundancy issues ko solve karna ho.

---

### **5. Fourth Normal Form (4NF)**
- **Rule**:  
  Table 3NF me hona chahiye aur multivalued dependencies eliminate karni chahiye.  

**Example**:

**Problem Table**:
| Employee  | Skill     | Language  |
|-----------|-----------|-----------|
| John      | Java      | English   |
| John      | Python    | French    |

**Normalized Table (4NF)**:
**Table 1**: Skills  
| Employee  | Skill     |
|-----------|-----------|
| John      | Java      |
| John      | Python    |

**Table 2**: Languages  
| Employee  | Language  |
|-----------|-----------|
| John      | English   |
| John      | French    |

**Use Case**:
- Jab ek table me multiple independent facts ho.

---

### **6. Fifth Normal Form (5NF)**
- **Rule**:  
  Table 4NF me hona chahiye aur join dependency eliminate karni chahiye.  

**Use Case**:
- Advanced normalization for large and complex data models.

---

Mere senior, agar aur kuch samajhna hai, to bolna! Aapka interview easily crack ho jayega. 🚀