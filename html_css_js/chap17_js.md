# [14일차] Do it! HTML+CSS+자바스크립트 웹 표준의 정석 / 602~641p / 17-4 DOM에서 노드 추가&삭제하기

### 17-1 문서 객체 모델 알아보기

    문서 객체 모델(DOM) : 자바스크립트를 이용하여 웹 문서에 접그나고 제어할 수 있도록 객체를 사용해 웹 문서를 체계적으로 정리하는 방법

    DOM 트리 : 노드를 부모와 자식 구조로 표현하면 나무 형태가 됨.

​

### 17-2 DOM 요소에 접근하고 속성 가져오기

    getElementById() :  id선택자로 접근

    getElementsByClassNaae() : class값으로 접근

    getElementsByTagName() : 태그 이름으로 접근

    querySelecter() : 선택자,태그로 접근

    querySelecterAll() : 선택자, 태그로 접근(해당되는 모든 노드)

    getAttribute() : 속성값 가져오기

    setAttribute() : 속성값 수정하기

​

### 17-3 DOM에서 이벤트 처리하기

    1. DOM요소에 함수 직접 연결

    2. 함수 이름을 사용해 연결

    event객체 : 이벤트 정보 저장(다양한 프로퍼티와 메서드 존재)

    3. addEventListener() 사용

    CSS속성 접근방법 : dovument.요소명.style.속성명

​

### 17-4 DOM에서 노드 추가*삭제하기

    createElement() : 요소 노드 추가

    createTextNode() : 텍스트 노드 추가

    appendChild() : 자식노드 연결하기

    createAttribute() : 속성 노드 추가

    setAttributeNode() : 속성 노드 연결

    ​

    노드 삭제방법은 부모노드를 찾아서 부모노드에서 해당 노드를 삭제해야함. 자체삭제 불가.

    parentNode 프로퍼티 : 현재 노드의 부모노드에 접근해서 부모노드의 요소노드를 반환

    removeChild() : 자식노드 삭제

```html
<!DOCTYPE html>
<html lang="ko">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta http-equiv="X-UA-Compatible" content="ie=edge">
	<title>DOM에 접근하기</title>
	<link rel="stylesheet" href="dom.css">
  <style>
    #container2 {
      width:300px;
      margin:10px auto;
    }
    #box{
      border: 1px solid green;
      height: 100px;
      width: 100px;
      margin: auto;
      transition : 1s;
    }
    #container3 {  
      width:500px;
      margin:20px auto;
      padding:20px;
    }
    input3[type="text"] {
      width:370px;
      float:left;
      height:30px;
      padding-left:30px;
    }
    button {
      width:90px;
      height:30px;
      float:right;
      background:#222;
      color:#fff;
      border:none;
    }
hr { clear:both; display:none; }
ul { list-style:none; padding-top:50px;}
li { line-height: 2.5; }
li:hover { cursor:pointer;}
  </style>
</head>
<body>
	<div id="container">
		<h1 id="heading">에디오피아 게뎁</h1>
			<div id="prod-img">
				<img src="coffee-pink.jpg" alt="에디오피아 게뎁">
			</div>
			<div id="desc">
				<h2 class="bright">Information</h2>
				<p>2차 세계대전 이후 설립된 <span class="accent">게뎁농장</span>은 유기농 인증 농장으로 여성의 고용 창출과 지역사회 발전에 기여하며 3대째 이어져 내려오는 오랜 역사를 가진 농장입니다. 게뎁 농장은 <span class="accent">SCAA 인증</span>을 받은 커피 품질관리 실험실을 갖추고 있어 철처한 관리를 통해 스페셜티커피를 생산합니다.</p>
				<h2>Flavor Note</h2>
				<p class="bright">은은하고 다채로운 꽃향, 망고, 다크 체리, 달달함이 입안 가득.</p>
			</div>
	</div>

  <div id="container2">
    <img src="cup-1.png" id="cup">		
  </div>

  <div id="box"></div>



	<script>
    var isRed = true; 
    var cup = document.querySelector("#cup");
    cup.addEventListener("mouseover",function(){
      cup.style.transform = "rotate(40deg)";
    });
    cup.addEventListener("mouseout", function(){
      cup.style.transform = "rotate(0)";
    });
    cup.onclick = function(){
      if(isRed){
        cup.src = "cup-2.png";
        isRed = false;
      } else {
        cup.src = "cup-1.png";
        isRed = true;
      }
    }

    var box = document.querySelector("#box");
    box.addEventListener("mouseover", function(){
      box.style.background = "green";
      box.style.borderRadius = "50%";
    })
    box.addEventListener("mouseout", function(){
      box.style.background = "";
      box.style.borderRadius = "";
    })

    function newRegister(){
      var newItem = document.createElement("li");
      var subject = document.querySelector("#subject");
      var newText = document.createTextNode(subject.value);

      var itemList = document.querySelector("#itemList");
      itemList.appendChild(newItem);
      newItem.appendChild(newText);

      subject.value = "";

      var items = document.querySelectorAll("li");
      for(let i = 0 ; i<items.length ; i++){
        items[i].addEventListener("click",function(){
          if(this.parentNode){
            this.parentNode.removeChild(this);
          }
        })
      }

    }

	</script>
  <div id="container3">
    <h1>Web Programming</h1>
    <p>공부할 주제를 기록해 보세요</p>
    <form action="">
      <input type="text" id="subject" autofocus>
      <button onclick="newRegister(); return false;">추가</button>
    </form>
    <hr>  
    <ul id="itemList">
    </ul>  
  </div>
</body>
</html>
```