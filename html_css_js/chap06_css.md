# [4일차] Do it! HTML+CSS+자바스크립트 웹 표준의 정석 /122~164p / 05-4 폼에서 사용하는 여러 가지 태그까지 

06-1 웹 문서에 디자인 입히기

스타일 사용이유

1. 내용과 디자인의 분리

2. 반응형 웹디자인

​

06-2 스타일과 스타일 시트

스타일 시트 : 여러 스타일 규칙들을 한군데 묶어 놓은 것

스타일 시트 종류

1.브라우저 기본 스타일 (별도의 스타일 적용안하면)

2.사용자스타일

    - 인라인스타일

    - 내부 스타일 시트

    - 외부 스타일 시트 (가장 많이 쓰임)

​

06-3 CSS기본 선택자 알아보기

선택자 종류

1. 전체 선택자 *{}

2. 타입 선택자 태그명{}

3. 클래스 선택자 .클래스명{}

4. id 선택자 #id명{}

5. 그룹 선택자 선택자1, 선택자2{}

(별도의 선택자 아님. 여러 선택자를 묶어놓은 것)

​

06-4 캐스케이딩 스타일 시트 알아보기

캐스케이딩은 스타일 시트 간의 우선순위가 위에서 아래로 계단식으로 적용된다는 의미

(스타일 시트간의 충돌 막기 위함)

1. 스타일 우선순위 - 중요도와 적용범위에 따라 결정 

   - 중요도 우선순위 : 사용자스타일 -> 제작자 스타일 -> 브라우저 기본 스타일

   - 적용범위 우선순위(중요도가 같은 경우) :

       !important -> 인라인 스타일 -> id스타일 -> 클래스 스타일 -> 타입 스타일

   - 소스 코드의 작성 순서(적용범위 같은 경우):

     나중에 작성한 스타일 -> 먼저 작성한 스타일

2. 스타일 상속 - 태그의 포함관계에 따라 부모 요소의 스타일을 자식에게 전달

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>상품 소개 페이지</title>
  <style>
    /* * {
      margin: 0;
      padding: 0;
    } */

    
    /* 타입선택자 */
    p{
      color: blue;
    }

    h1{
      color: blue;
    }

    /* class 선택자 */
    .redtext{
      color: red;
    }

    /* id 선택자 - 한 번만 사용 권장(유일해야 됨)*/
    #container{
      border: 1px solid #222;
      padding: 10px;
    }
    /* 그룹 선택자 */
    h1, p {
      color: blue !important;
    }

    h1{
      color: aqua;
    }

    body{
      font-size: 20px;
    }
  </style>
</head>
<body>
  <div id="container">
    <h1 style="color:blueviolet">레드향</h1>
    <p>껍질에 붉은 빛이 돌아 <span class="redtext">레드향</span> 이라 불린다.</p>
    <p>레드향은 한라봉과 귤을 교배한 것으로 일반 귤보다 2~3배 크고, 과육이 붉고 통통하다.</p>
    <p><span class="redtext"> 비타민 C와 비타민 P가 풍부해</span>  혈액순환, 감기예방 등에 좋은 것으로 알려져 있다.</p>
  </div>

</body>
</html>
```