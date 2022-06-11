---
title: SES Bounce 
categories: 
  - aws 
toc: true
toc_sticky: true
toc_label: Content 
---

## 평판
> SES에는 “평판” 이라는 개념이존재,<br>
평판은 반송율과 수신거부율로 정해지는데 권장사항으로는 반송율은 5% 미만,<br>
수신거부율은 0.1% 미만이여야 함.

## SNS (Simple Notification Service)
> 위에서 이야기한 “평판”을 관리하기위해 알람서비스를 이용함.<br>
이메일 반송 혹은 수신거부 되었을때, 모니터링 하기위해 사용한다.

## SES 설정
> 이메일전송이 반송되었을때 모니터링 하기위함.

1. Create SNS Topic (Amazon SES > Verified identities > Notification(Tab) > Edit Feedback notifications )
2. Set Bounce feedback

![base64Eg](/assets/postImg/generateTopic.png){: width="75%" height="75%"}

## SNS 설정
> 상단에서 생성한 Topic에 대한 구독자를 설정한다.

1. Create subscription (Amazon SNS > Subscriptions)
2. Set Topic ARN 
3. Set Protocol to Email And Set Email

![base64Eg](/assets/postImg/subcription.png){: width="75%" height="75%"}



## Reference
- [AWS SES Bounce 처리](https://isntyet.tistory.com/140)
- [AWS - SES 사용 후기](https://heowc.dev/2020/04/11/aws-ses-review/)
