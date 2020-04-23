## DDL

- 테이블 정의
- 테이블 수정
- 테이블 삭제
- 제약조건



칼럼 추가

```sql
SQL> alter table member
  2  add (point number, name varchar2(20), email varchar2(20));

Table altered.


SQL> alter table member
  2  add(tel varchar2(15), info varchar2(10));

Table altered.

```



칼럼 제약조건 수정

```sql
SQL> alter table member
  2  modify (tel char(11));
```



칼럼 삭제

```sql
SQL> alter table member
  2  drop column info;
```



칼럼 이름 변경

```sql
SQL> alter table member
  2  rename column addr to address;
```



테이블 삭제

```sql
SQL> drop table member;

Table dropped.
```



name 제약조건 not null 주고 null을 주었으시

```sql
SQL> create table member(
  2       id varchar2(10) primary key,
  3       pass varchar2(10),
  4       name varchar2(20) not null,
  5       addr varchar2(20))
  6  ;

Table created.

SQL> insert into member(id,name) values('jang',null);
insert into member(id,name) values('jang',null)
                                          *
ERROR at line 1:
ORA-01400: cannot insert NULL into ("SCOTT"."MEMBER"."NAME")
```



제약조건 조회

```sql
SQL> desc user_constraints;
 Name                                                                                                                                                                          Null?    Type
 ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -------- --------------------------------------------------------------------------------------------------------------------
 OWNER                                                                                                                                                                                  VARCHAR2(120)
 CONSTRAINT_NAME                                                                                                                                                               NOT NULL VARCHAR2(30)
 CONSTRAINT_TYPE                                                                                                                                                                        VARCHAR2(1)
 TABLE_NAME                                                                                                                                                                    NOT NULL VARCHAR2(30)
 SEARCH_CONDITION                                                                                                                                                                       LONG
 R_OWNER                                                                                                                                                                                VARCHAR2(120)
 R_CONSTRAINT_NAME                                                                                                                                                                      VARCHAR2(30)
 DELETE_RULE                                                                                                                                                                            VARCHAR2(9)
 STATUS                                                                                                                                                                                 VARCHAR2(8)
 DEFERRABLE                                                                                                                                                                             VARCHAR2(14)
 DEFERRED                                                                                                                                                                               VARCHAR2(9)
 VALIDATED                                                                                                                                                                              VARCHAR2(13)
 GENERATED                                                                                                                                                                              VARCHAR2(14)
 BAD                                                                                                                                                                                    VARCHAR2(3)
 RELY                                                                                                                                                                                   VARCHAR2(4)
 LAST_CHANGE                                                                                                                                                                            DATE
 INDEX_OWNER                                                                                                                                                                            VARCHAR2(30)
 INDEX_NAME                                                                                                                                                                             VARCHAR2(30)
 INVALID                                                                                                                                                                                VARCHAR2(7)
 VIEW_RELATED                                                                                                                                                                           VARCHAR2(14)




SQL> select OWNER,CONSTRAINT_NAME,CONSTRAINT_TYPE,TABLE_NAME
  2  from user_constraints;

OWNER
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
CONSTRAINT_NAME                                              CO TABLE_NAME
------------------------------------------------------------ -- ------------------------------------------------------------
SCOTT
SYS_C006999                                                  C  CUSTOMER

SCOTT
SYS_C007000                                                  P  CUSTOMER

SCOTT
SYS_C007001                                                  C  PRODUCT

SCOTT
SYS_C007002                                                  P  PRODUCT

SCOTT
SYS_C007003                                                  C  FACTORY

SCOTT
SYS_C007004                                                  P  FACTORY

SCOTT
SYS_C007005                                                  C  STORE

SCOTT
SYS_C007006                                                  P  STORE

SCOTT
SYS_C007007                                                  P  EMP

SCOTT
SYS_C007008                                                  C  MEMBER

SCOTT
SYS_C007009                                                  P  MEMBER


11 rows selected.
```

c not null / p primary key



Unique 제약조건 추가

```sql
SQL> alter table member
  2  add constraint mem_ssn_uni unique(ssn);

Table altered.

SQL> select OWNER,CONSTRAINT_NAME,CONSTRAINT_TYPE,TABLE_NAME
  2  from user_constraints;

OWNER
-----------------------------------------------------------------------------------------------------------------------------------
CONSTRAINT_NAME                                              CO TABLE_NAME
------------------------------------------------------------ -- ------------------------------------------------------------
SCOTT
SYS_C006999                                                  C  CUSTOMER

SCOTT
SYS_C007000                                                  P  CUSTOMER

SCOTT
SYS_C007001                                                  C  PRODUCT

SCOTT
SYS_C007002                                                  P  PRODUCT

SCOTT
SYS_C007003                                                  C  FACTORY

SCOTT
SYS_C007004                                                  P  FACTORY

SCOTT
SYS_C007005                                                  C  STORE

SCOTT
SYS_C007006                                                  P  STORE

SCOTT
SYS_C007007                                                  P  EMP

SCOTT
SYS_C007008                                                  C  MEMBER

SCOTT
SYS_C007009                                                  P  MEMBER

SCOTT
MEM_SSN_UNI                                                  U  MEMBER


12 rows selected.

SQL> insert into member(id, name, ssn) values('jang','장동건',12345);

SQL> insert into member(id, name, ssn) values('jang1','장동건',12345);
insert into member(id, name, ssn) values('jang1','장동건',12345)
*
ERROR at line 1:
ORA-00001: unique constraint (SCOTT.MEM_SSN_UNI) violated
```



foreign key 제약조건 추가

```sql
SQL> alter table member
  2  add constraint mem_dcode_fk foreign key(deptcode)
  3                 references mydept(code);

Table altered.

SQL> select OWNER,CONSTRAINT_NAME,CONSTRAINT_TYPE,TABLE_NAME
  2  from user_constraints;

OWNER
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
CONSTRAINT_NAME                                              CO TABLE_NAME
------------------------------------------------------------ -- ------------------------------------------------------------
SCOTT
SYS_C006999                                                  C  CUSTOMER

SCOTT
SYS_C007000                                                  P  CUSTOMER

SCOTT
SYS_C007001                                                  C  PRODUCT

SCOTT
SYS_C007002                                                  P  PRODUCT

SCOTT
SYS_C007003                                                  C  FACTORY

SCOTT
SYS_C007004                                                  P  FACTORY

SCOTT
SYS_C007005                                                  C  STORE

SCOTT
SYS_C007006                                                  P  STORE

SCOTT
SYS_C007007                                                  P  EMP

SCOTT
SYS_C007008                                                  C  MEMBER

SCOTT
SYS_C007009                                                  P  MEMBER

SCOTT
MEM_SSN_UNI                                                  U  MEMBER

SCOTT
SYS_C007011                                                  P  MYDEPT

SCOTT
MEM_DCODE_FK                                                 R  MEMBER


14 rows selected.

```



rollback은 dml에 적용



참조 테이블 관계

```sql
SQL> insert into member(id,name,ssn,deptcode) values('lee','이민호','54321','001');

1 row created.

SQL> insert into member(id,name,ssn,deptcode) values('lee2','이민호','543210','003');
insert into member(id,name,ssn,deptcode) values('lee2','이민호','543210','003')
*
ERROR at line 1:
ORA-02291: integrity constraint (SCOTT.MEM_DCODE_FK) violated - parent key not found


SQL> drop table mydept;
drop table mydept
           *
ERROR at line 1:
ORA-02449: unique/primary keys in table referenced by foreign keys
```



check 조건 추가

```sql
SQL> alter table member
  2  add constraint member_ck check(addr in ('인천','서울','경기'))
  3  ;

Table altered.

SQL> insert into member(id,name,addr) values('kang','강감찬','인천');

1 row created.

SQL> insert into member(id,name,addr) values('kang2','강감찬2','부산');
insert into member(id,name,addr) values('kang2','강감찬2','부산')
*
ERROR at line 1:
ORA-02290: check constraint (SCOTT.MEMBER_CK) violated

```



제약조건 제거

```sql
SQL> alter table member
  2  drop constraint MEMBER_CK;

Table altered.
```



not null은 컬럼 정의시 주는것이 일반적 null x

unique 유일한 값만 들어가도록 하고 싶을 때 사용합니다. 즉, 중복이 허용되지 않도록 데이터를 넣어야하는 경우 사용

check 내가 지정한 값만 와야됨(입력될 수 있는 데이터의 종류를 제한)

primary key 기본키입니다. 기본키란 해당 테이블을 대표하는 컬럼으로 Primary key로 지정된 컬럼은 Null값을 가지지 못하며, 중복된 값을 가질 수 없습니다.  UNIQUE와 NOT NULL을 동시에 정의한 것

foreign key 외래키로 지정된 컬럼은 참조관계를 가진 테이블의 기본키에 있는 값만을 가질 수 있습니다.

즉, Null 값은 허용하되, 참조하고 있는 테이블의 기본키에 있는 값만 입력될 수 있습니다.





sequence 

시퀀스란 자동으로 순차적으로 증가하는 순번을 반환하는 데이터베이스 객체, 보통 PK값에 중복값을 방지하기위해 사용

```sql
SQL> create table myorder(
  2         ord_num varchar2(10) primary key,
  3         id varchar2(20));

Table created.

SQL> create table order_detail(
  2          ord_num varchar2(10),
  3          prd_num varchar2(20));

Table created.

SQL> create sequence myorder_seq;

Sequence created.

SQL> insert into myorder values(myorder_seq.nextval,'jang');

1 row created.

SQL> insert into order_detail values(myorder_seq.currval,'prd001');

1 row created.

SQL> insert into order_detail values(myorder_seq.currval,'prd002');

1 row created.

SQL> insert into order_detail values(myorder_seq.currval,'prd003');

1 row created.

SQL> select * from myorder;

ORD_NUM              ID
-------------------- ----------------------------------------
1                    jang

SQL> select * from order_detail;

ORD_NUM              PRD_NUM
-------------------- ----------------------------------------
1                    prd001
1                    prd002
1                    prd003

SQL> insert into myorder values(myorder_seq.nextval,'jang');

1 row created.

SQL> insert into myorder values(myorder_seq.nextval,'jang');

1 row created.

SQL> insert into myorder values(myorder_seq.nextval,'jang');

1 row created.

SQL> select * from myorder;

ORD_NUM              ID
-------------------- ----------------------------------------
1                    jang
2                    jang
3                    jang
4                    jang

SQL> select myorder_seq.currval from dual;

   CURRVAL
----------
         4
   
//시퀀스 삭제
SQL> drop sequence myorder_seq;

Sequence dropped.
```

