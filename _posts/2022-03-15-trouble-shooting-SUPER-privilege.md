---
title: \[TroubleShooting-RDS\] You do not have the SUPER privilege
---
##   
> MariaDB에서 시퀀스 사용을위해 function을 추가하려했지만 다음과같은 오류가 발생했다.

## 에러발생 :
```
[HY000][1419] You do not have the SUPER privilege and binary logging is enabled (you *might* want to use the less safe log_bin_trust_function_creators variable)
```
## 해결 : 
> RDS 파라미터그룹의 log_bin_trust_function_creators variable 값을 1로 변경
