# [3일차] Do it! HTML+CSS+자바스크립트 웹 표준의 정석 / 122~164p / 05-4 폼에서 사용하는 여러 가지 태그까지


05-1 폼 삽입하기

form : 사용자가 웹사이트로 정보를 보내는 요소

field, legend : 폼 요소를 그룹핑

label : 레이블 텍스트와 폼 요소 연결

​

05-2 사용자 입력을 위한 input태그

input : 다양한 폼에서 사용자가 정보를 입력받을 때 사용(type활용)

input type="종류" : 

text, password, search, url, email, tel, checkbox, radio, number, range, date, month, week, time, datetime, 

datetime-local, submit, reset, image, button, file, 

​

05-3 input 태그의 주요 속성

input type="종류" : 

autofocus, readonly, required

​

05-4 폼에서 사용하는 여러 가지 태그

textarea : 여러 줄 입력하는 텍스트 영역

select, option : 드롭다운 목록

datalist, option : 데이터 목록

button : 버튼 생성

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>웹 폼 삽입하기</title>
</head>

<body>
  <form action="">
    <h1>레드향 주문하기</h1>
    <input type="hidden" name="url" value="사이트를 통한 직접 로그인">
    <label for="user-id">아이디 : </label>
    <input type="text" id="user-id">
    <label>비밀번호 : <input type="password"></label>
    <input type="submit" value="전송">

    <br>
    <br>
    <fieldset>
      <legend>배송정보</legend>
      <ol>
        <li>
          <label for="prod">주문상품</label>
          <input type="text" id="prod" value="상품용 3kg" readonly>
        </li>
        <li>
          <label for="user">이름</label>
          <input type="text" id="user" required autofocus>
        </li>
        <li>
          <label for="addr">배송 주소</label>
          <input type="text" id="addr" required>
        </li>
        <li>
          <label for="mail">이메일</label>
          <input type="email" id="mail">
        </li>
        <li>
          <label for="phone">연락처</label>
          <input type="tel" id="phone" required>
        </li>
        <li>
          <label for="day">배송 지정</label>
          <input type="date" id="day" required>
          (주문일로부터 최소 3일 이후)
        </li>
        <li>
          <label for="memo">메모</label> 
          <textarea id="memo" cols="40" rows="4"></textarea>
        </li>
        <li> 사은품 선택
          <label>
            <select>
              <option value="poster_1">에일리 포스터</option>
              <option value="poster_2" selected>아이유 포스터</option>
              <option value="figure_1">건담 피규어</option>
              <option value="figure_2">피카츄 피규어</option>
            </select>
          </label>  
        </li>
        <li>
          <label><input type="text" list="goods"></label> 
            <datalist id="goods">
              <option value="poster_1">에일리 포스터</option>
              <option value="poster_2" selected>아이유 포스터</option>
              <option value="figure_1">건담 피규어</option>
              <option value="figure_2">피카츄 피규어</option>
            </datalist> 
        </li>
        <li>
          <input type="file">
        </li>
        <li>
          <input type="image" src="" alt="대체텍스트">
        </li>
        <li>
          <input type="button" value="공지창 열기" onclick="window.open('index.html')">
        </li>
      </ol>
    </fieldset>
    <br>
    <fieldset>
      <legend>상품 선택</legend>
      <b>주문할 상품을 선택해 주세요</b>
      <ul>
        <li>
          <label><input type="checkbox" value="s_3"> 선물용 3kg</label>
          <input type="number" min="0" max="5" value="1">개
        </li>
        <li>
          <label><input type="checkbox" value="s_5"> 선물용 5kg</label>
          <input type="number" min="0" max="3" value="1">개
        </li>
        <li>
          <label><input type="checkbox" value="f_3"> 가정용 3kg</label>
          <input type="range" min="0" max="5" value="1">개
        </li>
        <li>
          <label><input type="checkbox" value="f_3"> 가정용 5kg</label>
          <input type="range" min="0" max="3" value="1">개
        </li>
      </ul>
      <b>포장 선택</b>
      <ul>
        <li>
          <label><input type="radio" name="gift">선물포장</label>
        </li>
        <li>
          <label><input type="radio" name="gift">선물포장 안 함</label>
        </li>
      </ul>
    </fieldset>
    <button type="submit">제출</button>
    <input type="reset" value="초기화">
  </form>
  <h2>날짜 지정하기</h2>
  <input type="date">
  <input type="month">
  <input type="week">
  <h2>시간 지정하기</h2>
  <input type="time">
  <input type="datetime">
  <input type="datetime-local">
  <h2>범위 제한하기</h2>
  <input type="date" min="2022-05-07" max="2022-05-28">
  <input type="time" min="14:00" max="16:00">
</body>
</html>
```