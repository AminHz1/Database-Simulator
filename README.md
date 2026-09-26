# 🗄️ Simple C++ In-Memory Database

A simple **in-memory database management system** implemented in **C++** using Object-Oriented Programming (OOP).

This project simulates some basic database operations such as creating tables, defining columns, inserting records, searching, updating, and deleting records.

The project stores all data in memory using C++ containers such as `vector` and `map`.

---

## ✨ Features

* 📋 Create database schemas and tables
* 🏷️ Define table columns and their data types
* ➕ Insert records into tables
* 🔍 Search records by column and value
* ✏️ Update existing records
* 🗑️ Delete records using an ID
* 📊 Display all available tables and their columns
* 🚫 Check whether a table exists
* 🧹 Logical deletion using metadata
* 🧩 Support for multiple tables
* 🏗️ Object-Oriented design

---

## 🛠️ Technologies

* **C++**
* Object-Oriented Programming (OOP)
* STL:

  * `vector`
  * `map`
  * `string`
  * `sstream`

---

## 📂 Project Structure

The project is implemented using several main classes:

```text
Database
│
├── MetaData
│   ├── isDeleted
│   └── tableName
│
├── Record
│   ├── MetaData
│   └── data
│
├── column
│   ├── columnName
│   └── dataType
│
├── schema
│   ├── tableName
│   └── Columns
│
├── dbinfo
│   └── schemas
│
└── DataBase
    └── records
```

---

## 🧱 Main Classes

### `MetaData`

Stores additional information about each record.

```cpp
struct MetaData {
    bool isDeleted;
    string tableName;
};
```

---

### `Record`

Represents a single record in a table.

Each record contains:

* Table name
* Deletion status
* Record data

```cpp
class Record {
public:
    MetaData MetaData;
    vector<string> data;
};
```

---

### `column`

Represents a column in a table.

Each column has:

* Column name
* Data type

Example:

```cpp
student.addColumn("ID", "int");
student.addColumn("Name", "string");
student.addColumn("age", "int");
```

---

### `schema`

Represents a table and its columns.

Example:

```cpp
schema student("student");

student.addColumn("ID", "int");
student.addColumn("Name", "string");
student.addColumn("age", "int");
```

---

### `dbinfo`

Manages database schemas and provides operations such as:

* Adding tables
* Checking table existence
* Deleting tables
* Displaying tables and columns

Example:

```cpp
Q.addSchema(student);
```

---

### `DataBase`

This is the main class responsible for managing records.

Records are stored using:

```cpp
map<string, vector<Record>> records;
```

The table name is used as the key, while the records belonging to that table are stored in a `vector`.

---

## ⚙️ Supported Operations

### ➕ Insert Record

Records can be inserted using a variadic template:

```cpp
DB.insertRecord("student", 1, "Ali", "21");
DB.insertRecord("student", 2, "Behnam", "20");
```

The program automatically converts the provided values to strings before storing them.

---

### 🔍 Find Records

Records can be searched using a column name and target value:

```cpp
DB.findRecords("student", "Name", "Ali");
```

Example output:

```text
>> 1 Ali 21
```

---

### ✏️ Update Record

A record can be updated by specifying:

* Table name
* Column name
* Old value
* New value

Example:

```cpp
DB.updateRecord(
    "student",
    "Name",
    "Ali",
    "Reza"
);
```

This changes:

```text
Ali
```

to:

```text
Reza
```

---

### 🗑️ Delete Record

Records can be deleted using their ID:

```cpp
DB.deleteRecord("student", 1);
```

The project uses **logical deletion**.

Instead of physically removing the record from the `vector`, the following metadata is changed:

```cpp
record.MetaData.isDeleted = true;
```

Deleted records are then ignored during searches and updates.

---

### 📋 Display Tables

All available tables and their columns can be displayed using:

```cpp
Q.display_AllTable();
```

Example:

```text
Available Tables:
========================
Tablename: student
  Columns:
=> ID (int)
=> Name (string)
=> age (int)
------------------------
```

---

## 🚀 Example

The following example creates two tables:

### Student

```text
ID      int
Name    string
age     int
```

### Teacher

```text
name    string
age     int
email   string
```

Records can then be inserted:

```cpp
DB.insertRecord("student", 1, "Ali", "21");
DB.insertRecord("student", 2, "Behnam", "20");

DB.insertRecord(
    "teacher",
    "Hossein",
    "35",
    "hossein12@gmail.com"
);
```

After that, records can be searched, updated, or deleted.

---

## ▶️ How to Run

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
```

### 2. Enter the project directory

```bash
cd YOUR_REPOSITORY
```

### 3. Compile the program

Using `g++`:

```bash
g++ main.cpp -o database
```

### 4. Run

On Windows:

```bash
database.exe
```

On Linux/macOS:

```bash
./database
```

---

## 📌 Important Notes

This project is an **educational database simulation**.

It does not use a real database engine and does not save data permanently.

All records are stored in RAM, so the data will be lost when the program terminates.

The project is mainly intended to demonstrate:

* C++ OOP
* Classes and objects
* Constructors
* Encapsulation
* Friend classes
* STL containers
* Templates
* Iterators
* Record management
* Basic database concepts

---

## 🔮 Possible Future Improvements

Some possible improvements for future versions:

* 💾 Save data to files
* 📥 Load database data when the program starts
* 🔑 Support primary keys
* 🔗 Support foreign keys
* 🧮 Add more data types
* 📑 Add SQL-like commands
* 🔍 Support advanced queries
* 📊 Add sorting and filtering
* 🔐 Add user authentication
* 🗂️ Separate the project into multiple `.h` and `.cpp` files

---

## 👨‍💻 Author

Developed as a C++ educational project to practice **Object-Oriented Programming and basic database system concepts**.

---

## 📄 License

This project is available for educational and personal use.
