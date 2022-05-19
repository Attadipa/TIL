# 함수(조건문)

```sql
-- DECODE
SELECT EMPNO, ENAME, DEPTNO, DECODE(DEPTNO, 10, '영업1팀', 20, '영업2팀', 30, '영업3팀') AS 부서명
FROM EMP;

-- CASE WHEN THEN END
SELECT
       EMPNO
      ,ENAME 
      ,DEPTNO
      ,CASE
      WHEN DEPTNO=10 THEN '영업1팀'
      WHEN DEPTNO=20 THEN '영업2팀'
      WHEN DEPTNO=20 THEN '영업3팀'
      ELSE '부서없음'
      END AS 부서
FROM EMP
ORDER BY DEPTNO;

SELECT  EMP.*,
        CASE
          WHEN SAL<=1000  THEN '신입'
          WHEN SAL BETWEEN 1001 AND 2000  THEN '초급'
          WHEN SAL BETWEEN 2001 AND 3000  THEN '중급'
          WHEN SAL BETWEEN 3001 AND 4000  THEN '고급'
          ELSE '특급'
        END AS 등급
FROM EMP;
```