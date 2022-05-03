---
title: No space left on device
categories: 
    - spring 
    - designPattern 
---

### Singleton 
> <b>"소프트웨어 디자인패턴 중 한 종류"</b><br>
Spring의 Bean들은 모두 싱글톤 패턴트로 제공된다.<br>
"클래스의 인스턴스를 딱 한개만 생성"<br><br>
어떻게 ?? 아래 예제코드를 통해 확인해보자 


### 동작방식 및 예제코드 
```java
public class SingtonService {
    /***
     * 1. static 영역에 최초 1회만 생성   
     */
    private static final SingletonService instance = new SingletonService();
    
    /***
     * 2. 해당인스턴스가 필요할 때 
     *  외부에서 아래 public method로접근해 
     *  객체를 별도생성없이 가져다가 쓸 수 있다. 
     * ex) SingletonService instance = SingletonService.getInstance();
     * 
     */
    public static SingletonService getInstance(){
        return instance;
    }

    /***
     * 3. 생성자를 private으로 선언하여, 
     * 외부에서 new 키워드를 사용한 객체생성을 못하게 막음. 
     */
    private SingletonService() { 
        
    }
}
```

### Spring과 Singleton
> spring == 자바 엔터프라이즈 프레임웍 <br>
엔터프라이즈 == 기업을 대상으로하는 개발을 의미, <br>
는 동시에 서비스를 이용하고자하는 사용자가 많을것이라는 의미를 내포함.<br><br>
그래서~~ 싱글톤 패턴을 사용하지 않는다면, <br>
수많은 사용자들로인해 발생하는 요청을 수많은 스레드가 처리하는 과정마다 <br>
필요한 객체를 new new 하며 생성/삭제 해야할것이고, <br>
이는 시스템적 성능 저하 및 메모리가 낭비되는 결과를 초래 <br>
결국 Spring에서 싱글톤 패턴을 제공하는 이유는 <br>
위와 같은 비효율적인 자원낭비를 막기위해 모든 Bean을 싱글톤 객체로 생성해 모든 사용자들의<br>
Thread가 공유될 수 있도록 만든것이다.<br> 


