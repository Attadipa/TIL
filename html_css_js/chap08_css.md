# [6일차] Do it! HTML+CSS+자바스크립트 웹 표준의 정석 / 238~288p / 08-5 웹 요소의 위치 지정하기까지

08-1 CSS와 박스모델

    블록레벨 요소 : 삽입시 혼자 한 줄 차지
    인라인 요소 : 한 줄에 다른 요소 올 수 있음
    박스모델 기본 구성 : contents, padding, border, margin
    콘텐츠 영역 크기 지정 : width(너비), height(높이)
    box-sizing : 박스 모델 크기 계산 
    box-shadow : 박스 모델 그림자 효과

​

08-2 테두리 스타일 지정하기

    적용순서 : top -> right -> bottom -> left
    border-style : 테두리 스타일 지정
    border-width : 테두리 두께 지정
    border-color : 테두리 색상
    border : 테두리 스타일 묶어서 지정
    border-radius : 둥근 테두리

​

08-3 여백을 조절하는 속성

    주의사항 : 마진중첩
    마진과 마진이 만날때 마진값이 큰 쪽으로 겹쳐짐

​

08-4 웹 문서의 레이아웃 만들기

    display : 배치방법 결정(inline, block, inline-block, none)
    float : 띄우기(left, right, none)
    clear : float속성 해제



08-5 웹 요소의 위치 지정하기

    left, right, top, bottom : 기준위치와 요소 사이에 상하좌우 얼마나 떨어져 있는지 지정
    porition : 배치방법 지정


```html
<!DOCTYPE html>
<html lang="ko">
	<head>
		<meta charset="UTF-8">
		<title>블록 레벨과 인라인 레벨</title>
    <link rel="stylesheet" href="chap08_ex.css">
		<style>
			.box1{
        width : 200px;
        height : 100px;
        padding: 20px;
        border: 10px solid black;
        margin : 5px;
        /* magin중첩현상! margin이 큰 쪽으로 겹쳐짐 */
        /* 요소의 가로배치는 상관없음 */
        display: inline-block;
      }
      .box2{
        box-sizing: border-box;
        width : 200px;
        height : 100px;
        padding: 20px;
        border: 10px solid blue;
        margin: 10px 15px 20px 30px;
        display: inline-block;
      }
      .title{
        border-style: solid;
        border-width: 5px 10px 15px 20px;
        width: 200px;
        height: 50px;
        border-left-color: brown;
        border-bottom-color: aquamarine;
        border-radius: 30px;
        display: inline;
        position: fixed;
      }
      .img1{
        border-radius: 50%;
        width: 150px;
        height: 150px;
        display: inline-block;  
        position: relative;
        right: 100px;
        top: 50px;


      }
      nav ul {
      list-style:none;  
      display:inline-block;    
 
      }
      nav ul li {
        display:inline-block;      
        padding:20px;
        margin:0 10px;
        border:1px solid #222;
        
      }
      div{
        padding: 10px;
        margin: 10px;
      }

      #box1{
        background-color: rgb(255, 231, 97);
        float: left;
      }
      #box2{
        background-color:aquamarine;
        float: right;  
      }
      #box3{
        background-color:rgb(234, 93, 41);
        clear: both;
      }
      #box4{
        background-color:rgb(85, 221, 255);

      }
      .img2{
        background-color: indianred;
        height: 150px;
        width: 400px;
        position: relative;
      }
      span{
        position: absolute;
        right: 10px;
        bottom: 10px;
        color: aliceblue;
        font-weight:200;
        font-size: 50px;
      }
		</style>
	</head>
	<body>
    <div class="box1">헬로우</div>
    <div class="box2">헬로우</div>
		<h1 class="title">시간이란...</h1>
    <img class="img1" src="photo.jpg">
    <nav>
      <ul>
       <li>menu 1</li>
       <li>menu 2</li>
       <li>menu 3</li>
       <li>menu 4</li>
      </ul>
    </nav>
    <div id="box1">menu 1</div>
    <div id="box2">menu 2</div>
    <div id="box3">menu 3</div>
    <div id="box4">menu 4</div>
    <div id="container">
			<header id="header">
				<h1>사이트 제목</h1>
      </header>
			<aside id="left-sidebar">
				<h2>사이드바</h2>				
      </aside>
			<section id="contents">
				<h2>본문</h2>
      </section>
			<aside id="right-sidebar">
				<h2>사이드바</h2>
      </aside>
			<footer id="footer">
				<h2>푸터</h2>
			<footer>
		</div>
    <div class="img2">
      <span>CSS3</span>
    </div>
    
</body>
</html>
```