---
title: Persistence 
---
## Persistence(영속성)
> 프로그램종료시 데이터는 메모리에만 존재하기때문에 사라짐.
> 이를 해결하기 위해 파일시스템과 관계형데이터베이스를 활용하여 구현함.

> 데이터가 영속성을 가지기 위해 Spring에서 사용하는 방법은 아래와 같음.

- JDBC(Java)
- Spring JDBC
- Persistence Framework

## Persistence Framework
> 자료를 DB에 저장하는 과정을 도와주는 소프트웨어임.
> 데이터를 가공하는 자바 객체층과 데이터를 저장하는 DB층 사이를 매끄럽게 연결하는 이음매임.
> Persistence Framework에는 ORM과 SQL Mapper가 있다. 

## SQL Mapper란??
> 객체와 관계형 데이터베이스의 데이터를 개발자가 작성한 SQL로 매핑시켜주는 Persistence Framework의 한 종류.
> 개발자가 직접 SQL을 작성해야하고, SQL문을 실행하고 얻은 데이터를 객체로 매핑.

### 장점:
- SQL에대한 이해도가 있다면, 수월하게 사용가능.
- 세부적인 SQL변경시, 편리함

### 단점: 
- DBMS에 따라 SQL문법이 다르기 때문에 DBMS에 종속적이다 


## ORM(Object-relational mapping)이란?
> 객체와 관계형 데이터베이스는 따로 설계됨
> "객체" 와 "테이블"을 연결하기위한 Persistence Framework의 한 종류.

### 장점: 
- 쿼리에 집중할 필요 없이, 빠르게 개발가능 (비즈니스로직에만 집중할 수 있음)
- DBMS에 종속적이지 않음.
- 재사용에 용이함.

### 단점:
- 프로젝트의 복잡성이 커질경우, 난이도 상승
- 잘못 적용시, 속도저하발생
- 복잡한 SQL을 사용하지못함.

## JPA란???
> Java Persistence API
> Java진영의 ORM기줄 표준(인터페이스)
> 자바 애플리케이션에서 관계형 데이터를 사용하는 방식을 정의한 인터페이스.

## Hibernate:
> 위에있는 JPA인터페이스를 구현받은 구현체의 한 종류.


