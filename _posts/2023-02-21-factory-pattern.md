---
title: Factory Pattern 
categories: 
    - designPattern 
---

### Factory Pattern 
Factory Pattern == 소프트웨어 디자인패턴 in OOP 

> the Factory Pattern provides a way to create objects 
without specifying the exact class of object that will be created 

생성될 객체의 정확한 클래스를 지정하지않고, 객체를 생성하는방법이라고한다. <br>
음... 이게무슨말일까?? <br>


> Instead of directly creating an object using the "new" keyword, a factory method is used to create object. 
This factory method can be defined in an interface or an abstract class, and each subclass can implement this method
in their own way to create objects of the appropriate type. 


우리가 객체를 사용하기위해 보통은 애플리케이션 코드에서 new 키워드를 사용해 객체를 생성하고,<br>
객체에있는 메소드를 호출해서 사용을한다. (보통은) <br>
그러나 팩토리패턴은, 애플리케이션 코드에서 new 키워드를 호출해 객체를 생성하는방식이아닌, <br>
팩토리 클래스를 통해 객체를 생성하는방법을 이야기한다. <br>




### 배경: 

애플리케이션단에서 new 키워드를 통해 생성된 객체는 다른코드들과 밀접하게 "결합"된 코드로 이어지는 경우가 많았다. <br>
이로인해 코드의 다른부분에 영향을주지않고 객체를 생성방식을 변경하기가 어려웠다. <br>

팩토리패턴은 객체생성을 담당하는 별도의 팩토리클래스를 정의해 이 문제를 해결한다.<br>
팩토리클래스는 생성될 객체의 내부를 보이지않게 캡슐화하고, 나머지 코드가 객체 구성의 세부사항을 알 필요 없이 <br>
간단한 인터페이스를 사용하여 객체를 만들 수 있도록 하였음. <br>


### 장점: 

1. 느슨한 결합 <br>
객체와 애플리케이션 코드간의 결합도가 낮아진다. <br>
2. 확장성<br>
기존코드 변경없이 새로운 타입의 객체를 추가해 확장할 수 있음. <br>


### 사용방법: 

1. 인터페이스생성 및 메소드정의 <br>
2. 자식클래스 구현 및 메소드 재정의 <br>
자식클래스를 생성하여 위 절차에서 생성된 인터페이스를 구현받고, <br>
인터페이스의 메소드를 재정의한다. (Override)
3. 팩토리클래스 생성 <br>
4. 팩토리클래스를 통한 자식객체 생성<br>





### 예제 

``` java 

// 1. 메세지를 전송하기위한 인터페이스(부모) 
public interface SendMessageService {

    void send();

}




// 2. SendMessageService 인터페이스를 구현받은 자식클래스 
public class SendMessageService_신한 extends SendMessageService {
    
    @Override
    public send(){

        // Send Something 
    }

}

// 2-2. SendMessageService 인터페이스를 구현받은 자식클래스 
public class SendMessageService_농협 extends SendMessageService {
    
    @Override
    public send(){

        // Send Something 
    }

}
// 2-3. SendMessageService 인터페이스를 구현받은 자식클래스 
public class SendMessageService_하나 extends SendMessageService {
    
    @Override
    public send(){

        // Send Something 
    }

}

// 3. 그리고 팩토리
public class SendMessageFactory {
  
  public static SendMessageService getPartner(String partner){


      switch (partner){
          case "신한": return new SendMessageService_신한();
          case "농협": return new SendMessageService_농협();
          case "하나": return new SendMessageService_하나();
      }

  }


}


// 4. 애플리케이션 코드
public void integrateMessage(String partner){
  
    // ...

    SendMessageService sendService = SendMessageFactory.getPartner(partner);
    sendService.send();

}

```




