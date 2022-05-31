# [10일차] Do it! HTML+CSS+자바스크립트 웹 표준의 정석 / 389~438p / 12-5 CSS 그리드 레이아웃 사용하기까지

### 12-1 반응형 웹 알아보기

  다양한 화면 크기에 맞게 웹 디자인이 재배치되고 표시방법이 바뀌는 웹 디자인 방법

  뷰포트 : 화면에서 실제 내용이 표시되는 영역

  뷰포트 단위 : vw, vh, vmin, vmax

​

### 12-2 미디어 쿼리 알아보기

  @media : (미디어쿼리) 사이트에 접속하는 장치에 따라 특정한 css스타일을 사용하는 방법

​

### 12-3 그리드 레이아웃 알아보기

  웹사이트를 여러 개의 칼럼으로 나눈 후 메뉴나 본문, 이미지 등의 웹 요소를 화면에 맞게 배치하는 것

  방법

  1. 플렉서블 박스 레이아웃

  2. CSS 그리드 레이아웃

​

### 12-4 플렉스 박스 레이아웃

  display : 플렉스 컨테이너 지정

  flex-direction : 플렉스 방향 지정

  flex-wrap :  플렉스 항목의 줄 바꿈

  flex-flow : 배치방향과 줄 바꿈을 한꺼번에 지정

  justify-content : 주축 정렬 방법 지정

  align-items : 교차축 정렬 방법 지정

  align-self : 특정 항목만 정렬 방법 지정

  align-content : 여러 줄일 때 교차축 정렬 방법 지정

​

### 12-5 CSS 그리드 레이아웃 사용하기

  display  : 그리드 컨테이너 지정

  grid-template-columns : 칼럼 지정

  grid-template-rows : 줄 지정

  fr : 상대적인 크기 지정

  repeat() : 값이 반복될 때 줄여서 표현

  minmax() : 최솟값과 최댓값 지정

  auto-fit : 자동으로 칼럼 개수 조절, 남는 공간 꽉 채움

  auto-fill : 자동으로 칼럼 개수 조절, 남는 공간 안 채움

  grid-column-gap : 칼럼과 칼럼 사이 간격 지정

  grid-row-gap : 줄과 줄 사이 간격 지정

  grid-gap : 칼럼과 줄 사이의 간격을 한꺼번에 지정


  ```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>미디어쿼리 사용하기</title>
  <style>
    body{
      background:url(bg0.jpg) no-repeat fixed;
      background-size : cover;
    }
    @media screen and (max-width:1024px){
      body{
      background:url(bg1.jpg) no-repeat fixed;
      background-size : cover;
      }
    }
    @media screen and (max-width:768px){
      body{
      background:url(bg2.jpg) no-repeat fixed;
      background-size : cover;
      }
    }
    @media screen and (max-width:320px){
      body{
      background:url(bg3.jpg) no-repeat fixed;
      background-size : cover;
      }
    }
    .container {
      display:flex;  /* 플렉스 컨테이너 지정 */
      height: 230px;
      background-color:#eee;
      border:1px solid #222;
      margin-bottom:30px;
      flex-flow : row wrap;
      align-content: center;
    }
    .boxx {
      padding:5px 5px;
      margin:5px;
	  	width:70px;
      background-color:#222;   
    }               
    p {
      color:#fff;
      text-align: center;
    }
    #wrapper{
      display:grid;
      grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
      grid-template-rows: minmax(50px, auto);

      }
    .items{
      padding:10px;
      background-color:rgb(238, 238, 238);
    }   
    .items:nth-child(odd){
      background-color:rgb(187, 187, 187);
    }
    #wrapper2{
        width:700px;
        display:grid;
        grid-template-columns:repeat(3, 1fr);
        grid-template-rows:repeat(3, 100px);
      }
      .box{
        padding:15px;
        color:#fff;
        font-weight:bold;
        text-align:center;
      }   
      .box1 {
        background-color:#3689ff;
        grid-column:1/4;
      }
      .box2 {
        background-color:#00cf12;
        grid-row:2/4;
        /* grid-column:1/2; */
        grid-column-start:1;
      }
      .box3 {
        background-color:#ff9019;
        grid-column:2/4;
        /* grid-row:2/3; */
        grid-row-start:2;
        }
      .box4 {
        background-color:#ffd000;
        grid-column-start:3;
        grid-row-start:3;
      }
  </style>
</head>
<body>
  <div id="wrapper">
    <div class="items">Lorem ipsum dolor sit amet consectetur adipisicing elit. Amet, reprehenderit.Lorem ipsum dolor, sit amet consectetur adipisicing elit. </div>
    <div class="items">Lorem ipsum dolor, sit amet consectetur adipisicing elit.Lorem ipsum dolor, sit amet consectetur adipisicing elit</div>
    <div class="items">Lorem ipsum dolor sit amet.Lorem ipsum dolor, sit amet consectetur adipisicing elit</div>
    <div class="items">Lorem ipsum dolor sit.Lorem ipsum dolor, sit amet consectetur adipisicing elit</div>
    <div class="items">Lorem, ipsum dolor.</div>
  </div> 
  <div class="container" id="opt1">
    <div class="boxx" style="height: 100px"><p>1</p></div>
    <div class="boxx" style="height: 200px"><p>2</p></div>
    <div class="boxx" style="height: 170px"><p>3</p></div>
    <div class="boxx" style="height: 70px"><p>4</p></div>  
  </div>
  <div id="wrapper">
    <div class="box box1">box1</div>
    <div class="box box2">box2</div>
    <div class="box box3">box3</div>
    <div class="box box4">box4</div>
  </div>
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