---
title: \[TroubleShooting-RDS\] Uncaught SyntaxError: Unexpected token '<'
---
##   
> 사내업무에서 콘솔 파일 다운로드 기능을 구현하던중 화면단에서 <br>
"Uncaught SyntaxError: Unexpected token '<' " 오류가 발생.<br>
아래 추가로 "‘uncaught referenceerror $ is not defind" 라는 오류가 떨어졌기에 당연히... 당연히..  import 한 Jquery를 인식하지 못하는중....이겠거니,,  판단하여 화면단에서 path가 올바른지를 확인하는데에 많은 시간을 소비했으나... 문제를 찾지못하여 개발중인 feature브랜치와 develop브랜치를 하나하나 비교하던중
REST Controller에서 이상한점을 발견. 빠른 개발을위해 Copy& Paste를 연발했고,
@RequestMapping과 @GetMapping을 하나의 RESTful에서 동시에 작성된곳을 발견함.
에이..설마.. 아닐꺼야.. 라는 생각과 함께 중복을 제거하고 refresh 했고,
놀랍게도 해당 코드에서 화면오류가 발생하는것을 확인...(재연가능)

## 해결 : 
```java
// @RequestMapping(method = RequestMethod.GET)
@GetMapping("blabla")
```