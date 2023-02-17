---
title: MariaDB Grant 
categories: 
    - database 


---


### Show User 
```sql
SELECT HOST,USER,PASSWORD FROM USER
```

### Generate User  
```sql
CREATE USER '${user.id}'@'%' IDENTIFIED BY '${password}';
```
### Grant  

```sql
GRANT ALL PRIVILEGES ON ${db.name}.* TO '${user.id}'@'%';
FLUSH PRIVILEGES;
```

### Delete User 
```sql
DROP USER ${user.id}@${host}
```
