---
title: "@RequiredArgsConstructor"
categories: 
  - spring 
toc: true
toc_sticky: true
toc_label: Content 
---



### RequiredArgsConstructor 란??
> <b>생성자</b>를통한 의존성주입을 간결하게 설정하는 애노테이션이다.

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


