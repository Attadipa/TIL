
# 서브쿼리

하나의 SQL 문에 포함되어 있는 또 다른 SQL 문

```sql
--인라인 뷰
SELECT ROWNUM, ENAME, SAL
FROM
(
    SELECT *
    FROM EMP
    ORDER BY SAL DESC
)
WHERE ROWNUM<=3;


--서브쿼리(다중 열)
SELECT EMPNO, ENAME, SAL, DEPTNO
FROM EMP
WHERE(DEPTNO, SAL) IN (SELECT DEPTNO, SAL
                       FROM EMP
                       WHERE DEPTNO = 30);
                       
--스칼라 서브쿼리(단일 행)
SELECT ENAME, 
       DEPTNO, 
       SAL,
      (
       SELECT TRUNC(AVG(SAL))
       FROM EMP
       WHERE DEPTNO = E.DEPTNO
       ) AS 부서평균급여
FROM EMP E;

--상(호연)관 (서브)쿼리
SELECT 
    ENAME
    , JOB
    , 
    (
    SELECT DNAME
    FROM DEPT
    WHERE DEPTNO = E.DEPTNO
    ) DNAME
FROM EMP E;

    SELECT *
    FROM DEPT;


-- OREDR BY 절 서브쿼리
SELECT EMPNO, ENAME, DEPTNO, HIREDATE
FROM EMP E
ORDER BY 
(
    SELECT DNAME
    FROM DEPT
    WHERE DEPTNO = E.DEPTNO
)
DESC
;

--TRUNCATE
SELECT * FROM EMP;
TRUNCATE TABLE EMP;
DELETE FROM EMP;
ROLLBACK;
```