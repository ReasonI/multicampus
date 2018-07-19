# jkkk
## hjh
#### 오ㅗ아ㅗ아ㅗ와아ㅘ
~~~java
system.out
~~~
~~~sql
select * from tab;

--table create
create table 테이블명 (필드명 자료형, 필드명 자료형(크기), ... );
create table test(
    no number,
    name varchar2(10)
);

select * from test; -- test table 목록 보기

desc test; -- 테이블 구조 보기

-- 레코드 추가하기
insert into 테이블명 values(값1, '값2, ... ');

insert into test values(1, 'yuna');
insert into test values(2, 'yuna');
insert into test values(1, 'lee');

select sysdate from dual;

---------------------------------------------------------
create table test2(
    no number,
    name varchar2(10) not null-- not null 제약조건 줌
);

insert into test(name) values(100);
insert into test2(name) values(200);
insert into test2 values(1, 'lee');

select * from test2; -- test table 목록 보기

--제약조건
create table userlist (
    id varchar2(10) constraint id_pk primary key, --기본키 >> 중복 허용X
    name varchar2(10) not null
    );

insert into userlist values('aa', 'yuna');
insert into userlist values('bb', 'bb');
insert into userlist values('cc', 'yuna');
insert into userlist values('aa', 'lee');

select * from userlist;

select * from emp2; --전체보기
select empno, name from emp2; -- 원하는 필드만 보기

--생일, 부서번호, 타입, 직위

select birthday, deptno, emp_type, position from emp2;

--필드명 변경해서 보여주기
select birthday as 생년월일, deptno "부서 번호", emp_type 타입, position "직위" from emp2; --화면상에서 출력만 이렇게 해주고 database에서는
바뀌지 않음

select * from dept2;

select dcode as 부번, dname "부  서  명", area "위    치" from dept2;

select * from student;

select grade from student;
select distinct grade from student; -- distinct 사용시 중복된 값 제거하고 보여줌

select distinct area, dcode from dept2;

select * from professor;

select *
from professor
where position = '정교수';

select name, profno, email
from professor
where position = '정교수';

select *
from professor
where position = '정교수' and id = 'simson';

select *
from professor
where deptno = '101';

select profno, id, hiredate, name, pay
from professor
--where deptno = 101;
--where deptno = 101 or pay >= 550;
where deptno = 101 and pay < 400;

select name, id
from professor
order by name; --이름을 기준으로 정렬한 채로 출력 >> asc(기본) : 오름차순, desc : 내림차순

select name, id
from professor
order by name asc, id desc;

select name, id
from professor
where deptno = 101
order by name desc;

select name, id
from professor
where name = '심슨'; -- % : 모든을 의미한다. _ : 한문자를 나타냄 <== 단독으로 쓰이지 못하고 like연산자와 같이 쓰인다.

select name, id
from professor
where name like '%희%';

select name, id
from professor
where name like '_현%';

select name, id
from professor
where name like '__';

--------------------------------------
--문제1) 이름에서 '김영조' 사람들을 보여주세여
select *
from professor
where name = '김영조';

--문제2) 이름에서 '김'씨 성을 가진 사람들을 보여주세여
select *
from professor
where name like '김%';

--문제3) 이름에서 두글자인 사람 보여주세여
select *
from professor
where name like '__';

--문제4) id에 s or a 글자가 들어가는 사람 찾기
select *
from professor
where id like '%s%' or id like '%a%';

--문제5) 전임강사 찾기
select *
from professor
where name like '%승%'

--문제6) multi table 생성하기 -필드는 name, age, address 필드 갖는...(자료형은 자유)
create table multi_table(
name varchar2(20),
age number,
address varchar2(10)
);

--문제7) multi table에 레코드 3개이상 넣기
insert into multi_table values('유나유나', 22, '경기');
insert into multi_table values('유나', 24, '서울');
insert into multi_table(age, address) values(22, '경기');

--확인~~ select * from multi_table;

--1. SELECT 문장 사용하기 1장 p13~ 실습해보기 (테이블은 적정하게 적용, 필드도...)
create table icecream(
name varchar2(10),
price number,
manufacturer varchar2(10)
);

insert into icecream values('메로나', 1000,'ㅎㅌ');
insert into icecream values('와크와', 2000,'ㅎㅌ');
insert into icecream values('쌍쌍바', 1000,'ㅎㅌ');
insert into icecream values('돼지바', 1000,'ㅎㅌ');
insert into icecream values('부라보', 1500,'ㅎㅌ');
insert into icecream values('월드콘', 1500,'오리온');
insert into icecream values('생귤탱', 1000,'오리온');
insert into icecream values('옥동자', 1000,'오리온');
insert into icecream values('팽이팽', 5000,'오리온');
insert into icecream values('위즐', 5000,'롯데');
insert into icecream values('바밤바', 1000,'롯데');
insert into icecream values('설레임', 1500,'롯데');
insert into icecream values('와', 2000,'롯데');

select distinct price, name, manufacturer
from icecream;

select distinct name, manufacturer
from icecream;

select * from icecream;
delete icecream where name = '생귤탱';

select * from icecream
where

~~~
