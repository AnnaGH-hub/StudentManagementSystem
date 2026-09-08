# 🎓 Student Management System

A console-based Student Management System built with **C# (.NET)** and **Microsoft SQL Server**. It allows administrators to perform full CRUD (Create, Read, Update, Delete) operations on student records through a simple, menu-driven command-line interface.

This project was built as a hands-on exercise in working with relational databases from C#, using `Microsoft.Data.SqlClient` for data access and parameterized queries to prevent SQL injection.

---

## 📋 Features

- ➕ **Add** new student records
- 📄 **View** all students or search for a specific student
- ✏️ **Update** existing student information
- 🗑️ **Delete** student records
- 🔒 Parameterized SQL queries to prevent SQL injection
- ⚙️ Externalized database configuration (no hardcoded credentials)

---

## 🛠️ Tech Stack

| Layer          | Technology                          |
|----------------|--------------------------------------|
| Language       | C# (.NET / .NET Core)                |
| Database       | Microsoft SQL Server                 |
| Data Access    | Microsoft.Data.SqlClient             |
| Interface      | Console Application                  |

---

## 📁 Project Structure

```
StudentManagementSystem/
├── StudentManagementSystem/
│   ├── Program.cs          # Application entry point & menu logic
│   ├── Student.cs          # Student model/entity
│   ├── DatabaseHelper.cs   # Data access logic (SQL commands)
│   └── appsettings.json    # Connection string configuration
├── Database/
│   └── schema.sql          # Table creation & sample seed data
├── .gitignore
└── README.md
```

> Note: adjust the tree above to match your actual file names/folders.

---

## 🚀 Getting Started

### Prerequisites

- [.NET SDK](https://dotnet.microsoft.com/download) (6.0 or later)
- [SQL Server](https://www.microsoft.com/sql-server) (Express edition works fine) or a SQL Server instance you can connect to
- [SQL Server Management Studio](https://learn.microsoft.com/sql/ssms) (optional, for viewing the database)

### 1. Clone the repository

```bash
git clone https://github.com/siMobin/StudentManagementSystem.git
cd StudentManagementSystem
```

### 2. Set up the database

Run the SQL script in `Database/schema.sql` against your SQL Server instance to create the required database and `Students` table:

```sql
CREATE DATABASE StudentDB;
GO

USE StudentDB;
GO

CREATE TABLE Students (
    StudentId   INT IDENTITY(1,1) PRIMARY KEY,
    FullName    NVARCHAR(100) NOT NULL,
    Email       NVARCHAR(100),
    Course      NVARCHAR(50),
    EnrollDate  DATE
);
```

### 3. Configure the connection string

Update the connection string in `appsettings.json` (or `Program.cs`, if not yet externalized) to point to your local SQL Server instance:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost;Database=StudentDB;Trusted_Connection=True;TrustServerCertificate=True;"
  }
}
```

> ⚠️ Never commit real credentials. Use Windows Authentication locally, or environment variables / user secrets for anything else.

### 4. Run the application

```bash
dotnet run
```

You'll be presented with a menu to add, view, update, or delete student records.

---

## 🖥️ Example Usage

```
====== Student Management System ======
1. Add Student
2. View All Students
3. Update Student
4. Delete Student
5. Exit
Enter your choice: 1

Enter Full Name: Jane Doe
Enter Email: jane.doe@example.com
Enter Course: Computer Science
Student added successfully!
```

---

## 🔒 Security Notes

- All SQL queries use **parameterized commands** to prevent SQL injection.
- Sensitive configuration (connection strings) is kept out of source code where possible.

---

## 🧭 Roadmap / Possible Improvements

- [ ] Migrate to a layered architecture (separate Repository/Service layers)
- [ ] Add input validation and custom exception handling
- [ ] Add unit tests for data access logic
- [ ] Build a GUI (WPF) or Web API version
- [ ] Add logging (e.g., Serilog)

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 👤 Author

**Shakibul Islam Mobin**
GitHub: [@siMobin](https://github.com/siMobin)
