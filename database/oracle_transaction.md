### 트랜잭션(Transaction)

1. 정의 : 쪼갤 수 없는 업무 처리의 최소 단위

EX) 계좌이체 : 내 통장의 돈을 다른 통장으로 옮기는 것
    1. 이체할 금액 확인
    2. 내 통장 잔고 확인
    3. 내 통장 금액 변경
    4. 상대방 통장 잔고 변경

2. 트랜잭션 제어 명령어(TCL : Transaction Control Language)
  1. 커밋(COMMIT) -> 데이터베이스에 반영
  2. 롤백(ROLLBACK) -> 트랜잭션 취소(마지막 커밋까지)

```sql
CREATE TABLE MY_TB(
    NAME    CHAR(9),
    AGE     NUMBER
    );
    
INSERT INTO MY_TB(NAME, AGE)
        VALUES('ABC',20);
   
COMMIT;
     
INSERT INTO MY_TB
            VALUES('ZZZ', 22);

ROLLBACK;

SELECT * FROM MY_TB;

DROP TABLE MY_TB;
```
