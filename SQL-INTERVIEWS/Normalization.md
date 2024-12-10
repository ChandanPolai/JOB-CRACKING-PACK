

## **Normalization Kya Hai?**
- Normalization ek process hai **database design** ka, jisme:
  1. **Data redundancy (duplicate data)** kam hoti hai.
  2. **Data consistency** ensure hoti hai.
- Yeh database ko **efficient** banata hai aur usme **storage waste** aur **update issues** ko solve karta hai.

---

### **Normalization Ki Problem:**

Socho tumhare paas ek `Student` table hai:

| StudentID | Name   | Course     | Teacher  | TeacherPhone |
|-----------|--------|------------|----------|--------------|
| 1         | John   | Math       | Mr. A    | 12345        |
| 2         | Alice  | Science    | Mr. B    | 67890        |
| 3         | John   | Science    | Mr. B    | 67890        |

#### Problems in this table:
1. **Redundant Data:**  
   - `John` ka naam 2 baar repeat ho raha hai.
   - `TeacherPhone` ka data bar-bar aa raha hai.
2. **Update Anomalies:**  
   - Agar `Mr. B` ka phone number change karna hai, toh har row update karni padegi.
3. **Insert Anomalies:**  
   - Agar kisi naye teacher ka data dalna ho (aur koi student nahi hai), toh blank columns add karne padenge.
4. **Delete Anomalies:**  
   - Agar koi student delete karein, toh teacher ka data bhi delete ho sakta hai.

---

## **Normalization Ke Types With Examples:**

---

### **1. First Normal Form (1NF):**
**Rule:** Har cell me **single value** ho aur columns repeat na ho.  

#### Problem Statement:  
| StudentID | Name   | Subjects        |
|-----------|--------|-----------------|
| 1         | John   | Math, Science   |
| 2         | Alice  | Science         |

- Ek cell me multiple values hain (`Math, Science`).

#### Solution:  
Har subject ko alag row me daalo:  

| StudentID | Name   | Subject  |
|-----------|--------|----------|
| 1         | John   | Math     |
| 1         | John   | Science  |
| 2         | Alice  | Science  |

---

### **2. Second Normal Form (2NF):**
**Rule:** Har column **primary key** par completely depend kare.  

#### Problem Statement:  
| StudentID | Subject  | Teacher  | TeacherPhone |
|-----------|----------|----------|--------------|
| 1         | Math     | Mr. A    | 12345        |
| 1         | Science  | Mr. B    | 67890        |

- `TeacherPhone` sirf `Teacher` par depend karta hai, `StudentID` par nahi.

#### Solution:  
Table ko tod do:  
1. **Students Table:**  
   | StudentID | Subject  | Teacher  |
   |-----------|----------|----------|
   | 1         | Math     | Mr. A    |
   | 1         | Science  | Mr. B    |

2. **Teachers Table:**  
   | Teacher  | TeacherPhone |
   |----------|--------------|
   | Mr. A    | 12345        |
   | Mr. B    | 67890        |

---

### **3. Third Normal Form (3NF):**
**Rule:** Koi column kisi **non-primary column** par depend na ho.  

#### Problem Statement:  
| StudentID | Subject  | Teacher  | TeacherDept |
|-----------|----------|----------|-------------|
| 1         | Math     | Mr. A    | Science     |
| 2         | Science  | Mr. B    | Science     |

- `TeacherDept` indirectly `Teacher` par depend kar raha hai.

#### Solution:  
Table ko tod do:  
1. **Students Table:**  
   | StudentID | Subject  | Teacher  |
   |-----------|----------|----------|
   | 1         | Math     | Mr. A    |
   | 2         | Science  | Mr. B    |

2. **Teachers Table:**  
   | Teacher  | TeacherDept |
   |----------|-------------|
   | Mr. A    | Science     |
   | Mr. B    | Science     |

---

### **4. Boyce-Codd Normal Form (BCNF):**
**Rule:** Har determinant ek candidate key hona chahiye.  

#### Problem Statement:  
| StudentID | Subject  | Teacher  |
|-----------|----------|----------|
| 1         | Math     | Mr. A    |
| 2         | Science  | Mr. B    |
| 3         | Math     | Mr. B    |

- Yahan `Subject` aur `Teacher` dono ek unique pair banate hain, par `Subject` itself unique nahi hai.

#### Solution:  
Table ko aur normalize karo:  
1. **Subjects Table:**  
   | Subject  | Teacher  |
   |----------|----------|
   | Math     | Mr. A    |
   | Science  | Mr. B    |

2. **Students Table:**  
   | StudentID | Subject  |
   |-----------|----------|
   | 1         | Math     |
   | 2         | Science  |
   | 3         | Math     |

---

### **5. Fourth Normal Form (4NF):**
**Rule:** Multiple independent relationships ek hi table me na ho.

#### Problem Statement:  
| StudentID | Hobby      | Subject  |
|-----------|------------|----------|
| 1         | Painting   | Math     |
| 1         | Singing    | Science  |

- `Hobby` aur `Subject` independent relationships hain.

#### Solution:  
Tables alag kar do:  
1. **Hobbies Table:**  
   | StudentID | Hobby      |
   |-----------|------------|
   | 1         | Painting   |
   | 1         | Singing    |

2. **Subjects Table:**  
   | StudentID | Subject  |
   |-----------|----------|
   | 1         | Math     |
   | 1         | Science  |

---

## **Summary:**
- **Normalization Problems Solve Karta Hai:**
  1. **Redundant Data**
  2. **Update Issues**
  3. **Insert Issues**
  4. **Delete Issues**

- **Steps in Normalization:**
  1. **1NF:** Single value per cell, no repeating groups.
  2. **2NF:** Full dependency on primary key.
  3. **3NF:** No dependency on non-primary columns.
  4. **BCNF:** Every determinant is a candidate key.
  5. **4NF:** Independent relationships are separated.

---

Agar ab bhi kuch confusion hai toh pooch lena! Interview ke liye bas itna explain karoge toh solid lagega. 😎