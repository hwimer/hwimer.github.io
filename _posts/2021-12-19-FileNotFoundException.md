---
title: \[TroubleShooting\] resource.getFile FileNotFoundException 
---
## getFile() 은안되고, getInputStream은 되는이유
 
### 문제발생
```
외부 .json파일을 가져와 사용하는 소스를 배포하였으며,
구동중 FileNotFoundException 발생. 
```

### 사실수집
``` java
-- 외부 json파일을 가져와서 사용하기위해 
-- .resource.getFile() 메소드를 사용하였으나, build,deploy후 구동중 FileNotFoundException이 발생.
String filePath = "/com/pack/abcabc.json";
FileReader fr = new FileReader(resource.getFile());
```

### WHY?

```
Spring에서 classpath에 있는 여러가지 resource를 처리하기위해 Resource라는 인터페이스의 구현체인 
ClassPathResource를 제공함. 해당 기능으로 파일 객체로 변환시켜 여러 처리를 하게되는데,

IDE환경에서 실행했다면, 실제 resource파일인 file://프로토콜을 사용하기 때문에 File객체를 생성 할 수 있지만,
executable jar로 실행했다면, FileNotFoundException 예외가 발생
executable jar는 jar파일 하나에 컴파일된 class file, resource와 nested jar들로 구성됨
여기서 resource의 URL은 jar://로 시작하는 주소를 갖게됨.
해당프로토콜로 classloader가 원만한 작업을 할 수 있음 
하지만 getFile을 실제 filesystem에서 지원하는 프로토콜로 처리를 해야함.
그래서 jar실행 환경에서는 사용할 수 없음. 
getInpuStream으로 classloader에 위임처리를 해야함.

```

### 조사방법결정
```
getFile을 jar실행 환경에서는 사용할 수 없음.
아래와같이 getInpuStream을통해 classloader에 위임 처리를 해야함.
```
### 조사방법구현 
``` java
String filePath = "/com/pack/abcabc.json";
FileReader fr = new FileReader(resource.getInputStream());
```

### 경과관찰


### 문제해결
