# [11일차] Do it! HTML+CSS+자바스크립트 웹 표준의 정석 / 463~509p / 14-5 반복문 알아보기까지

이미 자바를 공부했기 때문에 자바와의 차이점 중심으로 서술하겠습니다

​

### 14-1 변수 알아보기

    변수 선언시 타입을 명시하지 않고 var로 통일. 할당되는 데이터에 따라 타입이 결정됨.

​

### 14-2 자료형 이해하기

    기본유형

    1. 숫자형 : 정수와 실수로 구분. 자바와는 달리 명확히 구분하지 않고 숫자형으로 묶음.

    2. 문자열 : 큰따옴표는 물론이고 작은따옴표도 사용함. 단일 문자는 따로 문자타입으로 분리되지 않음.

    3. 논리형 :  참과 거짓 표현. 자바와 동일

    복합유형

    1. 배열 : 대괄호 사용. 빈 배열 선언가능

    2. 객체

    특수유형

    undefined : 자료형이 정의되지 않았을 때의 데이터 상태

    null : 데이터 값이 유효하지 않은 상태

    ​

    데이터 유형 자동 변환 : 데이터 유형이 유연하다. 자바스크립트의 장점이자 단점

​

### 14-3 연산자 알아보기

    산술연산자 : 자바와 동일 but '/'은 정말로 나눗셈이다.(자바에서는 몫을 구하는 연산자)

    할당연산자 : 자바에서의 대입연산자

    연결연산자 : 자바와 동일

    비교연산자 : '==='. '!==' 을 사용하여 타입일치여부도 확인한다.

    논리연산자 : 자바와 동일

​

### 14-4 조건문 알아보기

    if문 if~else문 switch문 -> 자바와 동일

​

### 14-5 반복문 알아보기

    for문 while문 do~while문 break문 continue문 -> 자바와 동일

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>계산하기</title>
  <style>
    body{
      background-color: rgb(21, 27, 148);
    }
    p{
      color: rgb(255, 122, 33);
      font-size: 50px;
    }
    strong {
      font-size: 100px;
      color: gold;
    }
    .container{
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(150px,1fr));
    }
    .dan{
      width: 100px;
      border: 5px solid rgb(0, 174, 255);
      color: aliceblue;
      margin: 10px;
      padding: 20px;
    }
    h1{
      color: rgb(82, 255, 209);
      text-align: center;
    }
    span{
      font-size: 50px;
      color: gold;
      font-style: italic;
    }
  </style>

</head>
<body>
  <script>
    var currentYear = 2021;
    var birthYear;
    var age;

    birthYear = prompt("태어난 연도를 입력하세요.(yyyy)","");
    age = currentYear - birthYear +1;
    document.write(currentYear + "년 현재<br>");
    document.write(birthYear + "년에 태어난 사람의 나이는 " + age + "세입니다.");

    var userNumber = prompt("숫자를 입력하세요.");
    if(userNumber !== null) {
      if(userNumber%3===0){
        alert("3의 배수입니다")
      }
      else{
        alert("3의 배수가 아닙니다")
      }
    }
    var numberOne = prompt("숫자를 입력하세요.");
    var numberTwo = prompt("숫자를 입력하세요.");
    if(numberOne!==null && numberTwo!==null){
      if(numberOne<10 || numberTwo<10){
        alert("둘 중의 하나가 10보다 작습니다.")
      } else{
        alert("10보다 작은 숫자가 없습니다.")
      }
    }1
    var choice = prompt("좋아하는 과일을 선택해주세요 1.사과, 2.포도, 3.수박");
    switch(choice){
    case "1" : document.write("<p><strong>사과</strong>를 좋아하시네요</p>"); break;
    case "2" : document.write("<p><strong>포도</strong>를 좋아하시네요</p>"); break;
    case "3" : document.write("<p><strong>수박</strong>를 좋아하시네요</p>"); break;
    default : alert("잘못입력했습니다")
    }
    document.write("<div class='container'>")
    for(i = 2 ; i<10 ; i++){
      document.write("<div class='dan'>");
      document.write("<h1>"+i+"단"+"</h1>");
      for(j = 1 ; j<10 ; j++){
        document.write(i+" x "+j+" = "+i*j+"<br>");
      }
      document.write("</div>");
    }
    document.write("</div>");

    var sum =10;
    do{
      alert("sum is "+sum);
    } while(sum<10)

    var input = 3;
    var no = 1;
    for(i = 2 ; i<=input ; i++){
        no *= i;
    }
    document.write("<span>");
    document.write("입력값 : "+input+"<br>");
    document.write("팩토리얼 : "+ no);
    document.write("</span>");

    </script> 
</body>
</html>
```