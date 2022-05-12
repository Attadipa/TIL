# [2일차] Do it! HTML+CSS+자바스크립트 웹 표준의 정석 / 64~120p / 04-6 하이퍼링크 삽입하기 까지

03-4 웹 문서 구조를 만드는 시맨틱 태그

시맨틱태그 : 이름만 봐도 의미를 알 수 있는 태그

header, nav, main, article, section, aside, footer, div

​

04-1 텍스트 입력하기

hn ex) h1, h2, 등 -> 제목(숫자가 커질수록 크기가 작아짐)

p 단락바꾸기

br 줄 바꾸기 -> 닫는태그없음

blockquote 인용문쓰기 -> 살짝 들여쓰기됨

strong, b 굵게 -> strong은 의미강조도 추가됨

em, i 이탤릭체 -> em은 의미강조도 추가됨4

​

04-2 목록 만들기

ol,li 순서있는 목록, 항목(순서 type지정가능)

ul, li 순서없는 목록, 항목

dl, dt, dd 설명목록,항목,설명(순서는 없음)

​

04-3 표 만들기

table 표만들기

caption 표제목

tr 표의 행

th, td 표의 셀 -> th는 제목 행의 셀로서 진하게 표시 및 가운데 정렬

​

04-4 이미지 삽입하기

img src="이미지 파일 경로 alt="대체용 텍스트"

​

04-5 오디오와 비디오 삽입하기

object, embed 다양한 멀티미디어 파일 삽입

audio 오디오파일 삽입

video 비디오파이 삽입

​

04-6 하이퍼링크 삽입하기

a href="링크할 주소" target ="_blank">텍스트 또는 이미지 /a

target ="_blank"->새탭에서 웹페이지 열림

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>레드향</title>
  <style>
    table{
      border: 1px solid;
      border-collapse: collapse;
    }
    td,th{
      border: 1px solid;
      padding: 10px;
    }
  </style>
</head>

<body>
  <img src="images/tangerines.jpg">
  <audio src="medias/spring.mp3" controls autoplay></audio>
  <video src="medias/salad.mp4" controls width="500"></video>
  <h1><a href="https://namu.wiki/w/%EB%A0%88%EB%93%9C%ED%96%A5" target="_blank">레드향</h1></a>

  <ol type="a">
    <li><b><i>맛좋은 레드향</i></b></li>
    <li><strong>신선한 레드향</strong></li>
    <li><em>달콤한 레드향</em></li>
  </ol>


  <h2>상품 구성</h2>
  <table>
    <caption>선물용과 가정용 상품 구성</caption>
    <tr>
      <th>용도</th>
      <th>중량</th>
      <th>갯수</th>
      <th>가격</th>
    </tr>
    <tr>
      <td>선물용</td>
      <td>3kg</td>
      <td>11~16과</td>
      <td>35,000원</td>
    </tr>
    <tr>
      <td>선물용</td>
      <td>5kg</td>
      <td>18~26과</td>
      <td>52,000원</td>
    </tr>
    <tr>
      <td>가정용</td>
      <td>3kg</td>
      <td>11~16과</td>
      <td>30,000원</td>
    </tr>
    <tr>
      <td>가정용</td>
      <td>5kg</td>
      <td>18~26과</td>
      <td>47,000원</td>
    </tr>
  </table>
</body>
</html>
```