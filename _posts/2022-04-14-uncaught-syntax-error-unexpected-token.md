---
title: Uncaught SyntaxError Unexpected token
categories: 
    - troubleShooting
---
### 문제발생: 
> 백오피스 파일 다운로드 기능을 구현하던 중 Uncaught SyntaxError: Unexpected token '<' 오류가 발생.
> 아래 추가로 uncaught reference $ is not defind" 라는 오류가 떨어졌기에,
> 당연히 .. import한 제이쿼리를 인식하지 못하는중이겠거니 판단하여 화면단에서 path가 올바른지를 확인하는데에 많은 시간을 소비했음... 
> 그러나... 문제를 찾지못하여 개발중인 feature브랜치와 develop브랜치를 하나하나 비교하던중
> RestController에서 이상한점을 발견하였음. 

### 문제가 되었던 부분...
```java
@RequestMapping(method = RequestMethod.GET)
@GetMapping("blabla")
```

> 빠른 개발을위해 Copy& Paste를 연발했고, 
> @RequestMapping과 @GetMapping을 하나의 RESTful에서 중복되게 작성된곳을 발견.. 
> 아니겠지.. 라는 생각과 함께 중복을 제거하고 refresh 했고, 
> 놀랍게도 해당 코드에서 오류가 발생하는것을 확인하였음.. (재연가능)

### 해결 : 
```java
@GetMapping("blabla")
```
