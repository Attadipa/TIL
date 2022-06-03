# [13일차] Do it! HTML+CSS+자바스크립트 웹 표준의 정석 / 554~598p / 16-3 브라우저와 관련된 객체까지

​

### 16-1 객체 알아보기

    객체란? 프로그램에서 인식할 수 있는 모든 대상

    종류? 문서 객체 모델(DOM), 브라우저 관련 객체, 내장 객체

    객체 자체가 아니라 인스턴스 형태로 만들어서 사용해야 한다.

    자바와의 차이점은 자바스크립트에서의 객체개념은 자바에서의 클래스개념과 대응된다는 점이다.

​

### 16-2 자바스크립트의 내장 객체

    Array객체 : 배열을 다루며, new예약어를 사용하여 변수에 할당할 수도 있고 대괄호를 사용하여 표현할 수도 있다.

    Date객체 : 날짜와 시간 정보를 다룸. 따로 인스턴스를 만들어 사용

    Math객체 : 수학계산과 관련된. Array객체나 Date객체와 달리 따로 인스턴스를 만들지 않습니다. 자바에서의 static 변수와 static 메서드 사용하는 경우와 유사

​

### 16-3 브라우저와 관련된 객체 

    window 객체 : 브라우저 창이 열릴 때마다 하나씩 만들어짐. 자바스크립트의 모든 객체는 window객체에 포함.

    자바에서의 object 클래스에 해당.

    document 객체 : 웹문서마다 하나씩 있음. HTML문서의 정보가 담겨있음.

    navigator 객체 : 현재 사용하는 브라우저의 정보가 들어있습니다

    history 객체 : 현재 창에서 사용자의 방문 기록을 저장.

    location 객체 : 현재 페이지의 URL정보가 담겨 있음.

    screen 객체 : 현재 사용하는 화면 정보를 다룸.




```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>독서 챌린지</title>
  <style>
    #container{
      margin:50px auto;
      width:300px;
      height:300px;
      border-radius:50%;
      border:2px double #222;
      background-color:#d8f0fc;
      text-align: center;
    }
    h1 {
      margin-top:80px;
    }
    .accent {
      font-size:1.8em;
      font-weight:bold;
      color:red;
    }
  </style>
</head>
<body>
  <div id="container">
    <h1>책 읽기</h1>
    <p><span class="accent" id="result"></span>일 연속으로 <br> 책 읽기를 달성했군요.</p>
    <p>축하합니다!</p>
  </div>  

  <script>
    var now = new Date();
    var firstDay = new Date("2022-01-01");
    
    var toNow = now.getTime();
    var toFirst = firstDay.getTime();
    var passedTime = toNow - toFirst;
    passedTime = Math.round(passedTime/(24*60*60*1000));

    document.querySelector('#result').innerText = passedTime;

  
    function openCenter(doc, win, width, height){
      var left = (screen.availWidth-width)/2;
      var top = (screen.availHeight-height)/2;
      var opt = "left="+left+", top = "+top+", width = "+width+" ,height = "+height;
      window.open(doc, win, opt);
    }

    openCenter("notice.html","notice",500,300);
  </script>
</body>
</html>
```