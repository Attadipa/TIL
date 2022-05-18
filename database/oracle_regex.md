# 정규표현식 (REGULAR EXPRESSION)


    [] : 한 글자
        EX) [김이박최] , [0123456789] , [0-9]
    \d : 숫자(digit) 하나
        EX) \d\d\d\d : 숫자 4개
    {} : 반복되는 갯수
        EX) \d{10} : 숫자 10개
        EX) \d{3,4} : 숫자 3개 또는 4개
    ^ : 문자열의 시작
    $ : 문자열의 끝

    \w : 문자 하나
    * : 0개 이상
    + : 1개 이상
    | : 또는
        EX) abc|zzz|qqq : abc 또는 zzz 또는 qqq 셋 중에 하나
    \D : 숫자가 아닌 것

정규표현식은 검색해서 쓰는게 정신건강에 좋습니다.

```SQL

CREATE TABLE MEMBER(
    NO      NUMBER,
    ID      VARCHAR2(100),
    PWD     VARCHAR2(100),
    PHONE   VARCHAR2(100)
);
ALTER TABLE MEMBER ADD EMAIL VARCHAR2(100);
SELECT * FROM MEMBER;
DESC MEMBER;


INSERT INTO MEMBER VALUES(8, '지젤', '1234', '010-1234-5678', 'asdf1234@naver.com');
SELECT * FROM MEMBER
WHERE REGEXP_LIKE (PHONE,'^01[01679]-\d{4}-\d{4}$');

--이메일 정합성 검사

SELECT *
FROM MEMBER
WHERE REGEXP_LIKE (EMAIL , '\D\w*@\D\w*.(com|co.kr|net)');

```