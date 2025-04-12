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
