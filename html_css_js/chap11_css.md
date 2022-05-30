# [9일차] Do it! HTML+CSS+자바스크립트 웹 표준의 정석 / 356~384p / 11-3 애니메이션 알아보기


11-1 변형 알아보기

    transform : 물체의 크기나 형태의 위치를 바꾸는 것

    translate() : 웹요소 이동

    scale() : 요소 확대 축소

    rotate() : 요소 회전

    skew() : 요소를 비틀어 왜곡

​

11-2 트랜지션 알아보기

    transition : 웹 요소의 배경색을 바꾸거나 모양을 바꾸는 것처럼 스타일 속성이 시간에 따라 바뀌는 것

    transition-property : 트랜지션의 대상 지정

    transition-duration : 트랜지션의 진행 시간 지정

    transtion-timing-function : 트랜지션 효과의 시작, 중간, 끝에서 속도를 지정가능

    transtion-delay : 트랜지션의 지연 시간 설정

​

11-3 애니메이션 알아보기

    @keyframes : 애니메이션에서 상태 바뀌는 지점 설정

    animation-name : 애니메이션 이름 지정

    animation-duration : 애니메이션 실행 시간 지정

    animation-direction : 애니메이션 방향 지정

    animation-iteration-count : 반복횟수 지정

    animation : 애니메이션 속성 한꺼번에 표기


```html
<!DOCTYPE html>
<html lang="ko">
	<head>
		<meta charset="UTF-8">
		<title>Transform:translate</title>
    <style>
			#container {
				width:800px;
				height:100px;
				margin:20px auto;
			}
			.origin {
				width: 100px;
				height: 100px;
				border: 1px solid black;
				float: left;
				margin: 10px;
        perspective: 200px;

			}
      div > img{

        transition: all 1s;
      }
			.origin > div {				
				width:100px;
				height:100px;
				background-color:orange;
        transition: all 1s;
			}
      #movex:hover {
        transform: translateX(50px);  /* x축으로(가로) 50px 이동 */
      }
      #movey:hover {
        transform: translateY(20px);  /* y축으로(세로) 20px 이동 */
      }
      #movexy:hover {
        transform: translate(10px, 20px);  /* x축으로(가로) 10px, y축으로(세로) 20px 이동 */
      }
      #scalex:hover{
        transform: scaleX(2);  /* x축으로(가로) 2배 확대 */ 
      }
      #scaley:hover{
        transform: scaleY(1.5);  /* y축으로(세로) 1.5배 확대 */ 
      } 
      #scale:hover{
        transform: scale(0.7);  /* x, y축으로(가로, 세로) 0.7배 확대 */ 
      }
      #rotatex:hover{
        transform: rotateX(55deg);
        
      }
      #rotatey:hover{
        transform: rotateY(55deg);
      }
      #rotatez:hover{
        transform: rotateZ(55deg);
      }
      #rotatexyz:hover{
        transform: rotate3d(1, -1, 1, 55deg);
      }
      #skewx:hover {
        transform: skewX(30deg);  /* x축 기준으로 30도 비틀기 */
      }
      #skewy:hover {
        transform: skewY(15deg);  /* y축 기준으로 15도 비틀기 */
      }
      #skewxy:hover {
        transform: skew(-25deg, -15deg);  /* x축 기준으로 -25도, y축 기준으로 -15도 비틀기 */
      }
      .box {
      width: 100px;
      height: 110px;
      background-color: #07f;
      border: 1px solid #222;
      transition-property: width, height;
      transition-duration: 1s, 1s;
      transition-timing-function: ease-in;
      float: left;
    }
    .box:hover {
      width:200px;
      height:120px;		
    }
    #ex div{
      float:left;
      width:50px;
      height:100px;
      margin:5px 5px;
      padding:5px;
      color:white;
      background-color:#006aff;
      border-radius:5px;
      text-align:center;
      font-weight:bold;	
    }
    #ex:hover div{
      height:400px;
    }
    #ex .ease {
      transition: 3s ease;
    }
    #ex .linear{
      transition:3s linear;
    }
    #ex .ease-in{
      transition:3s ease-in;
    }
    #ex .ease-out{
      transition:3s ease-out;
    }
    #ex .ease-in-out{
      transition:3s ease-in-out;
    }
    .rbox{
      border-radius:30%;
      margin: 10px;
      float: left;
      width: 100px;
      height: 100px;
      background-color: rgb(125, 125, 175);
      transition: 1s ease-in-out;
    }
    .rbox:hover{
      border-radius:0;
      margin: 30px;
      transform: rotate(360deg);
      width: 200px;
      height: 200px;
      background-color: rgb(238, 0, 255);
    }
    .anime{
      border-radius:30%;
      margin: 10px;
      float: left;
      width: 100px;
      height: 100px;
      background-color: rgb(255, 123, 0);
      animation: rotate 3s infinite, color 3s infinite alternate;
    }@keyframes rotate{
      from{transform: perspective(120px) rotateY(180deg);}
      50%{transform: perspective(120px) rotateX(180deg);}
      to{transform: perspective(120px) rotateZ(180deg);}
    }
    @keyframes color{
      from{background-color: rgb(255, 85, 0);}
      50%{background-color: rgb(55, 255, 0);}
      to{background-color: rgb(5, 68, 203);}
    }

		</style>
	</head>
	<body>		
		<div id="container">
			<div class="origin">
				<div id="movex"></div>		
			</div>
			<div class="origin">
				<div id="movey"></div>	
			</div>
			<div class="origin">
				<div id="movexy"></div>		
			</div>
      <div class="origin">
				<div id="scalex"></div>		
			</div>
			<div class="origin">
				<div id="scaley"></div>	
			</div>
			<div class="origin">
				<div id="scale"></div>		
			</div>
		</div>
    <div class="origin">
      <img src="tree.jpg" id="rotatex">
    </div>
    <div class="origin">
      <img src="tree.jpg" id="rotatey">
    </div>
    <div class="origin">
      <img src="tree.jpg" id="rotatez">
    </div>
    <div class="origin">
      <img src="tree.jpg" id="rotatexyz">
    </div>
    <div class="origin">
      <div id="skewx"></div>		
    </div>
    <div class="origin">
      <div id="skewy"></div>	
    </div>
    <div class="origin">
      <div id="skewxy"></div>		
    </div>
    <div class="box"></div>	
    <div id="ex">
      <div class="ease"> ease </div>
      <div class="linear"> linear </div>
      <div class="ease-in"> ease-in </div>
      <div class="ease-out"> ease-out </div>
      <div class="ease-in-out"> ease-in-out </div>
    </div>
      <div class="rbox"> </div>
      <div class="anime"></div>
    </body>
	</body>
</html>
```