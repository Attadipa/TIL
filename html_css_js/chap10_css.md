# [8일차] Do it! HTML+CSS+자바스크립트 웹 표준의 정석 / 219~352p / 10-3 가상 클래스와 가상 요소까지

10-1 연결 선택자

a    b  하위 선택자 : 부모 요소에 포함된 모든 하위요소 선택(자식요소, 손자요소 등)

a > b  자식 선택자 : 부모 요소의 자식요소만 선택

a ~ b  형제 선택자 : 모든 형제 요소 선택

a + b  인접 형제 선택자 : 인접한 형제 요소만 선택

​

10-2 속성 선택자

a[속성]  [속성]선택자 : 속성이 있는 요소 선택

a[속성=속성값]  [속성=속성값]선택자 : 속성이 특정 속성값을 갖는 요소 선택

a[속성~=속성값]  [속성~=속성값]선택자 : 여러 속성값중에서 해당 속성값이 포함된 요소 선택

a[속성|=속성값]  [속성|=속성값]선택자 : 여러 속성값중에서 해당 속성값 또는 하이픈(-)로 연결된 단어를 속성값으로 갖는 요소 선택

a[속성^=속성값]  [속성^=속성값]선택자 : 지정된 속성값으로 시작하는 요소 선택

a[속성$=속성값]  [속성$=속성값]선택자 : 지정된 속성값으로 끝나는 요소 선택

a[속성*=속성값]  [속성*=속성값]선택자 : 속성값이 어느 위치에 있든지 지정한 속성값이 포함되어 있는 요소 선택

​

10-3 가상 클래스와 가상 요소

: 가상 클래스 : 사용자 동작에 반응(주의 : 아래 순서대로 적용할 것)

  link : 방문하지 않은 링크

  visited : 방문한 링크

  hover :  마우스 포인터 올려놓으면 스타일 적용

  active : 웹 요소 활성화시 적용

  focus : 웹 요소에 초점이 맞추어졌을 때 적용

:: 가상 요소 : 불필요한 태그 사용하지 않으면서 요소 추가

  before 내용 뒤에 컨텐츠 추가

  after 내용 앞에 컨텐츠 추가

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>고급 선택자</title>
  <style>
    body {
      background-color:#eee;
    }
    #container {
      width:600px;
      margin:20px auto;
    }
    p {
      width:500px;
      padding:10px;
    }

    #container > p{
      background-color: #fff;
      border:1px solid black;
    }

    #container > div > p {
      background-color: #222;
      color: #fff;
      font-weight:bold;
    }

    h2 ~ p{
      border-radius: 30%;
    }

    h2 + p{
      height: 50px;
      font-size: 30px;
      text-align: center;
    }
    ul {
      list-style:none;
    }
    li {
      width:120px;	
      font-size: 20px;
      display:inline-block;
      margin:10px;
    }
    li a[href] {
      padding: 5px 20px;
			font-size: 14px;
			text-decoration: none;
			font-weight: bold;
    }
    li a[href="#"] {
      background:yellow;
		  border:1px solid #ccc;
		  font-weight:normal;
      cursor:default;
    } 
    ul a:link{
      background-color: rgb(0, 255, 51);
    }
     a:visited{
      background-color: rgb(30, 0, 255);
    }
    #container div p:hover{
      background-color: red;
    }
    ul a:focus{
      background-color: rgb(147, 147, 71);
    }
    ul a:active{
      background-color: rgb(175, 2, 255);
    }
    p#new::after{
      content: "NEW!!";
      font-size: large;
      padding: 2px 4px;
      margin: 0 10px;
      border-radius: 2px;
      background-color: red;
      color: white;
    }

    
  </style>
</head>
<body>
  <div id="container">
    <p>일반적인 텍스트 단락입니다.</p>
    <h1>예약 방법 & 사용 요금</h1>
    <p>아직 온라인 예약 신청이 준비되어 있지 않습니다. <br>전화(xxx-xxxx-xxxx)로 문의 바랍니다.</p>
    <div>
      <h2>온양온천</h2>
      <p>가족실(2~4인) : 60,000원/일</p>
      <p>도미토리(4인 공용) : 25,000원/일</p> 
      <p>VIP실(1인) : 120,000원/일</p>
      <p id="new">VVIP실(2인) : 200,000원/일</p>
    </div>
  </div>
  <ul>
		<li><a>메인 메뉴 : </a></li>
		<li><a href="#">메뉴 1</a></li>
		<li><a href="b.html">메뉴 2</a></li>
		<li><a href="c.html">메뉴 3</a></li>
		<li><a href="d.html">메뉴 4</a></li>
	</ul> 
</body>
</html>
```