---
title: 'SQL(MySQL)'
date: 2020-6-24 23:50:43
category: 'etc'
---

> ## 시작

개발인생(말만 번지르하지만 사실 2년 정도..ㅎㅎ) 전부에서 NoSQL만 공부하고 접하며 사용했다. SQL에 대해서도 조금씩 관심을 가졌었지만 최근에 들어서 직접적으로 사용하게될 상황이 생겼다. MySQL은 오픈 소스의 관계형 데이터베이스 시스템(Relational DBMS)이다. 기본적으로 구성되는 개념은 테이블, 스키마, 데이터 베이스, 데이터베이스 서버, 관계형 데이터베이스, SQL, 쿼리가 있다.

> ## 기본적인 SQL 문법

### 1. Create

```sql
INSERT INTO 테이블명 (컬럼들) VALUES(컬럼 차례대로 맞는 값);
```

### 2. Read

```sql
SELECT * FROM (스키마명.)테이블명;
SELECT (보고싶은) 컬럼 FROM (스키마명.)테이블명;
SELECT (보고싶은) 컬럼 FROM (스키마명.)테이블명 WHERE 컬럼='원하는 값';
```

### 3. Update

```sql
UPDATE 테이블명 SET 컬럼='변경 값' WHERE 컬럼=값;
// EX)
UPDATE smartlogin SET default_member_icon=새로운 이미지 주소값 WHERE consumer_seq=27;
```

### 4. Delete

```sql
DELETE FROM 테이블명 WHERE 컬럼=값;
```

### 5. Count

```sql
SELECT COUNT(*) FROM 테이블명 WHERE 컬럼=찾고 싶은 값 LIMIT 0, 제한할 숫자;
```

### 6. Like & Not Like

```sql
SELECT COUNT(*) FROM 테이블명 WHERE 컬럼=찾고 싶은 값;

SELECT * FROM 테이블명 WHERE 컬럼 LIKE '';
SELECT * FROM 테이블명 WHERE 컬럼 LIKE '' AND 테이블명 NOT LIKE '';
```

```sql
'-' : 글자숫자를 정해줌(EX 컬럼명 LIKE '홍_동')
'%' : 글자숫자를 정해주지않음(EX 컬럼명 LIKE '홍%')

--A로 시작하는 문자를 찾기--
SELECT 컬럼명 FROM 테이블 WHERE 컬럼명 LIKE 'A%'

--A로 끝나는 문자 찾기--
SELECT 컬럼명 FROM 테이블 WHERE 컬럼명 LIKE '%A'

--A를 포함하는 문자 찾기--
SELECT 컬럼명 FROM 테이블 WHERE 컬럼명 LIKE '%A%'

--A로 시작하는 두글자 문자 찾기--
SELECT 컬럼명 FROM 테이블 WHERE 컬럼명 LIKE 'A_'

--첫번째 문자가 'A''가 아닌 모든 문자열 찾기--
SELECT 컬럼명 FROM 테이블 WHERE 컬럼명 LIKE'[^A]'

--첫번째 문자가 'A'또는'B'또는'C'인 문자열 찾기--
SELECT 컬럼명 FROM 테이블 WHERE 컬럼명 LIKE '[ABC]'
SELECT 컬럼명 FROM 테이블 WHERE 컬럼명 LIKE '[A-C]'
```
