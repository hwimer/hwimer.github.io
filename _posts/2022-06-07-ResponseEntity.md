---
title: ResponseEntity란? 
categories: 
  - spring 
toc: true
toc_sticky: true
toc_label: Content 
---
## ResponseEntity란??
> 서버가 사용자에게 데이터를 제공해줌에 있어서 예외처리를 할 수(?) 있는 방법이다. 
> e.g) 사용자가 게시판을 접속했으나, 해당게시판에는 게시물이 존재하지 않을 수 있다. 
> ResponseEntity는 개발자가 직접 결과 데이터와 HTTP 상태코드를 직접 제어할 수 있는 클래스로, 
> 개발자는 404나 500 ERROR와 같은 HTTP 상태 코드를 전송하고 싶은 데이터들과 함께 전송할 수 있기 때문에 좀더 
> 세밀한 제어가 필요한 경우에 사용합니다. 


## ResponseEntity란?? 
> 응답데이터를 담는 그릇이다.<b>(그런데 이제 부가설명을 좀 곁들인...)</b><br>
Spring에서는 클라이언트가 API를 호출했을 때 데이터만 띡 응답하는것이 아닌, <br>
상태값과 같이 데이터를 담아 응답할 수 있는 그릇(ResponseEntity(객체))을 제공해준다.<br>
아래 예제를 통해 다시 접근해보자.<br>
클라이언트에서 다음과 같은 요청을 통해 사용자가 수신한 메세지 목록을 아래와같이 요청하고,

```java
    @GetMapping("/messages/{userId}")
    public ResponseEntity<List<Message>>getMessages(@PathVariable("userId") long userId){
        MessageExample example=new MessageExample();
        example.createCriteria()
        .andUserIdEqualTo(userId);
        List<Message> messageList=messageMapper.selectByExample(example);

        if(messageList.size()==0){
        return ResponseEntity.noContent().build();
        }
        return new ResponseEntity<>(messageList,HttpStatus.OK);
    }

``` 
> 사용자가 수신한 메세지목록이 존재하는경우,

> 혹은 해당 메세지가 단1건도 존재하지 않을경우, 
> 사용자가 수신한 메세지목록이 존재하지 않을 수도있다.<br>
해당 메세지가 단1건도 존재하지 않을경우,  

## Sample Code


## Best Practice


## 주의사항 
- Constructor 보다 Builder 