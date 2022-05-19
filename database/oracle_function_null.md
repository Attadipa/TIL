# 함수 (NULL처리)

```sql
-- NVL : NULL인지 판단 후 NULL이면 지정된 값 반환
SELECT NVL(COMM*12,0)
FROM EMP;

-- NVL2 : NVL기능에 추가로 NULL이 아닐때도 지정된 값 반환 가능
SELECT NVL2(COMM,COMM*12,0)
FROM EMP;

-- NULLIF : 특정 조건 만족시 NULL반환
SELECT EMPNO, ENAME, JOB, SAL, COMM, NULLIF(SAL, 800)
FROM EMP;
```
