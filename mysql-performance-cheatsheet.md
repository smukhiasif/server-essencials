
# 🐬 MySQL Basic Commands Cheat Sheet

A quick reference guide for essential MySQL commands, great for developers and DB admins.

---

## 🔐 1. Login to MySQL
```bash
mysql -u root -p
```

---

## 🧑‍💻 2. Show All Users
```sql
SELECT User, Host FROM mysql.user;
```

---

## 🛢 3. Show All Databases
```sql
SHOW DATABASES;
```

---

## 📦 4. Create a Database
```sql
CREATE DATABASE my_database;
```

---

## 🗑 5. Drop a Database
```sql
DROP DATABASE my_database;
```

---

## 📂 6. Use a Database
```sql
USE my_database;
```

---

## 📄 7. Show All Tables
```sql
SHOW TABLES;
```

---

## 🧱 8. Create a Table
```sql
CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  email VARCHAR(100) UNIQUE
);
```

---

## 🗑 9. Drop a Table
```sql
DROP TABLE users;
```

---

## 🧾 10. Show Table Structure
```sql
DESCRIBE users;
-- or
SHOW COLUMNS FROM users;
```

---

## 🧮 11. Insert Data
```sql
INSERT INTO users (name, email) VALUES ('John Doe', 'john@example.com');
```

---

## 📋 12. Select Data
```sql
SELECT * FROM users;
SELECT name FROM users WHERE id = 1;
```

---

## ✏️ 13. Update Data
```sql
UPDATE users SET email = 'john.doe@example.com' WHERE id = 1;
```

---

## ❌ 14. Delete Data
```sql
DELETE FROM users WHERE id = 1;
```

---

## 🔐 15. Create User
```sql
CREATE USER 'new_user'@'localhost' IDENTIFIED BY 'password';
```

---

## 🔑 16. Grant Privileges
```sql
GRANT ALL PRIVILEGES ON my_database.* TO 'new_user'@'localhost';
FLUSH PRIVILEGES;
```

---

## 🚫 17. Revoke Privileges
```sql
REVOKE ALL PRIVILEGES ON my_database.* FROM 'new_user'@'localhost';
```

---

## 🧾 18. Show Grants for a User
```sql
SHOW GRANTS FOR 'new_user'@'localhost';
```

---

## 🔁 19. Change User Password
```sql
ALTER USER 'new_user'@'localhost' IDENTIFIED BY 'newpassword';
```

---

## 🚮 20. Delete User
```sql
DROP USER 'new_user'@'localhost';
```

---

## 📦 21. Export Database (Backup)
```bash
mysqldump -u root -p my_database > backup.sql
```

---

## 📥 22. Import SQL File
```bash
mysql -u root -p my_database < backup.sql
```

---

## 🔍 23. Search for a Column in All Tables
```sql
SELECT table_name 
FROM information_schema.columns 
WHERE table_schema = 'my_database' AND column_name = 'email';
```

---

## 🧠 24. Check Current User
```sql
SELECT CURRENT_USER();
```

---

## 📅 25. Show Current Date & Time
```sql
SELECT NOW();
```

---

## 🔧 26. List All Engines
```sql
SHOW ENGINES;
```

---

✅ Tip: Use `\q` to exit MySQL CLI.

---

# ⚡️ MySQL Performance Tuning Tips

Optimize your MySQL server and queries for better performance and efficiency.

---

## 🔧 Server-Level Tuning

### 1. Increase InnoDB Buffer Pool Size
```ini
innodb_buffer_pool_size = 1G
```

### 2. Enable Query Cache (MySQL < 5.7)
```ini
query_cache_type = 1
query_cache_size = 64M
```

### 3. Adjust Thread and Connection Settings
```ini
max_connections = 200
thread_cache_size = 50
```

### 4. Set Slow Query Logging
```ini
slow_query_log = 1
slow_query_log_file = /var/log/mysql/slow-queries.log
long_query_time = 2
```

---

## 📦 Table & Index Optimization

### 5. Use Indexes Wisely
```sql
CREATE INDEX idx_user_email ON users(email);
```

### 6. Avoid SELECT *
```sql
SELECT name, email FROM users WHERE id = 1;
```

### 7. Use EXPLAIN for Query Analysis
```sql
EXPLAIN SELECT * FROM orders WHERE customer_id = 101;
```

---

## 🔁 Query Optimization

### 8. Prefer JOINs Over Subqueries
```sql
SELECT u.* FROM users u JOIN orders o ON u.id = o.user_id;
```

### 9. Use LIMIT with OFFSET
```sql
SELECT * FROM products ORDER BY created_at DESC LIMIT 10 OFFSET 20;
```

---

## 🧹 Maintenance

### 10. Analyze & Optimize Tables
```sql
ANALYZE TABLE users;
OPTIMIZE TABLE users;
```

---

## 📊 Monitoring Tools
- mysqltuner.pl
- pt-query-digest (Percona Toolkit)
- MySQL Enterprise Monitor
- Grafana + Prometheus

---

💡 Tip: After changing configs, restart MySQL:
```bash
sudo systemctl restart mysql
```

---
