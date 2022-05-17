# [5일차] Do it! HTML+CSS+자바스크립트 웹 표준의 정석 / 194~232p / 07-5 표 스타일까지

07-1 글꼴 관련 스타일

font-family : 글꼴 지정

font-size : 글자 크기(px, em 등)

font-style : 글자체 ( 이탤릭체 등)

font-weight : 글자 굵기

​

07-2 웹폰트 사용

사용자 시스템에 없는 글꼴 사용가능

구글 웹폰트 -> 글꼴 선택 -> import문 가져오기 -> font-family에 해당 글꼴 지정

style태그 바로 밑에 import문 배치해야 적용가능

​

07-3 텍스트 관련 스타일

color : 글자색 (표현방식 : 색상명, #16진수, rgb/rgba, hsla 등)

text-align : 텍스트 정렬

line-height : 줄 간격 조절

text-decoration : 텍스트의 줄 표시 및 삭제 가능(보통 하이퍼링크의 밑줄 삭제시 많이 쓰임)

text-shadow : 그림자 효과(가로, 세로, 번짐, 색상)

text-transform : 대소문자 변환

letter-spacing : 자간 조절

word-spacing : 단어간격 조절

​

07-4 목록 스타일

list-style-type : 불릿모양과 번호 스타일 지정

list-style-image : 불릿 대신 이미지 사용

list-style-position : 목록 들여쓰기

list-style : 목록 속성 한꺼번에 표시

​

07-5 표 스타일

caption-side : 표 제목 위치 지정

border : 테두리그리기

border-spacing : 셀 사이의 여백

border-collapse : 표와 셀 테두리 합치기

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>상품 소개 페이지</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Song+Myung&display=swap'); 
    @import url('https://fonts.googleapis.com/css2?family=Noto+Serif+KR:wght@600&display=swap');

    /* 웹폰트 임포트문은 <style>태그 바로 다음에 와야 임포트된다. */
    body{
      background: url(bg.jpg);
     
    }
    h1{
      font-family: 'Song Myung', 바탕; 
      /* 인터넷 연결불가시 대신 표시할 폰트 설정 필요*/

      font-size: 7em;
      color:#d97093ac;
      text-shadow: black 10px 10px 5px;
    }
    .italic{
      font-style: italic;
    }
    .accent{
      font-weight: 1000;
      font-size: large;
    }
    .tstyle{
      text-align: right;
      line-height: 3;
    }
    p{
      font-size: 2em;
      font-family: 'Noto Serif KR', 바탕; 
      color: antiquewhite;
    }
    .tstyle2{
      text-decoration: underline;
    }
    a{
      text-decoration: none;
    }
    .mylist{
      list-style-type: square;
      color: aliceblue;
    }
    .mylist2{
      list-style-type: upper-alpha;
      color: aliceblue;
    }
    table{
      color: blanchedalmond;
      caption-side:bottom;
      border: 1px solid #fff;
      border-collapse: collapse;
      
    }
    td,th{
      border: 1px solid #fff;
      padding: 10px;
    }
    th{
      background-color:rgb(9, 12, 61);
      
    }
  </style>
</head>
<body>
  <h1>레드향</h1>
  <p class="tstyle">껍질에 붉은 빛이 돌아 <span class="tstyle2">레드향</span>이라 불린다.</p>
  <p>레드향은 한라봉과 귤을 교배한 것으로</p>
  <p>일반 귤보다 <a href="#">2~3배 크고,</a> 과육이 붉고 통통하다.</p>   
  
  <h2 style="color:cyan">도서 시리즈</h2>
  <ul class="mylist">
    <li>Do it! 시리즈</li>
    <li>첫 코딩 시리즈</li>
    <li>된다 시리즈</li>
  </ul>
  <ol class="mylist2">
    <li>Do it! 시리즈</li>
    <li>첫 코딩 시리즈</li>
    <li>된다 시리즈</li>
  </ol>
  <table>
    <caption>선물용과 가정용 상품 구성</caption>
    <thead>
      <tr>
        <th>용도</th>
        <th>중량</th>
        <th>갯수</t>
        <th>가격</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td rowspan="2">선물용</td>
        <td>3kg</td>
        <td>11~16과</td>
        <td>35,000원</td>
      </tr>
      <tr>
        <td>5kg</td>
        <td>18~26과</td>
        <td>52,000원</td>
      </tr>
      <tr>
        <td rowspan="2">가정용</td>
        <td>3kg</td>
        <td>11~16과</td>
        <td>30,000원</td>
      </tr>   
      <tr>
        <td>5kg</td>
        <td>18~26과</td>
        <td>47,000원</td>
      </tr>
    </tbody>        
  </table>
</body>
</html>
```