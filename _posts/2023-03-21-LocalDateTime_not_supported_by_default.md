---
title: LocalDateTime_not_supported_by_default
categories: 
    - troubleShooting 
---

### LocalDateTime_not_supported_by_default

### 줄거리  
토이프로젝트를 진행하면서 특정이벤트가 발생했을때, 데이터를 적재하는 로직이있었다. <br>
row를 적재하는시점에 적재되는 시간이들어가는 created_at 컬럼이 있었는데, <br>
자동으로 now()값이아닌, null로 채워지지 않는 증상이 있었고, 자동으로 값을 채워주기위해 테이블 scheme을 다음과같이 수정하였다. <br>

#### before 
````sql 
...
    created_at  datetime     DEFAULT NULL,
...
````

#### after 

``` sql
...
    created_at  datetime     DEFAULT CURRENT_TIMESTAMP,
...

```


### 오류발생 
변경해주고나서, row를 적재시, 변경된 컬럼에는 now()값으로 잘 치환되어 값이 적재되었고, <br>
적재된 row를 화면에 표출하기위해 행(엔티티)을 DTO로 매핑하는과정에서 위와같은 오류가 발생하였다.<br>

```
[ERROR] 2023-03-21 23:31:45.243 [http-nio-8100-exec-2] org.apache.catalina.core.ContainerBase.[Tomcat].[localhost].[/].[dispatcherServlet] - Servlet.service() for servlet [dispatcherServlet] in context with path [] threw exception [Request processing failed; nested exception is java.lang.IllegalArgumentException: Java 8 date/time type `java.time.LocalDateTime` not supported by default: add Module "com.fasterxml.jackson.datatype:jackson-datatype-jsr310" to enable handling (through reference chain: java.util.ArrayList[0]->com.kokn.paperround.entity.Keyword["createdAt"])] with root cause
com.fasterxml.jackson.databind.exc.InvalidDefinitionException: Java 8 date/time type `java.time.LocalDateTime` not supported by default: add Module "com.fasterxml.jackson.datatype:jackson-datatype-jsr310" to enable handling (through reference chain: java.util.ArrayList[0]->com.kokn.paperround.entity.Keyword["createdAt"])
	at com.fasterxml.jackson.databind.exc.InvalidDefinitionException.from(InvalidDefinitionException.java:77)
	at com.fasterxml.jackson.databind.SerializerProvider.reportBadDefinition(SerializerProvider.java:1300)
	at com.fasterxml.jackson.databind.ser.impl.UnsupportedTypeSerializer.serialize(UnsupportedTypeSerializer.java:35)
	at com.fasterxml.jackson.databind.ser.BeanPropertyWriter.serializeAsField(BeanPropertyWriter.java:728)
	at com.fasterxml.jackson.databind.ser.std.BeanSerializerBase.serializeFields(BeanSerializerBase.java:774)
	at com.fasterxml.jackson.databind.ser.BeanSerializer.serialize(BeanSerializer.java:178)
	at com.fasterxml.jackson.databind.ser.impl.IndexedListSerializer.serializeContents(IndexedListSerializer.java:119)
	at com.fasterxml.jackson.databind.ser.impl.IndexedListSerializer.serialize(IndexedListSerializer.java:79)
	at com.fasterxml.jackson.databind.ser.impl.IndexedListSerializer.serialize(IndexedListSerializer.java:18)
	at com.fasterxml.jackson.databind.ser.DefaultSerializerProvider._serialize(DefaultSerializerProvider.java:480)
	at com.fasterxml.jackson.databind.ser.DefaultSerializerProvider.serializeValue(DefaultSerializerProvider.java:319)
	at com.fasterxml.jackson.databind.ObjectMapper._convert(ObjectMapper.java:4371)
	at com.fasterxml.jackson.databind.ObjectMapper.convertValue(ObjectMapper.java:4334)
	...
```

### 원인 

> This issue occurs when you are trying to serialize or deserialize a Java object that includes a LocalDateTime property using the Jackson library. By default, Jackson does not support LocalDateTime

필자는 엔티티를 DTO로 변환하는 과정에서 jackson 라이브러리를 사용했고, <br>
jackson을 사용할때, 변환하려는객체에 LocalDateTime이라는 타입이 포함되어있는경우, serialize 혹은, deserialize를 지원하지않는다.<br>
이를 가능케하기위해 Jackson에서는 아래와같은 별도의 라이브러리를 제공한다. <br>

> com.fasterxml.jackson.datatype:jackson-datatype-jsr310

### 사용법 

#### 라이브러리추가 
pom.xml 혹은 build.gradle에 위에명시된 라이브러리를 추가한다. (추가된 라이브러리는 JavaTimeModule 클래스를 제공한다.)

#### ObjectMapper 객체생성 
메세지를 컨버팅하기위한 객체를 생성하는데, <br>
LocalDateTime을 컨버팅하기위해 기존의 생성방식과는 조금다르게, 아래처럼 모듈을 등록해주어야한다. <br>

##### before 
``` java
        ObjectMapper om = new ObjectMapper();
```
##### after 
``` java
        ObjectMapper om = new ObjectMapper().registerModule(new JavaTimeModule());
```

### 해결완료