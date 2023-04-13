---
title: MultiThread
categories: 
    - CS 
---

### MultiThread 란??

> multithreading is a technique by which a single program can run multiple tasks concurrently (at the same time) within a single process

MultiThread == 하나의 프로세스에서 둘 이상의 스레드가 "동시에" 수행하는 것을 의미. <br>
일반적으로는 하나의 프로세스를 하나의 스레드가 수행하지만, <br>
하나의 프로세스를 여러스레드가 동시에 수행하는것을 멀티스레드라고 한다.<br>

### 특징
1. 리소스 및 메모리공유 <br><br>
프로세스가 실행될 때 메모리를 할당되어 실행되는데 <br>
이 때 할당된 메모리를 여러쓰레드가 공유해서 작업한다. <br>
당연히 여러쓰레드가 동일한 메모리를 참조하기때문에 낭비가 적습니다. <br>


### 용도
동일한 기능을 수행하는 프로세스를 여러스레드를 생성해서 작업들을 분배해주면 <br>
하나의 스레드에서 작업하는것보다 속도가 빠르다(대기시간을 줄일 수 있다)<br>
예를들어 계좌를 개설하는 행원이 한명이고, 계좌를 개설하기위해 대기하고있는 고객이 50명이라고했을때<br>
행원을 10명으로 늘리면 행원당 계좌개설을 5명만 하면된다. 그 만큼 고객이 줄어든다는 장점을 가지고있다. <br>
