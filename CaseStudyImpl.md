
---

## 🔰 PROBLEM STATEMENT

Design and implement a **console-based Java application** using **JDBC** that supports:

✅ Full CRUD operations on Employee data
✅ Additional operations:

* Search employees by department
* Update salary of an employee
* Check if an employee exists by ID

Requirements:

* ✅ Layered architecture (Model, DAO, Service, Main)
* ✅ Singleton DB connection
* ✅ Externalized DB configuration via `.properties`
* ✅ Maven project with proper dependencies
* ✅ Lombok for boilerplate elimination

---

## 🛠 TOOLS & TECHNOLOGIES USED

| Component           | Tool/Technology         |
| ------------------- | ----------------------- |
| Language            | Java 8+                 |
| DB                  | MySQL                   |
| Connectivity        | JDBC                    |
| Dependency Mgmt     | Maven                   |
| Configuration       | `.properties` file      |
| Code Simplification | Lombok                  |
| IDE (Optional)      | IntelliJ IDEA / Eclipse |

---

## 🗂 PROJECT STRUCTURE

```
employee-crud-jdbc/
├── src/
│   ├── main/java/
│   │   ├── config/
│   │   │   └── DBConfig.java
│   │   ├── model/
│   │   │   └── Employee.java
│   │   ├── dao/
│   │   │   ├── EmployeeDAO.java
│   │   │   └── EmployeeDAOImpl.java
│   │   ├── service/
│   │   │   ├── EmployeeService.java
│   │   │   └── EmployeeServiceImpl.java
│   │   └── MainApp.java
│   └── resources/
│       └── db.properties
├── schema.sql
└── pom.xml
```

---

## 📄 FILE: `pom.xml`

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>employee-crud-jdbc</artifactId>
    <version>1.0</version>

    <dependencies>
        <!-- ✅ MySQL JDBC Driver -->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>8.0.33</version>
        </dependency>

        <!-- ✅ Lombok for reducing boilerplate -->
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <version>1.18.28</version>
            <scope>provided</scope>
        </dependency>
    </dependencies>
</project>
```

✅ **Explanation:**
Adds JDBC driver for MySQL and Lombok dependency for model class code simplification.

---

## 📄 FILE: `src/main/resources/db.properties`

```properties
db.url=jdbc:mysql://localhost:3306/testdb
db.username=root
db.password=yourpassword
```

✅ **Explanation:**
Keeps DB credentials external to Java code for security and environment flexibility.

---

## 📄 FILE: `schema.sql`

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100),
    department VARCHAR(50),
    salary DOUBLE,
    active BOOLEAN,
    joining_date DATE,
    age INT
);
```

✅ **Explanation:**
Creates a table with 8 columns for storing employee data in MySQL.

---

## 📄 FILE: `config/DBConfig.java`

```java
package config;

import java.sql.*;
import java.util.*;
import java.io.InputStream;

public class DBConfig {
    private static Connection connection;

    private DBConfig() {}

    public static Connection getInstance() {
        if (connection == null) {
            try (InputStream input = DBConfig.class.getClassLoader().getResourceAsStream("db.properties")) {
                Properties props = new Properties();
                props.load(input);
                connection = DriverManager.getConnection(
                    props.getProperty("db.url"),
                    props.getProperty("db.username"),
                    props.getProperty("db.password")
                );
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
        return connection;
    }
}
```

✅ **Explanation:**
Implements **Singleton** pattern. Loads DB config from file and returns a single shared `Connection`.

---

## 📄 FILE: `model/Employee.java`

```java
package model;

import lombok.*;
import java.sql.Date;

@Data
@NoArgsConstructor
@AllArgsConstructor
public class Employee {
    private int id;
    private String name;
    private String email;
    private String department;
    private double salary;
    private boolean active;
    private Date joiningDate;
    private int age;
}
```

✅ **Explanation:**
A POJO representing Employee entity with annotations:

* `@Data` – getters/setters, toString, etc.
* `@NoArgsConstructor`, `@AllArgsConstructor` – constructors

---

## 📄 FILE: `dao/EmployeeDAO.java`

```java
package dao;

import model.Employee;
import java.util.List;

public interface EmployeeDAO {
    void save(Employee emp);
    Employee findById(int id);
    List<Employee> findAll();
    void update(Employee emp);
    void deleteById(int id);
    List<Employee> findByDepartment(String dept);
    void updateSalary(int id, double newSalary);
    boolean exists(int id);
}
```

✅ **Explanation:**
Defines all **CRUD + 3 additional** DB operations.

---

## 📄 FILE: `dao/EmployeeDAOImpl.java`

```java
package dao;

import config.DBConfig;
import model.Employee;

import java.sql.*;
import java.util.*;

public class EmployeeDAOImpl implements EmployeeDAO {
    private final Connection conn = DBConfig.getInstance();

    public void save(Employee emp) {
        String sql = "INSERT INTO employees VALUES (?, ?, ?, ?, ?, ?, ?, ?)";
        try (PreparedStatement ps = conn.prepareStatement(sql)) {
            ps.setInt(1, emp.getId());
            ps.setString(2, emp.getName());
            ps.setString(3, emp.getEmail());
            ps.setString(4, emp.getDepartment());
            ps.setDouble(5, emp.getSalary());
            ps.setBoolean(6, emp.isActive());
            ps.setDate(7, emp.getJoiningDate());
            ps.setInt(8, emp.getAge());
            ps.executeUpdate();
        } catch (SQLException e) { e.printStackTrace(); }
    }

    public Employee findById(int id) {
        try (PreparedStatement ps = conn.prepareStatement("SELECT * FROM employees WHERE id=?")) {
            ps.setInt(1, id);
            ResultSet rs = ps.executeQuery();
            if (rs.next()) return extract(rs);
        } catch (SQLException e) { e.printStackTrace(); }
        return null;
    }

    public List<Employee> findAll() {
        List<Employee> list = new ArrayList<>();
        try (PreparedStatement ps = conn.prepareStatement("SELECT * FROM employees");
             ResultSet rs = ps.executeQuery()) {
            while (rs.next()) list.add(extract(rs));
        } catch (SQLException e) { e.printStackTrace(); }
        return list;
    }

    public void update(Employee emp) {
        String sql = "UPDATE employees SET name=?, email=?, department=?, salary=?, active=?, joining_date=?, age=? WHERE id=?";
        try (PreparedStatement ps = conn.prepareStatement(sql)) {
            ps.setString(1, emp.getName());
            ps.setString(2, emp.getEmail());
            ps.setString(3, emp.getDepartment());
            ps.setDouble(4, emp.getSalary());
            ps.setBoolean(5, emp.isActive());
            ps.setDate(6, emp.getJoiningDate());
            ps.setInt(7, emp.getAge());
            ps.setInt(8, emp.getId());
            ps.executeUpdate();
        } catch (SQLException e) { e.printStackTrace(); }
    }

    public void deleteById(int id) {
        try (PreparedStatement ps = conn.prepareStatement("DELETE FROM employees WHERE id=?")) {
            ps.setInt(1, id);
            ps.executeUpdate();
        } catch (SQLException e) { e.printStackTrace(); }
    }

    public List<Employee> findByDepartment(String dept) {
        List<Employee> list = new ArrayList<>();
        try (PreparedStatement ps = conn.prepareStatement("SELECT * FROM employees WHERE department=?")) {
            ps.setString(1, dept);
            ResultSet rs = ps.executeQuery();
            while (rs.next()) list.add(extract(rs));
        } catch (SQLException e) { e.printStackTrace(); }
        return list;
    }

    public void updateSalary(int id, double newSalary) {
        try (PreparedStatement ps = conn.prepareStatement("UPDATE employees SET salary=? WHERE id=?")) {
            ps.setDouble(1, newSalary);
            ps.setInt(2, id);
            ps.executeUpdate();
        } catch (SQLException e) { e.printStackTrace(); }
    }

    public boolean exists(int id) {
        try (PreparedStatement ps = conn.prepareStatement("SELECT COUNT(*) FROM employees WHERE id=?")) {
            ps.setInt(1, id);
            ResultSet rs = ps.executeQuery();
            return rs.next() && rs.getInt(1) > 0;
        } catch (SQLException e) { e.printStackTrace(); }
        return false;
    }

    private Employee extract(ResultSet rs) throws SQLException {
        return new Employee(
            rs.getInt("id"),
            rs.getString("name"),
            rs.getString("email"),
            rs.getString("department"),
            rs.getDouble("salary"),
            rs.getBoolean("active"),
            rs.getDate("joining_date"),
            rs.getInt("age")
        );
    }
}
```

✅ Full DAO implementation covering all required DB operations using JDBC best practices.

---

## 📄 FILE: `service/EmployeeService.java`

```java
package service;

import model.Employee;
import java.util.List;

public interface EmployeeService {
    void create(Employee emp);
    Employee get(int id);
    List<Employee> getAll();
    void update(Employee emp);
    void delete(int id);
    List<Employee> getByDepartment(String dept);
    void changeSalary(int id, double salary);
    boolean employeeExists(int id);
}
```

✅ Business abstraction layer.

---

## 📄 FILE: `service/EmployeeServiceImpl.java`

```java
package service;

import dao.*;
import model.Employee;
import java.util.*;

public class EmployeeServiceImpl implements EmployeeService {
    private final EmployeeDAO dao = new EmployeeDAOImpl();

    public void create(Employee emp) { dao.save(emp); }
    public Employee get(int id) { return dao.findById(id); }
    public List<Employee> getAll() { return dao.findAll(); }
    public void update(Employee emp) { dao.update(emp); }
    public void delete(int id) { dao.deleteById(id); }
    public List<Employee> getByDepartment(String dept) { return dao.findByDepartment(dept); }
    public void changeSalary(int id, double salary) { dao.updateSalary(id, salary); }
    public boolean employeeExists(int id) { return dao.exists(id); }
}
```

✅ Delegates all logic to DAO, ready for future business logic additions.

---

## 🧪 FILE: `MainApp.java`

```java
import model.Employee;
import service.*;

import java.sql.Date;
import java.util.*;

public class MainApp {
    public static void main(String[] args) {
        EmployeeService service = new EmployeeServiceImpl();
        Scanner sc = new Scanner(System.in);

        while (true) {
            System.out.println("\n=== Employee Management ===");
            System.out.println("1. Add | 2. View All | 3. View by ID | 4. Update | 5. Delete");
            System.out.println("6. Search by Dept | 7. Update Salary | 8. Exists | 9. Exit");
            System.out.print("Enter choice: ");
            int ch = sc.nextInt();

            switch (ch) {
                case 1: System.out.println("Enter id, name, email, dept, salary, active, date, age:");
                        Employee e = new Employee(sc.nextInt(), sc.next(), sc.next(), sc.next(),
                            sc.nextDouble(), sc.nextBoolean(), Date.valueOf(sc.next()), sc.nextInt());
                        service.create(e); break;

                case 2: service.getAll().forEach(System.out::println); break;
                case 3: System.out.println(service.get(sc.nextInt())); break;
                case 4: System.out.println("Enter updated details:");
                        Employee u = new Employee(sc.nextInt(), sc.next(), sc.next(), sc.next(),
                            sc.nextDouble(), sc.nextBoolean(), Date.valueOf(sc.next()), sc.nextInt());
                        service.update(u); break;
                case 5: service.delete(sc.nextInt()); break;
                case 6: sc.nextLine(); service.getByDepartment(sc.nextLine()).forEach(System.out::println); break;
                case 7: service.changeSalary(sc.nextInt(), sc.nextDouble()); break;
                case 8: System.out.println(service.employeeExists(sc.nextInt())); break;
                case 9: System.exit(0);
                default: System.out.println("Invalid choice.");
            }
        }
    }
}
```

✅ Switch-case based menu covering all features in one terminal UI.

