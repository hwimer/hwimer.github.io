---
title: Try Catch, Throw Exception
categories: 
  - Java
  - CS
---

## 
> 글의기원은 Spring의 Transaction처리는 
> 기본적으로는.. RunTime계열은 rollback하고, Unchecked 계열은 rollback하지않음.
> 그것은 어디까지나 기본적인 동작임..
> Spring Transaction은 옵션으로 우리가 설정할 수 있게끔
> 런타임 예외 중에서도 이러 이러한 예외는 롤백을 하지않게끔 설정할 수 있고, 
> UnChecked 예외중에서도 이러이러한 롤백은 반대로 롤백을 하게끔 설정 할 수있음. 
> 
> Spring Transaction의 기본 전략으로 모든 예외를 업무에서 처리하지않기 때문에 

## Error와 Exception
### 오류(Error)란??
> 오류는 "시스템에 비정상적인 상황이 생겼을 때 발생".
> 개발자가 미리 예측X 
> 때문에 오류에 대한 처리를 신경쓰지 않아도 됨.


### 예외(Exception)란??
> 예외란, "개발자가 구현한 로직에서 발생"
> 따라서 발생할 상황을 미리 예측해 처리할 수 있음.
> 때문에 예외를 구분하고, 그에 따른 처리방법을 명확히 알고 적용하는것이 중요



<div class="mermaid"> 
  graph TD; 
Object-->Throwable; Throwable-->Error; Throwable-->Exception;
Exception-->CheckedException;
Exception-->RuntimeException;
RuntimeException-->UncheckedException;
</div>

> 모든 예외클래스는 Throwable클래스를 상속받고 있고, Throwable은 최상위 클래스 Object의 자식 클래스이다.
> Exception은 수많은 자식클래스를 가지고 있다. 그 중 RuntimeException을 주목해야함.
> RuntimeException은 CheckException과 UncheckedException을 구분하는 기준이다.
> Exception의 자식 클래스 중 RuntimeException을 제외한 모든 클래스는 CheckedException이며, RuntimeException과
> 그의 자식 클래스들을 Unchecked Exception이라 한다. CheckedException과 Unchecked Exception에 대해


|| checkedException |uncheckedException|
|------------------|--|---|
| 처리여부             |예외처리 필수|명시적인 처리를 강제하지 않음.|
| 확인시점             |컴파일 단계|실행단계|
| 트랜잭션처리             |rollback(X)|rollback(O)|
| 대표예외 |- IOException |- NullPointException|
| |- SQLException | - IllegalArgumentException|
| | | - IndexOutOfBoundException|
| | | - SystemException|

> Checked Exception과 Unchecked Exception의 명확한 기준은 
> "꼭 처리를 해야하는가?" 이다. Checked Exception이 발생할 가능성이 있는 메소드라면,
> 반드시 로직을 try/catch로 감싸거나 throw로 던져서 처리해야한다.
> 반면에 Unchecked Exception은 명시적으로 예외처리를 하지 않아도 된다.
> 이 예외는 피할 수 있지만 개발자가 부주의해서 발생하는 경우가 대부분이고 미리 예측하지
> 못했던 상황에서 발생하는 예외가 아니기 때문에 굳이 로직으로 처리를 할 필요가 없도록 만들어져 있음.
> 
> 또한 예외를 확인할 수 있는 시점에서도 구분할 수 있음.
> 일반적으로 컴파일 단계에서 명확하게 Exception 체크가 가능한 것을 Checked Exception이라 하며,
> 실행과정 중 어떠한 특정 논리에 의해 발견되는 Exception을 Unchecked Exception이라고 한다.
> 따라서 컴파일 단계에서 확인할 수 없는 예외라고해서 Unchecked Exception이며, 실행과정중에 발견된다고 해서 
> RuntimeException이라고 하는 것임.
> 
> 예외발생시 트랜잭션의 roll-back 여부이다. 기본적으로 Checked Exception은 예외발생시,
> Transaction을 roll-back하지 않고, 예외를 던져줌. 하지만 Unchecked Exception은 예외 발생시
> Transaction을 roll-back처리함. 어떻게 묶어놓느냐에 따라서 Checked Exception이냐, Unchecked Exception이냐 영향도가 큼.
> roll-back이 되는 범위가 달라지기 때문에 개발자가 이를 인지하지 못하면, 실행결과가 맞지 않거나 예상치 못한 예외가 발생할 수 있음. 
> 그러므로 이를 인지하고 트랜잭션을 적용시킬 때, 전파방식(propagation behavior)과 롤백규칙 등을 적절히 활용하면 
> 더욱 효과적인 애플리케이션을 구현할 수 있다. 
