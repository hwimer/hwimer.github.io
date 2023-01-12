---
title: "Spring 구동순서"
categories: 
  - spring 
toc: true
toc_sticky: true
toc_label: Content 
---



### 구동순서
----
1. web.xml이 로딩됨
   1. tomcat에의해 
2. ContextLoaderListener 생성
   1. 
### 내가 생각하는 Stream 이란?? 
> 자바 Collection을 Framework를 유연하게 핸들링하는 표준 라이브러리이다. 


### 이점 : 
- 무분별한 loop방지 결국 가독성??
### Before
```java
@Controller
public class UserController {
    
    private UserService userService;
    
    public UserController(UserService userService){
       this.userService = userService; 
    }
}
```

### After

```java
@Controller
@RequiredArgsConstructor
public class UserController {
    
    private final UserService userService;
}
```


### Reference :
- [Spring Framework 구동순서 완벽정리](https://yoo-hyeok.tistory.com/139)


