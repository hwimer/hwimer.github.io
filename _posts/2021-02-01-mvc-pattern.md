---
title: mvc pattern
categories: 
    - spring 

---

### MVC
> MVC = model + view + controller  

- model : 
	- 애플리케이션에서 사용되는 데이터와 그 데이터를 처리하는 부분
- view : 
	- 사용자에게 보여지는 UI
- controller : 
	- 사용자의 행동에 대해서 처리하는 부분

### flow
1. 사용자의 action이 Controller에 들어옵니다.
2. Controller는 사용자의 action을 확인하고, model 을 업데이트합니다.
3. Controller는 Model을 나타내줄 View를 선택합니다.
4. View는 Model을 이용하여 화면을 나타냅니다.


### 장점 : 
SIMPLE
보편적으로 많이 사용되는 디자인 패턴

### 단점 : 
높은의존성  
애플리케이션이 커질수록 유지보수가 어려움.
