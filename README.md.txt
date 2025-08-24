# 📌 Java & Spring Boot Task Repository

This repository contains multiple Java and Spring Boot tasks (Task 4 → Task 8).  
Each task demonstrates important concepts in **Java programming, JDBC, Spring Boot, and REST API integration**.  

---

## 📂 Repository Structure
```
.
├── Task4-FileIO
│   ├── products.csv
│   └── FileIOCSV.java
├── Task5-ExceptionHandling
│   └── FileProcessingWithExceptions.java
├── Task6-JDBC
│   └── JDBCCrudApp.java
├── Task7-RestAPI
│   └── src/main/java/com/example/taskapi/...
├── Task8-FrontendIntegration
│   ├── index.html
│   └── script.js
└── README.md
```

---

## 🔹 Task 4: File I/O – CSV Read & Write
**Objective**: Read data from `products.csv`, process it, and write results to another CSV.

### Steps to Execute:
1. Open `Task4-FileIO` in Eclipse/IntelliJ/VS Code.  
2. Ensure `products.csv` exists in the project root with sample data:
   ```
   Laptop,45000
   Mouse,500
   Phone,20000
   ```
3. Run `FileIOCSV.java`.  
4. Output:
   - A new file `filtered_products.csv` will be generated with products where price > 1000.  
   - Console will show a success message.

---

## 🔹 Task 5: Exception Handling – Robust File Processing
**Objective**: Improve Task 4 with proper exception handling.

### Steps to Execute:
1. Open `Task5-ExceptionHandling` project.  
2. Ensure `products.csv` is present.  
3. Run `FileProcessingWithExceptions.java`.  
4. Behavior:
   - Handles `FileNotFoundException` if file missing.  
   - Handles `NumberFormatException` for invalid prices.  
   - Throws custom `InvalidProductDataException` for bad rows.  
   - Always closes file using `finally`.  
5. Test with valid & invalid CSV data to see error handling.

---

## 🔹 Task 6: JDBC & Database Integration
**Objective**: Connect Java app to MySQL/H2 and perform CRUD.

### Steps to Execute:
1. Install **MySQL** or use **H2 in-memory DB**.  
2. Create database & table:
   ```sql
   CREATE DATABASE taskdb;
   USE taskdb;

   CREATE TABLE users (
       id INT PRIMARY KEY AUTO_INCREMENT,
       name VARCHAR(50),
       email VARCHAR(100)
   );
   ```
3. Add JDBC driver dependency to project (MySQL/H2).  
4. Update DB credentials in code:
   ```java
   Connection conn = DriverManager.getConnection(
       "jdbc:mysql://localhost:3306/taskdb", "root", "password"
   );
   ```
5. Run `JDBCCrudApp.java`.  
6. Test insert, select, update, delete operations.  

---

## 🔹 Task 7: Build REST API with Spring Boot
**Objective**: Build a REST API for Task Management.

### Steps to Execute:
1. Open [Spring Initializr](https://start.spring.io/).  
   - Add dependencies: **Spring Web**, **Spring Data JPA** (optional).  
   - Import into Eclipse/IntelliJ.  
2. Create `Task.java` model:
   ```java
   private Long id;
   private String title;
   private String description;
   ```
3. Create `TaskController.java` with CRUD endpoints:
   - `GET /tasks`
   - `POST /tasks`
   - `PUT /tasks/{id}`
   - `DELETE /tasks/{id}`
4. Run Spring Boot app:
   ```bash
   mvn spring-boot:run
   ```
5. Test using Postman:  
   - `GET http://localhost:9090/tasks`  
   - `POST http://localhost:9090/tasks` with JSON body:  
     ```json
     {
       "id": 1,
       "title": "Test Task",
       "description": "Integration with API"
     }
     ```

---

## 🔹 Task 8: Frontend Integration with REST API
**Objective**: Simple web page consuming REST API.

### Steps to Execute:
1. Open `Task8-FrontendIntegration` folder.  
2. Create `index.html` with a task list section and form.  
3. JavaScript (`script.js`) will:
   - Fetch tasks from backend:  
     ```js
     fetch("http://localhost:9090/tasks")
       .then(res => res.json())
       .then(data => {
         // render tasks into DOM
       });
     ```
   - Add tasks via POST:  
     ```js
     fetch("http://localhost:9090/tasks", {
       method: "POST",
       headers: {"Content-Type":"application/json"},
       body: JSON.stringify({title, description})
     });
     ```
4. Run Spring Boot backend (Task 7).  
5. Open `index.html` in browser.  
6. Interact with API (list tasks, add new tasks dynamically).  

---

## ✅ Final Notes
- **Task 4–6** → Java console applications (run inside IDE).  
- **Task 7–8** → Spring Boot + Frontend (backend must run before frontend).  
- Database credentials (Task 6) should match your system.  
- Each task is placed inside a separate folder (`Task4-FileIO/`, `Task5-ExceptionHandling/`, …).  
