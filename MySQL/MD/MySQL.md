# MySQL

## SQL

### Structured Query Language 의 약자이다

-   **Structured** : 표를 작성하여 정리정돈(구조화) 시키는 것
-   **Query** : 질의(DB에게 명령하는 것)
-   **Language** : 언어



## MySQL의 구조

### Table

-   MySQL이나 다른 관계형 데이터베이스(Relational DB) 들은 데이터를 테이블의 형태로 관리하게 된다. 따라서 Table이란 DB의 가장 마지막 계층이다.

### Schema

-   데이터베이스의 구조와 제약 조건을 정의한 것이다. 쉽게는 폴더에 해당하며 스키마도 폴더처럼 사용자가 자유롭게 만들 수 있고, 사용자에 따라 접근을 제한하는 등의 권한 관리가 가능하다. 또한, 폴더이기 때문에 여러 테이블을 담을 수 있다.
-   MySQL의 2번째 계층이다.

### Instance

-   DBMS가 동작할 때의 단위, OS의 입장에선 프로세스이다. DBMS에 따라선 서버 프로세스, 혹은 서버로 부르기도 한다.  MySQL에선 Oracle과 달리 3계층 구조로, Instance - DB - Schema - Table 구족 아닌, Instance - Schema - Table 구조이다.





## 문법

### Table 만들기

``` mysql
CREATE TABLE tableName(
	columnName Type NullAble ...)
	
ex)
CREATE TABLE topic(
	id INT(11) NOT NULL AUTO_INCREMENT, //값이 자동으로 1씩 증가
	title VARCHAR(100) NOT NULL,
	description TEXT NULL,
	created DEATETIME NOT NULL,
	author VARCHAR(30) NULL,
	profile VARCHAR(100) NULL,
	PRIMARY KEY(id);) // map의 id같은 느낌
```



### Table에 데이터 삽입

``` mysql
INSERT INTO tableName (colums...) VALUES(// 순서에 맞게 입력);

ex)
INSERT INTO topic (title, description, created, author, profile) VALUES('MySQL','MySQL is ...', NOW(), 'egoing','developer');
```



### Table Read

``` mysql
SELECT * FROM TableName; // TableName 테이블의 모든 데이터 출력
SELECT columns FROM TableName; // TableName의 columns에 해당하는 데이터만 출력
SELECT columns FROM TAbleName WHERE column=value; // TableName의 Columns에 해당하면서 column = value 를 만족하는 행만 출력(rows); 
SELECT columns TableName WHERE column=value ORDER BY A asc or desc // 위에 해당하는 값을 A를 기준으로 내림차순 or 오름차순 정렬
SELECT columns TableName WHERE column=value ORDER BY A asc or desc LIMIT 2; // 위에서 해당하는 값중 2개만 출력
```



### Table Update

``` mysql
UPDATE TableName SET 바꿀 정보 WHERE 바꿀 곳;

ex)
UPDATE topic SET description='MySQL is ...', title='MySQL' WHERE id=2;
```



### Table Delete

``` mysql
DELETE FROM TableName WHERE 삭제할 곳; 
```



### DATABASE (SCHEMA)  만들기

``` mysql
CREATE DATABASE DBName; // 생성
DROP DATABASE DBName; // 삭제
SHOW DATABASES; // DB들 출력
USE DBNAme; // 해당 DB를 사용
```



### JOIN

``` mysql
SELECT TableName.Column AS 테이블에 표시될 이름,columns, FROM TableName LEFT JOIN TableName ON A테이블.행 = B테이블.행;
```

