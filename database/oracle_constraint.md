# 제약조건


```SQL

--NOT NULL : NULL값 허용하지 않음

--DEFAULT : 기본으로 들어갈 값

--CHECK : 체크 조건 검사를 통과해야만 데이터 저장 가능

--PRIMARY KEY : 기본키(식별자)

--UNIQUE : 중복 허용하지 않음(NULL은 허용)

--FOREIGN KEY : 외래키(다른 테이블 칼럼 참조)



CREATE TABLE ZZZ(
    ID VARCHAR2(100) NOT NULL
);
--테이블 생성 이후에도 제약조건 수정가능
ALTER TABLE ZZZ MODIFY ID VARCHAR2(200);

-- DEFAULT : 기본으로 들어갈 값
CREATE TABLE TTT(
    ID VARCHAR2(100) DEFAULT 'ADMIN'
);
--테이블 생성 이후에도 제약조건 수정 가능
ALTER TABLE ZZZ MODIFY ID VARCHAR2(100) DEFAULT 'HONGGILDONG';

--CHECK : 체크 조건 검사를 통과해야만 데이터 저장 가능
CREATE TABLE ZZZ(
    ID VARCHAR2(100) CHECK(ID.LENGTH < 10)
);
--테이블 생성 이후에도 제약조건 수정 가능
ALTER TABLE ZZZ ADD CONSTRAINT ZZZIDCHECK
CHECK(REGEXP_LKE(PHONE LIKE '^010-\d{3,4}-\d[4]$'));

--PRIMARY KEY : 기본키(식별자) (NOT NULL, UNIQUE)
CREATE TABLE ZZZ(
    ID VARCHAR2(100) PRIMARY KEY
);

CREATE TABLE ZZZ(
    ID VARCHAR2(100),
    CONSTRAINT ZZZTBK PRIMARY KEY(ID)
);

ALTER TABLE ZZZ ADD CONSTRAINT ZZZTBPK PRIMARY KEY(ID);

--UNIQUE : 중복 방지
CREATE TABLE ZZZ
ADD CONSTRAINT ZZZTBIDUQ UNIQUE(ID);

--FOREIGN KEY : 부모테이블의 기본키를 참조함
CREATE TABLE STUDENT(
    NO NUMBER PRIMARY KEY
   ,NAME VARCHAR2(100)
);
DROP TABLE STUDENT;
DROP TABLE SCORE;

CREATE TABLE SCORE(
    STD_NO NUMBER
   ,GRADE CHAR(2)
   ,CONSTRAINT SCORE_FK FOREIGN KEY(STD_NO) REFERENCES STUDENT(NO) ON DELETE CASCADE
);

--ON DELETE CASCADE : 부모테이블이 값이 삭제되면 자식테이블의 값도 삭제 (잘 안씀)
--ON DELETE SET NULL : 부모테이블이 값이 삭제되면 자식테이블의 값은 NULL

INSERT INTO STUDENT(NO,NAME)
VALUES(1, 'JAVA');
COMMIT;

INSERT INTO SCORE(STD_NO, GRADE)
VALUES('1', 'A');
COMMIT;

INSERT INTO STUDENT(NO, NAME)
VALUES(1, 'JAVA');
```