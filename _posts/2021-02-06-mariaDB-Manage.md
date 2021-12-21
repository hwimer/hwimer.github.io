---
title: management of maria
---

## to connect mariaDB console through root account 

### connect
 
```
${mariadb bin dir}\msyql -uroot -p
```


```sql
USE mysql
```

#### SELECT USER LIST
```sql
SELECT HOST,USER,PASSWORD FROM USER
```

### CREATE 
```sql
CREATE USER '${user.id}'@'%' IDENTIFIED BY '${password}';
```
### PERMISSION

```sql
GRANT ALL PRIVILEGES ON ${db.name}.* TO '${user.id}'@'%';
FLUSH PRIVILEGES;
```


### DELETE ACCOUNT
```sql
DROP USER ${user.id}@${host}
```
