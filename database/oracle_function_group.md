# 함수(그룹)

```sql
--GROUP BY : 사용인자를 모두 사용하여 그룹 나누기
SELECT DEPTNO, JOB, SUM(SAL) 총급여
FROM EMP
GROUP BY DEPTNO, JOB;

--ROLLUP : 오른쪽부터 사용인자를 하나씩 줄여가면서 그룹 나누기
SELECT DEPTNO, JOB, SUM(SAL) 총급여
FROM EMP
GROUP BY ROLLUP(DEPTNO, JOB);

--CUBE : 사용인자를 활용한 모든 경우의 수 별로 그룹 나누기
SELECT DEPTNO, JOB, SUM(SAL) 총급여
FROM EMP
GROUP BY CUBE(DEPTNO, JOB);

--GROUPING SET : 각각의 인자별로 그룹 나누기(인자 하나만 사용)
SELECT DEPTNO, JOB, SUM(SAL) 총급여
FROM EMP
GROUP BY GROUPING SETS(DEPTNO, JOB);

--ROLLUP, CUBE, GROUPING SET 3개 함수에 대해 보조
--GROUPING
SELECT 
    DEPTNO
    , CASE    --GROUPING(DEPTNO) 널값인지판단
        WHEN GROUPING(DEPTNO) = 1 THEN '부서번호제외통계'
        WHEN GROUPING(JOB) = 1 THEN 'JOB제외통계'
        ELSE '엘스'
      END "통계에서 제외한 칼럼"
    , JOB
    , SUM(SAL) 총급여
FROM EMP
GROUP BY CUBE(DEPTNO, JOB);
```