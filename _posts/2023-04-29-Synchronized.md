---
title: Synchronized Method  
categories: 
    - Java
---

### Synchronized 메소드란? 

Synchornized Method == 멀티스레드 환경에서 Thread Safe 하기위한 메소드 <br><br><br>


### 용도

  멀티스레드 환경에서 여러 스레드가 하나의 공유자원에 <b>동시에</b> 접근하지 못하도록 막는것을 의미한다. <br><br><br>



### 동작원리

> When a thread enters a synchronized method, it acquires a lock on the object that the method belongs to. This lock ensures that no other thread can enter any other synchronized method that belongs to the same object until the first thread has finished executing the current synchronized method.

  멀티스레드 환경에서 synchronized 키워드가 부여된 메소드에 먼저 접근한 스레드가 메소드의 주인인 <br>
  객체에대한 잠금권한을 얻어, 다른 스레드가 접근 할 수 없게한다.  <br>
  먼저 접근한 스레드가 메소드에대한 실행완료되었을때 unlock하고,  <br>
  그제서야 대기하고있던 다른 스레드가 해당 메소드에 다시접근하여 lock - 실행 - unlock을 반복한다.  <br>



### 사용법 

  - 메소드에서의 synchronized 사용 
  ``` java
  synchronized void increase() {
    count++;
  }
  ```

  - 메소드 내부에서의 synchronized 사용 
  ``` java
  void increase() {
    synchronized(this) {
      count++;
    }
  }
  ```


