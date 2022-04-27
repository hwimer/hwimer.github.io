---
title: Persistence 
categories : 
  - spring
---
## Persistence(영속성)
> Persistence란??<br>
프로그램종료시 데이터는 메모리에만 존재하기때문에 사라짐.<br>
이를 해결하기 위해 파일시스템과 관계형데이터베이스를 활용하여 구현함.<br>
데이터가 영속성을 가지기 위해 Spring에서 사용하는 방법은 아래와 같음.

1. JDBC(Java)
2. Spring JDBC
3. Persistence Framework

## Persistence Framework
> Persistence Framework란 "자료를 DB에 저장하는 과정을 도와주는 소프트웨어"<br>
데이터를 가공하는 자바 객체층과 데이터를 저장하는 <br>
DB층 사이를 매끄럽게 연결하는 이음매라고 할 수 있음.<br>
Persistence Framework에는 ORM과 SQL Mapper가 있음. 

## SQL Mapper란??
> 객체와 관계형 DB의 데이터를 개발자가작성한 SQL로 매핑시켜주는 <br> 
Persistence Framework의 한 종류.<br>
개발자가 직접 SQL을 작성해야하며, <br>
SQL문을 실행하고 얻은 데이터를 객체로 매핑해줌. <br><br>
하지만.. 단순 CRUD시 매번 매핑하기위해 Mybatis를 작성하는 노가다아닌 노가다를 해야함<br>
이를 해결하기위한 mybatis generate라는 기똥찬 플러그인이 있음. 


### 장점:
- SQL에대한 이해도가 있다면, 수월하게 사용가능.
- 세부적인 SQL변경시, 편리함

### 단점: 
- 네?? 뭐라구요?? DB를 변경해야한다구요?? (DBMS에 종속적임) 


## ORM(Object-relational mapping)이란?
> ORM이라는 기술이있음.<br>
이 기술은 객체와 테이블을 연결하기위한 기술이다.


### 장점: 
> prefix: (이 기술을사용하면)
- 쿼리에 집중할 필요 없이, 빠르게 개발가능 (비즈니스로직에만 집중할 수 있음)
- DBMS에 종속적이지 않음.
- 재사용에 용이함.

### 단점:
> prefix : (이기술을 사용하면) 
- 프로젝트의 복잡성이 커질경우, 난이도 상승
- 잘못 적용시, 속도저하발생
- 복잡한 SQL을 사용하지못함.

## JPA란???
> ORM기술을 자바진영에서 사용하기위해 정의된 인터페이스이다.(그저 설명서이다..)
자바진영에서 관계형DB를 사용하는 방식을 정의한 인터페이스이다. 

## Hibernate:
> 위에있는 JPA인터페이스(설명서)를 구현받은 구현체의 한 종류이다.(실체)<br>
굳이(?).. 비교하자면 떡볶이 레시피가있고, 이것을 엽기떡볶이가 만드느냐,<br>
배떡이만드느냐의 차이임.

