# 데이터 정의 명령어(DDL)

1. 테이블을 생성하는 CREATE

2. ALTER - 테이블 변경

  * ADD : 칼럼 추가
  * RENAME : 칼럼명 변경
  * MODIFY : 칼럼 타입 변경
  * DROP : 칼럼삭제

3. RENAME - 테이블명 변경

4. TRUNCATE - 테이블 데이터 삭제
  SELECT FROM 테이블명 을 통해서도 데이터를 삭제할 수 있지만 DML이기 때문에 COMMIT 효과 없음.

5. DROP - 테이블 삭제

```SQL
-- 칼럼명에 공백 있을 시, 쌍따옴표로 묶어주면 사용 가능
-- 예약어를 칼럼명으로 사용하고 싶으면, 쌍따옴표로 처리 가능

CREATE TABLE KH_MEMBER(
    NAME VARCHAR2(10),
    AGE NUMBER
    );
SELECT * FROM KH_MEMBER;

ALTER TABLE KH_MEMBER ADD EMAIL VARCHAR2(100);

ALTER TABLE KH_MEMBER RENAME COLUMN AGE TO AGE2;

--조건에 맞지 않는 데이터가 이미 들어있다면, 수정이 불가능함
ALTER TABLE KH_MEMBER MODIFY NAME VARCHAR2(2);

ALTER TABLE KH_MEMBER DROP COLUMN EMAIL;

INSERT INTO KH_MEMBER (NAME, AGE2)
               VALUES ('아이유',20);

RENAME KH_MEMBER TO NEW_MEMBER;
SELECT * FROM NEW_MEMBER;
               
TRUNCATE TABLE NEW_MEMBER;

DROP TABLE NEW_MEMBER;
```

