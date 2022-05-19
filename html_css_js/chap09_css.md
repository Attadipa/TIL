# [7일차] Do it! HTML+CSS+자바스크립트 웹 표준의 정석 / 293~314p / 09-3 그러데이션 효과로 배경 꾸미기까지

09-1 배경색과 배경 범위 지정하기

background-color : 배경색 지정

background-clip : 배경색 적용 범위 조절

​

09-2 배경 이미지 지정하기

background-image : 배경에 이미지 넣기

background-repeat : 배경 이미지의 반복(repeat, repeat-x, repeat-y, no-repeat)

background-position : 배경 이미지의 위치 조절

background-origin : 배경 이미지의 적용 범위 조절

background-attachment : 배경 이미지의 고정

background : 배경 이미지 관련 속성 종합 설정

background-size : 배겨이미지 크기 조절

​

09-3 그러데이션 효과로 배경 꾸미기

linear-gradient : 선형 그러데이션

radial-gradient : 원형 그러데이션

repeating-linear-gradient : 선형 그러데이션(반복 패턴)

repeating-radial-gradient : 원형 그러데이션(반복 패턴)

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>배경 이미지</title>
  <style>
    .box {
      /* background-image:url('bg2.png');
      background-repeat: no-repeat;
      background-position:top right;
      background-attachment: fixed; */
    
      border: 1px solid black;
      width:400px;
      height:400px;
      margin:20px;
      background: url('bg4.jpg') no-repeat left top;
      background-size: contain;
    }
    #container{
      width: 1100px;
      margin: 50px auto;
    }

    body{
      background:url(bg1.jpg) no-repeat;
      background-size: cover;
    }
    .grad{
      width: 250px;
      height: 250px;
      border: 1px solid black;
      display: inline-block;
      margin: 5px;
      padding: 10px;

      background: linear-gradient(45deg, white 30%, skyblue 60%, blue);
      background-clip:content-box;
    }
    .grad1{
      width: 250px;
      height: 250px;
      border: 1px solid black;
      display: inline-block;
      margin: 5px;

      background: radial-gradient( white, yellow, red)
    }
    .grad2{
      width: 250px;
      height: 250px;
      border: 1px solid black;
      display: inline-block;
      margin: 5px;

      background: radial-gradient(circle at 0% 70%, white, yellow, red)
    }
    .grad3{
      width: 250px;
      height: 250px;
      border: 1px solid none;
      border-radius: 50%;
      display: inline-block;
      margin: 10px;

      background: repeating-radial-gradient(circle at 30% 30%, white, red, yellow 10% 10px)
    }
    .grad4{
      width: 200px;
      height: 200px;
      border: 1px solid none;
      border-radius: 50%;
      display: inline-block;
      margin: 10px;

      background: radial-gradient(circle at 70% 70%, white 1%, rgb(70, 157, 0) 40%, rgb(8, 63, 0))
    }
    .grad5{
      width: 150px;
      height: 150px;
      border: 1px solid none;
      border-radius: 50%;
      display: inline-block;
      margin: 10px;

      background: radial-gradient(circle at 50% 200%, black 5%, rgb(91, 0, 0) 40%, rgb(252, 0, 0))
    }
    .grad6{
      width: 100px;
      height: 100px;
      border: 1px solid none;
      border-radius: 50%;
      display: inline-block;
      margin: 10px;

      background: repeating-radial-gradient( rgb(255, 255, 255), rgb(117, 0, 143), rgb(33, 0, 53) 10px)
    }
  </style>
</head>
<body>
  <div id="container">
    <h1 class="box">배경 꾸미기</h1>
  </div>
  <div class="grad">
    <span style="font-size: 30px">linear</span>
  </div>
  <div class="grad1">
    <span style="font-size: 30px">radial</span>
  </div>
  <div class="grad2">
    <span style="font-size: 30px">radial</span>
  </div>
  <div class="grad3">
  </div>
  <div class="grad4">
  </div>
  <div class="grad5">
  </div>
  <div class="grad6">
  </div>
</body>
</html>
```