# [12일차] Do it! HTML+CSS+자바스크립트 웹 표준의 정석 / 513~550p / 15-7 DOM을 이용한 이벤트 처리기까지

### 15-1 함수 알아보기

    자바의 클래스 내에 메서드를 만드는 것이 아니라 script문 안에 function하고 그냥 만듦.

​

### 15-2 var를 사용한 변수의 특징

    스코프 별 변수 분류 : 지역변수, 전역변수

    호이스팅 : 변수의 선언과 할당을 분리해서 선언부분을 스코프의 가장 위쪽으로 끌어올리는 것처럼 해석

    var : 호이스팅 O, 재선언 O, 재할당 O

​

### 15-3 let와 cont의 등장

    let : 호이스팅 X, 재선언 X, 재할당 O  -> 자바의 변수와 성질이 가장 유사

    const : 호이스팅 X, 재선언 X, 재할당 X  -> 자바의 변수와 성질이 가장 유사

​

### 15-4 재사용할 수 있는 함수 만들기

    매개변수 있는 함수

​

### 15-5 함수 표현식

    익명함수 : 이름없이 함수 선언 => 익명함수는 함수 자체가 식이므로 함수를 변수에 할당하여 사용가능

    즉시 실행 함수 : 함수를 정의하면서 동시에 실행

    화살표 함수 : 자바의 함수형 인터페이스와 유사한 형태. 익명함수에서만 사용가능

​

### 15-6 이벤트와 이벤트 처리기

    이벤트 :  웹브라우저 사용자가 행하는 어떤 동작

    이벤트 처리기 : 이벤트 발생시 처리하는 함수

​

### 15-7 DOM을 이용한 이벤트 처리기

    querySelector() 많이 이용.

    ()안에 클래스 이름이나 id이름 또는 다양한 선택자를 넣을 수 있음.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>함수</title>
	<style>
		body {
			padding-top:20px;
			text-align:center;
      font-size: 20px;
		}
    span{
      font-size: 30px;
      background-color: rgb(255, 175, 78);
    }
    .container{
      height: 100px;
      padding : 10px;
      display: grid;
      grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
    }
    .button{
      margin: 20px;
      border: 1px solid black;
      height: 80px;
    }
    .screen{
      margin-left: 100px;
      margin-right: 100px;
      margin-top: 20px;
      height: 200px;
      border: 10px solid rgb(111, 221, 255);
      border-radius: 20%;
      background-color: aliceblue;
    }
    button{
      height: 80px;
      margin: 20px;
      font-size: 20px;
      background-color: rgb(255, 220, 79);
      border: 10px solid rgb(255, 177, 51);
      border-radius: 30%;
    }

    .button2{
      background-color: rgb(255, 136, 0);
      border: 10px solid rgb(255, 177, 51);
      color: aliceblue;
    }
	</style>
</head>
<body>
	<script>

    addNumber();
    
    function addNumber(){
      var num1 = 2;
      var	num2 = 3;
      var sum = num1 + num2;
      console.log(sum);
      console.log(num3);
      var num3 = 4;
    }


    (function(num1, num2){
      sum = num1 + num2
    }(10,20))
    document.write("실행결과 : "+sum+"</br>");

    // (function (){
    //   var userName = prompt("이름을 입력하세요")
    //   document.write("안녕하세요? <span>"+ userName + "</span>님!</br>")
    // }());

    // const hi = function() {
    //   alert("안녕하세요?");
    // }
    // const hi = () => alert("안녕하세요?");
    let hi = (user) => document.write(user+"님, 안녕하세요?</br>");
    hi("아이유");

    let sumsum = (a,b) =>  a + b;
    sumsum(3,4);
    document.write("두 수의 합 : "+ sumsum(10,20));

      function changeBg(color){
        var result = document.querySelector('.screen');
        result.style.backgroundColor = color;
      }
      function changeFc(color){
        var result = document.querySelector('.screen');
        result.style.color = color;
      }
      function darkMode(color){
        var result = document.querySelector('body');
        result.style.backgroundColor = color;
      }
      
      document.querySelector('.button2').onclick = changeFcOnclick;

      function changeFcOnclick(){
        document.querySelector('.screen').style.color = 'blue';
      }
	</script>	
  <div class="container">
    <div class="button" onclick="changeBg('red')">사과</div>
    <div class="button" onclick="changeBg('purple')">포도</div>
    <button class="button2">글자색</br>바꾸기</button>
    <button onclick="changeFc('white')">글자색</br>바꾸기</button>
    <button onclick="darkMode('black')">다크</br>모드</button>
  </div>
  <div class="screen">The White House is the official residence and workplace of the president of the United States. It is located at 1600 Pennsylvania Avenue NW in Washington, D.C., and has been the residence of every U.S. president since John Adams in 1800. The term "White House" is often used as a metonym for the president and his advisers.</div>

</body>
</html>
```