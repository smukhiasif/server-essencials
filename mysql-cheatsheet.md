# 🐬 MySQL Basic Commands Cheat Sheet

A quick reference guide for essential MySQL commands, great for developers and DB admins.

---

## 🔐 1. Login to MySQL
```bash
mysql -u root -p
```

## 🧑‍💻 2. Show All Users
```bash
SELECT User, Host FROM mysql.user;
```

## 🛢 3. Show All Databases
```bash
SHOW DATABASES;
```

## 📦 4. Create a Database
```bash
CREATE DATABASE my_database;
```

## 🗑 5. Drop a Database
```bash
DROP DATABASE my_database;

## 📂 6. Use a Database
```bash
USE my_database;
```

## 📄 7. Show All Tables
```bash
SHOW TABLES;
```

## 🧱 8. Create a Table
```bash
CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  email VARCHAR(100) UNIQUE
);
```

## 🗑 9. Drop a Table
```bash
DROP TABLE users;
```

## 🧾 10. Show Table Structure
```bash
DESCRIBE users;
-- or
SHOW COLUMNS FROM users;
```

## 🧮 11. Insert Data

```bash
INSERT INTO users (name, email) VALUES ('John Doe', 'john@example.com');
```

## 📋 12. Select Data
```bash
SELECT * FROM users;
SELECT name FROM users WHERE id = 1;
```

## ✏️ 13. Update Data
```bash
UPDATE users SET email = 'john.doe@example.com' WHERE id = 1;
```

## ❌ 14. Delete Data
```bash
DELETE FROM users WHERE id = 1;
```

## 🔐 15. Create User
```bash
CREATE USER 'new_user'@'localhost' IDENTIFIED BY 'password';
```

## 🔑 16. Grant Privileges
```bash
GRANT ALL PRIVILEGES ON my_database.* TO 'new_user'@'localhost';
FLUSH PRIVILEGES;
```

## 🚫 17. Revoke Privileges
```bash
REVOKE ALL PRIVILEGES ON my_database.* FROM 'new_user'@'localhost';
```
## 🧾 18. Show Grants for a User
```bash
SHOW GRANTS FOR 'new_user'@'localhost';
```
## 🔁 19. Change User Password
```bash
ALTER USER 'new_user'@'localhost' IDENTIFIED BY 'newpassword';
```

## 🚮 20. Delete User
```bash
DROP USER 'new_user'@'localhost';
```

## 📦 21. Export Database (Backup)
```bash
mysqldump -u root -p my_database > backup.sql
```

## 📥 22. Import SQL File

```bash
mysql -u root -p my_database < backup.sql
```

## 🔍 23. Search for a Column in All Tables

```bash
SELECT table_name 
FROM information_schema.columns 
WHERE table_schema = 'my_database' AND column_name = 'email';
```

## 🧠 24. Check Current User

```bash
SELECT CURRENT_USER();
```

## 📅 25. Show Current Date & Time

```bash
SELECT NOW();
```

## 🔧 26. List All Engines

```bash
SHOW ENGINES;
```

✅ Tip: Use \q to exit MySQL CLI.
