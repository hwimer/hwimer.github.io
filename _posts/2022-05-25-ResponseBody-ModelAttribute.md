---
title: ReseponseBody VS ModelAttribute 
categories: 
  - spring 
toc: true
toc_sticky: true
toc_label: Content 
---

> 클라이언트로부터 전송받은 데이터를 컨트롤러에서 객체에 바인딩(변환?)시<br>
> @RequestBody와 @ModelAttribute를 사용하는데<br> 
> 이 둘의 미묘(?)한 차이를 정리하기위해 포스팅.  


### 결론 
> <b>@RequestBody :</b><br>  
> > JSON data를 자바객체로 "변환" 시에 사용. 
>
> <b>@ModelAttribute : </b><br>
> > form data를 자바객체로 "바인딩"(할당) 시 사용.

### MessageConverter
> 스프링은 여러형태의 MessageConverter를 소유하고있다.<br>
> > FormHttpMessageConverter<br>
> > MappingJacksonHttpMessageConverter

### 차이 
> <b>@RequestBody</b>
> > Setter 필요없음 <br>
> > @RequestBody에 사용되는 MessageConverter(MappingJacksonHttpMessageConverter)의 매커니즘은<br>
> > 객체에 바인딩하지 않고 <b>변환</b> 하기때문이다.<br>
> > 미디어타입 : application/json
> 
> <b>@ModelAttribute</b>
> > Setter 필요 <br>
> > @ModelAttribute에 사용되는 MessageConverter(FormHttpMessageConverter)의 매커니즘은<br>
> > 객체에 직접적으로 <b>바인딩</b>하기 때문이다.<br>
> > 미디어타입 : application/x-www-form-urlencoded


### 느낀점
> 경우에따라 form data를 받을땐 @ModelAttribute를,<br>
JSON data를 받을땐 @RequestBody를 사용하면될것같다.


[//]: # (> 스프링은 여러가지의 MessageConverter를 소유하고있으며, )

[//]: # (> FormHttpMessageConverter)

[//]: # (> MappingJacksonHttpMessageConverter)

