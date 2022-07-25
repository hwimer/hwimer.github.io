---
title: "DispatcherSevlet이란?"
categories: 
  - spring 
toc: true
toc_sticky: true
toc_label: Content 
---

### 1. Dispatcher Servlet이란??
- FrontController + RequestDispatcher 이다.
> DispatcherServlet이 자동생성되어 질 때 수 많은 객체가 Ioc된다.<br>
> 보통 필터들이며, 해당 필터들은 내가 직접 등록할 수 도 있고(on servlet-context.xml),<br>
> 기본적으로 필요한 필터들은 자동으로 등록되어진다. <br>
 

### 2. FrontController 패턴이란?
- 디자인패턴중 한 종류이다.
- 필터이다. 
> 맨 앞단에서 모든요청을 낚아채 필요한 클래스에 요청하는 역할을 가지고있다.

### 3. requestDispatcher란?
> 사용자의 요청을 필요한 클래스까지 가는동안 request와 response를 그대로 유지시켜주는 기법이다.<br><br>
사용자가 웹서버에 특정한 자원을 요청A를 request한다.<br>
위에서 설명했던 frontController는 해당요청을 낚아채 요청에 해당되는 자원을 가져오기위해 새로운 요청B를 생성하게된다.<br>
분명 A와 B가 같은 요청임에도 B요청이 재생성되므로서 A에대한 정보가 유실된다.<br>
스프링에서는 A를 그대로 보존하여 자원을 요청하는 기법이 필요하였고,<br>
이를 <b>"requestDispatcher"</b>라 한다.<br>

#### 3-1. 언제사용할까??
> 보통은 사용자가 브라우저에서 페이지를 전환할 때 모든요청에대해 서버는 각각의 요청으로 인지하는데,<br>
requestDispatcher를 기법을 사용하면 사용자가 a라는 페이지에서 b페이지를 이동할 때 <br>
nav바에 담겨있는 사용자의 정보를 그대로 가지고 이동할 수 있다.

 
