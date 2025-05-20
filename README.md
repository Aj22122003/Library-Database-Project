# 📚 University Library Database

A **relational database** system for managing a university library, designed to store and manage data on books, authors, publishers, students, and employees efficiently.

---

## 🔧 Project Overview

This project implements a fully normalized SQL database that:

- Tracks book inventory and their authors
- Manages book issuances to students
- Stores details of publishers, employees, and students
- Facilitates many-to-many relationships between books and authors

---

## 🗂️ Entity-Relationship Diagram

![Library ER Diagram](./cb8b2ed5-a67f-49a5-977a-dd8704ea43f9.png)

---

## 🧩 Database Schema

The schema consists of the following tables:

### 1. `STUDENT`
| Field     | Type        | Description          |
|-----------|-------------|----------------------|
| StuID     | PK          | Student ID           |
| StuName   | VARCHAR     | Student name         |
| StuAddr   | VARCHAR     | Student address      |
| StuEmail  | VARCHAR     | Student email        |

### 2. `EMPLOYEE`
| Field     | Type        | Description          |
|-----------|-------------|----------------------|
| EmpID     | PK          | Employee ID          |
| EmpName   | VARCHAR     | Employee name        |
| EmpAddr   | VARCHAR     | Employee address     |
| EmpEmail  | VARCHAR     | Employee email       |

### 3. `BOOK`
| Field     | Type        | Description                  |
|-----------|-------------|------------------------------|
| BookID    | PK          | Book ID                      |
| BookName  | VARCHAR     | Name of the book             |
| NoOfPages | INTEGER     | Number of pages              |
| ISBNNum   | VARCHAR     | ISBN number                  |
| StuID     | FK → STUDENT| Borrowed by (optional)       |
| EmpID     | FK → EMPLOYEE| Assigned librarian          |
| PubID     | FK → PUBLISHER| Publisher                   |

### 4. `AUTHOR`
| Field       | Type     | Description     |
|-------------|----------|-----------------|
| AuthorID    | PK       | Author ID       |
| AuthorName  | VARCHAR  | Name of author  |
| AuthorAddr  | VARCHAR  | Address         |
| AuthorEmail | VARCHAR  | Email           |

### 5. `BOOK_AUTH`
| Field        | Type     | Description                         |
|--------------|----------|-------------------------------------|
| BookAuthID   | PK       | Mapping ID                          |
| BookID       | FK → BOOK| Book linked to author               |
| AuthorID     | FK → AUTHOR| Author linked to book             |

### 6. `PUBLISHER`
| Field      | Type     | Description         |
|------------|----------|---------------------|
| PubID      | PK       | Publisher ID        |
| PubName    | VARCHAR  | Publisher name      |
| PubAddr    | VARCHAR  | Publisher address   |
| PubEmail   | VARCHAR  | Publisher email     |

---

## 🔑 Key Relationships & Constraints

- ✅ **Primary Keys:** Each entity table has a unique identifier (e.g., `StuID`, `BookID`, `AuthorID`).
- 🔗 **Foreign Keys:** `BOOK` table connects to `STUDENT`, `EMPLOYEE`, and `PUBLISHER`.
- 🔁 **Many-to-Many:** `BOOK_AUTH` bridges the many-to-many relationship between `BOOK` and `AUTHOR`.

---

## 💾 Technologies Used

- **SQL** (MariaDB)
- **ER Diagram** via draw.io / dbdiagram.io
- **HeidiSQL** for interface & query testing

---

## 🧪 Features & Testing

- Create and populate tables using SQL scripts
- Sample insert queries available
- Easily extendable to include:
  - Borrowing/return history
  - Fine management
  - Stored procedures for querying and logic encapsulation

---

## 📂 Sample SQL Structure

```sql
CREATE TABLE STUDENT (
    StuID INT PRIMARY KEY,
    StuName VARCHAR(100),
    StuAddr VARCHAR(200),
    StuEmail VARCHAR(100)
);
(More SQL files provided in the project directory)

📌 How to Use
Clone the repository:

bash
Copy
Edit
git clone https://github.com/omotuno/university_library_database_project.git
Load tables into your SQL environment (MariaDB preferred).

Execute sample queries or insert your own data.

📬 Contact
For queries or suggestions, open an issue on the GitHub repository
Ajinkya Kutarmare
kutarmareajinkya52@gmail.com


