---

[//]: # (title: You do not have the SUPER privilege)
title: You do not have the SUPER privilege
categories: 
    - troubleShooting
    - database 

---


## 오류: 
> MariaDB(AWS-RDS)에서 시퀀스 사용을 위해 function을 추가하려고했지만, <br>
> 다음과같은 오류가 발생.

```text
[HY000][1419] You do not have the SUPER privilege and binary logging is enabled (you *might* want to use the less safe log_bin_trust_function_creators variable)
```

## 해결 : 
> RDS 파라미터그룹의 log_bin_trust_function_creators variable 값을 1로 변경
