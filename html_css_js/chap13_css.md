# [10일차] Do it! HTML+CSS+자바스크립트 웹 표준의 정석 / 441~461p / 13-4 자바스크립트 스타일 가이드까지

### 13-1 자바스크립트로 무엇을 할까

    웹 요소 제어, 웹 애플리케이션 제작, 다양한 라이브러리 사용가능, 서버  

​

### 13-2 웹 브라우저가 자바스크립트를 만났을 때

    1. 웹 문서 안에<script>태그로 작성

    2. 외부 스트립트 파일로 연결

​

### 13-3 자바스크립트 용어와 기본 입출력 방법

    식과 문 : 식은 표현식, 문은 명령

    입출력 방법

    alert(메세지) : 알림창 출력

    confirm(메세지) : 확인창 출력

    propmt(메세지(,기본값)) : 프로프트 창에서 입력

    document.write()문 : 웹문서(document)에서 괄호 안의 내용을 표시(write)

​

13-4 자바스크립트 스타일 가이드

    1. 코드를 보기 좋게 들여쓰기

    2. 세미콜론으로 문장 구분(없어도 가능은 하지만 세미콜론 붙이는 걸 권장)

    3. 공백을 넣어 읽기 쉽게 작성

    4. 소스 코드를 잘 설명하는 주석을 작성

    5. 식별자는 정해진 규칙을 지켜 작성


```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <script>
    alert("안녕하세요");
    confirm("Hello world");
    var text = prompt("입력하세요","기본값");
    var season = ["봄","여름","가을","겨울"];
    document.write(text);
    document.write(season);
    document.write(season[0]);
    console.log(text + "님을 환영합니다");
  </script> 
</body>
</html>
```