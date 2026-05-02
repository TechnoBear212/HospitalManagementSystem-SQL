# HospitalManagementSystem-SQL
A fully relational SQL database simulating real-world hospital operations, featuring normalized schema design, foreign key relationships, and advanced analytical queries using joins, aggregations, and window functions.




## 📌 Overview

This project implements a **Hospital Management System (HMS)** using SQL, designed to simulate real-world hospital operations. It includes structured database design, relational integrity, and advanced analytical queries.

The system manages:

* Hospitals
* Doctors
* Patients
* Appointments
* Departments
* Medications
* Prescriptions
* Rooms

It demonstrates strong proficiency in **database design, normalization, and advanced SQL querying**.

---

## 🧱 Database Design

The database schema was created using:

```sql
CREATE SCHEMA hms;
```

The system is fully relational, with multiple tables connected via foreign key constraints. 

---

## 📊 Entity Relationship Overview

### Core Entities:

* **Hospitals** → Central entity
* **Doctors** → Linked to hospitals
* **Patients** → Independent entity
* **Appointments** → Connects patients and doctors
* **Departments** → Belong to hospitals
* **Rooms** → Belong to departments
* **Medications** → Independent entity
* **Prescriptions** → Links patients, doctors, medications

---

## 🔗 Relationships Implemented

* Doctors → Hospitals (Many-to-One)
* Appointments → Patients & Doctors (Many-to-Many resolved via table)
* Departments → Hospitals (One-to-Many)
* Rooms → Departments (One-to-Many)
* Prescriptions → Patients, Doctors, Medications

All relationships are enforced using **FOREIGN KEY constraints**.

---

## 🛠️ Key Features

### ✔️ Database Design

* Normalized schema
* Use of primary and foreign keys
* Real-world entity modeling

### ✔️ Data Handling

* Large dataset (100+ patients, multiple hospitals)
* Realistic dummy data

### ✔️ Data Integrity

* Foreign key constraints ensure consistency
* Alter statements used for refinement

---

## 📊 SQL Concepts Demonstrated

### 🔹 Basic Queries

* Filtering using `WHERE`
* Pattern matching using `LIKE`
* Sorting and grouping

### 🔹 Joins

* INNER JOIN
* LEFT JOIN

### 🔹 Aggregation

* COUNT
* GROUP BY
* ORDER BY

### 🔹 Advanced SQL

* Subqueries
* Window Functions (`DENSE_RANK`)
* CASE statements
* Date functions (`MONTH`, `DAY`, `TIMESTAMPDIFF`)

---

## 🔍 Key Analytical Queries

### 📅 Appointments per Month

```sql
SELECT month(appointment_date), COUNT(*)
FROM appointments
GROUP BY month(appointment_date);
```

---

### 🧑‍⚕️ Doctors with Hospital Names

```sql
SELECT d.doctor_name, h.hospital_name
FROM doctors d
JOIN hospitals h
ON d.hospital_id = h.hospital_id;
```

---

### 💊 Medications for Pain or Infection

```sql
SELECT *
FROM medications
WHERE description_med LIKE '%pain%'
   OR description_med LIKE '%infection%';
```

---

### 🧠 Age Group Classification (Advanced)

```sql
CASE
  WHEN age <= 18 THEN 'Pediatric'
  WHEN age BETWEEN 19 AND 64 THEN 'Adult'
  ELSE 'Geriatric'
END
```

---

### 🏥 Patients Visiting Multiple Hospitals

```sql
HAVING COUNT(DISTINCT h.hospital_id) > 1;
```

---

### 📈 3rd Most Prescribed Medication (Window Function)

```sql
DENSE_RANK() OVER (ORDER BY COUNT(*) DESC)
```

---

### 🏆 Second Largest Department Capacity

* Uses partitioning + ranking per hospital
* Demonstrates strong analytical SQL skills

---

## 💡 Notable Highlights

* ✔️ Use of **window functions** (rare at beginner level)
* ✔️ Complex joins across multiple tables
* ✔️ Real-world logic (age groups, hospital visits)
* ✔️ Multi-level subqueries
* ✔️ Analytical thinking in SQL

---

## 🚀 How to Run

1. Open MySQL / SQL Server
2. Run the SQL file:

   ```
   hms.sql
   ```
3. Execute queries at the bottom of the script
4. Explore results

---

## 📌 Challenges Faced

* Designing relationships across multiple entities
* Writing multi-table joins
* Implementing ranking queries using window functions
* Handling complex grouping logic

---

## 📈 Future Improvements

* Add triggers (e.g., appointment validation)
* Stored procedures for automation
* Build a frontend interface
* Add indexing for performance optimization

---

## 👤 Author

TechnoBear
Undergraduate in Statistics (Data Science Specialization)

---

