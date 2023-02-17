---
title: HTTP, HTTPS 차이 
categories:
    - network 
---


### HTTPS란 ?

  HTTP(Hypertext Transfer Protocol) + S(Secure) 
  데이터를 주고받기위한 프로토콜 + 암호화 

  > http, https are both used for communication between a client (such a web browser) and server 
  

### 배경 

      
  > the main difference between them is in how they secure the data that is trasmitted over the internet <br>
  HTTP is an unencrypted protocol(암호화X), which means that the data being trasmitted between the client <br>
  and server is not secured and can potentially be intecepted by third parties(누군가로부터 후킹당할 수 있음)<br>
  This means that if someone intercepts the comunication, ...

  HTTP는 암호화가되지않은 데이터를 주고받는 프로토콜이다. 
  그런데 이 통신과정에서 주고받는데이터가 누구로부터 Intercept당할 수 있다. 
  개인정보를 도둑맞을 수 있단얘기 >> 보안성 매우취약 


  
  > On the other hand, HTTPS is a secure protocol that uses encryption to protect the data (암호화를사용 데이터를 보호하기위함)<br>
  being transmitted HTTPS uses an SSL/TLS (Secure Sockets Layer/Transprot Layer Security) protocol to encrypt the <br>
  client and server. This encryption ensures that any data transmitted over the internet is secure and can only be accessed by the <br>
  intended recipient

  HTTPS는 암호화된 데이터를 주고받는 프로토콜이다. 
  클라이언트와 서버간의 통신을 암호화한다. (SSL/TLS 프로토콜을이용해서 ...)
  이 암호화된 데이터는 안전하고 의도된 수신자만 access할 수 있도록 보장한다. 


### 동작원리 

    > Once the secure connection is established,(보안연결이 설정되면,) the web browser and server can then <br>
    use the HTTPS protocol to securely exchange data, such as requests and responses for web pages, images, and other resources 

    This secure communication ensures that any data transmitted over the internet is protected from intecption and 
    cannot be read or modified by third parties. This is especially important for websites that transmit sensitive inforamtion, 
    such as login, credential, credit card, and other information blah... 

    In summary, HTTPS works by establishing a secure, encrypted connection between the client and server 
    using SSL/TLS, which then allows for secure communication using the HTTP protocol. This ensures that any data 


  보안이 연결되면, HTTPS 프로토콜을 사용해 은밀히 데이터를 변경한다. (요청, 응답에대한 모든 데이터를(웹 페이지, 이미지 ...)
  보안을 보장합니다 인터넷을통해 주고받는 모든데이터들에 대해서

  제3자가 읽을수도, 수정할수도없습니다. 해당 프로토콜은 결과적으로 매우중요합니다. 
  in 개인정보를 전송하는 웹사이트에서


#### 요약 


  1. 클라이언트가 서버로 요청 
  해당행위로 서버와 보안세션을 시작함. 

  2. 서버는 메세지를 응답
  응답메세지에는 보안세션에 사용될 프로토콜과 암호, 
  서버의 공개키가들어있는 SSL/TLS인증서를 동봉되어있다. 

  3. 서버에응답에대한 검증절차 
  서버로부터 응답받은 클라이언트의 브라우저는 
  동봉된 인증서가 유효하고 신뢰할 수 있는 CA(인증)기관에서 발급되었는지를 확인한다. 
  인증서가 유효할 경우, 브라우저는 대칭세션 키를 생성하고 서버의 공용키를 사용해 데이터를 암호화한다. 

  4. 서버의 decript 테스트
  위 절차에서 클라이언트의 브라우저는 세션키를 암호화해서 서버로 전송하고, 
  암호화된 세션키를 받은 서버는 해당 메세지를 수신하여 
  자신(서버)의 개인키를 이용해 복호화해본다. 
  
  5. 완료 
  클라이언트와 웹서버모두 서로 대칭 세션키를 사용하기때문에 
  이 둘 사이에 전송된 모든 데이터를 암호화하고 전송, 받는주체는 수신하고 복호화해서 사용합니다. 
  제 3자가 가로챌 수 없습니다. 



  











