# 함수(문자열 관련)


```sql
-- SUBSTR

SELECT SUBSTR('ABCDEFGHIJK',3,50) FROM DUAL;
SELECT * 
FROM EMP
WHERE ENAME LIKE '%' || SUBSTR('ABCDEFGHIJK',5,1) || '%';

--CONCAT : 문자열 합치는 기능
SELECT CONCAT('ABC','아이유')
FROM DUAL;

--TRIM : 공백 제거
--LTRIM : 왼쪽 공백 제거
--RTRIM : 오른쪽 공백 제거

SELECT '   ABC   'AS T
FROM DUAL;

SELECT LTRIM('   ABC   ')AS T
FROM DUAL;

SELECT RTRIM('   ABC   ')AS T
FROM DUAL;

SELECT TRIM('   ABC   ') AS T
FROM DUAL;

--LOWER : 소문자로 변경
--UPPER : 대문자로 변경
SELECT  LOWER('ABC')
FROM DUAL;
SELECT  UPPER('abc')
FROM DUAL;

--PAD: 원하는 사이즈 만큼 빈칸을 채워줌(내가 원하는 문자로)
--LPAD:
--RPAD:
SELECT RPAD('ABD',10,'X') AS TEST
FROM DUAL;
SELECT LPAD('ABD',10) AS TEST
FROM DUAL;

--INICAP : 첫글자를 대문자로 바꿔줌
SELECT INITCAP('abc')
FROM DUAL;

--INSTR : 특정 문자열이 몇번째에 존재하는지 확인
SELECT INSTR('ABCDEFG','CD')
FROM DUAL;

--LENGTH
SELECT LENGTH('ABC123ZZZ안녕')
FROM DUAL;
```