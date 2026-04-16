# Easy_Crud
EasyCRUD is a full-stack web application that performs CRUD operations on student data using RESTful APIs and a MariaDB database, demonstrating efficient client–server communication and database management.

# MariaDB Setup and Configuration 

This guide provides clear steps to install, secure, and configure **MariaDB** for backend development. It also explains how to create a database, configure a database user, and prepare credentials required to connect your backend application.

This setup is commonly used in full-stack and backend projects where a service needs reliable database connectivity.

---

# 1. Install MariaDB

## For Ubuntu / Linux

Update system packages and install MariaDB server:

```bash
sudo apt update
sudo apt install mariadb-server -y
```

After installation, verify that the MariaDB service is running:

```bash
sudo systemctl status mariadb
```

---

# 2. Secure MariaDB Installation

Run the built-in security script to apply recommended security settings.

```bash
mysql_secure_installation
```

During the setup, configure the following:

* Set a strong **root password**
* Remove anonymous users
* Disable remote root login
* Remove test database
* Reload privilege tables

These steps help protect your database environment in development and production.

---

# 3. Configure Database and User

Login to the MariaDB server:

```bash
mysql -u root -p
```

Enter the root password when prompted.

## Create a Database

```sql
CREATE DATABASE student_db;
```

## Create a Database User and Grant Permissions

```sql
GRANT ALL PRIVILEGES ON student_db.* 
TO 'username'@'localhost' 
IDENTIFIED BY 'your_password';
```

Replace:

* `username` → your database username
* `your_password` → your secure password

Apply changes:

```sql
FLUSH PRIVILEGES;
```

Exit the MariaDB shell:

```sql
EXIT;
```

---

# 4. Backend Database Configuration

To connect your backend application (Spring Boot / Node.js / Express / etc.) with the database, configure the following environment variables or application properties.

```env
DB_HOST=localhost
DB_PORT=3306
DB_NAME=student_db
DB_USER=username
DB_PASS=your_password
```

These credentials are required for:

* Database connection
* API data operations
* CRUD functionality
* Backend service initialization

---

# Developer Notes 
* Always use **environment variables** instead of hardcoding credentials
* Use strong passwords for database users
* Limit privileges in production environments
* Keep database and application configurations separated
* Enable logging for debugging and monitoring

---

# Changes Made by Developer

* Configured MariaDB database for backend integration
* Created dedicated database user with required privileges
* Prepared environment-based database credentials
* Secured database installation using recommended settings

---

This configuration ensures a stable and secure database setup for modern backend applications and full-stack development workflows.
