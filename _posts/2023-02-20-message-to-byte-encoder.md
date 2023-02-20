
### MessageToByteEncoder 란??

MessageToByteEncoder == Netty framework for Java
비동기이벤트기반 네트워크 애플리케이션 프레임웤 



### 용도

메세지를 bytes로 인코딩해준다 (outbound messages >> byte buffers) 
그리고 변환된 메세지는 네트워크를 통해 전송할 수 있다. 


### 사용법 

1. 클래스 상속 

2. encode() method 재정의 <br>

예제코드<br>
``` java 
public class MyEncoder extends MessageToByteEncoder<MyMessage> {

    @Override 
    protected void encode(ChannelHandlerContext ctx, MyMessage msg, ByteBuf out) {

        byte[] bytes = convertMessageToBytes(msg);
        out.writeBytes(bytes);
    }

    private byte[] convertMessageToBytes(MyMessage msg){
        // Convert the message to byte array 
    }

}
```

### 작동방식 

위에서 생성한 클래스를 (MessageToByteEncoder를 상속받은 클래스) 생성자를통해 호출시<br>
재정의한 encode() 메소드가 자동적으로 실행된다. 


