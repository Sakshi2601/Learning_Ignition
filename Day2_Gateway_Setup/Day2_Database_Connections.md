# Ignition Learning Notes - Day 2 

## Database Connections

Ignition connects to SQL databases to store tag history, alarms, transaction groups, and project data. Each database type needs correct drivers and proper configuration.

---

## 1. MySQL Connection

### Steps:

1. **Load MySQL Driver**

   * Download `mysql-connector-java-x.x.jar`.
   * Upload in Gateway → *Config > Databases > Drivers*.

2. **Create Database Connection**

   * Gateway → *Config > Databases > Connections*.
   * JDBC URL example:

     ```
     jdbc:mysql://localhost:3306/databasename
     ```
   * Default Port: **3306**.

3. **Other Notes**

   * Make sure MySQL service is running.
   * Allow remote connections if using another machine.

---

## 2. Microsoft SQL Server (MS SQL)

### Pre-Configuration:

1. Open **SQL Server Configuration Manager**.
2. Enable **TCP/IP** under SQL Server Network Configuration.
3. Right-click TCP/IP → Properties → Set ports (usually **1433**).
4. Restart SQL Server service.

### Create Connection

* In Gateway → *Databases > Connections*.
* JDBC URL examples:

  * Using instance name:

    ```
    jdbc:sqlserver://localhost;instanceName=SQLEXPRESS;databaseName=mydb
    ```
  * Using port:

    ```
    jdbc:sqlserver://localhost:1433;databaseName=mydb
    ```

---

## 3. PostgreSQL

### Connection Steps:

* PostgreSQL driver comes built-in with Ignition.
* Gateway → *Database Connections*.
* JDBC URL:

  ```
  jdbc:postgresql://localhost:5432/databasename
  ```
* Default Port: **5432**.

---

## 4. Oracle Database

### Steps:

1. Download Oracle driver `ojdbc8.jar` or `ojdbc11.jar`.
2. Upload it in Gateway → *Databases > Drivers*.

### Create Connection

* JDBC example:

  ```
  jdbc:oracle:thin:@localhost:1521/orcl
  ```
* Default port: **1521**.

---

## Summary

* **MySQL:** upload driver → connect on *3306*.
* **MS SQL:** enable TCP/IP → instance or port *1433*.
* **PostgreSQL:** built-in driver → port *5432*.
* **Oracle:** upload `ojdbc.jar` → port *1521*.

---

**End of Day 2 — Database Notes**
