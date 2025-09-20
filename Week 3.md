# SQL_MASTER 3주차 정규 과제 

## Week 3 : SQL 기본 문법

📌**SQL_MASTER 정규과제**는 매주 MySQL Workbench 툴을 활용하여 **직접 데이터베이스를 설계하고 실습하는 프로젝트 기반 과제**입니다. 

이번 주는 아래의 **SQL_MASTER_3rd_TIL**에 나열된 주제를 중심으로 개념을 학습하고, 주차별 **학습 목표**에 맞게 정리해주세요. 정리한 내용은 GitHub에 업로드한 후, **스프레드시트의 'SQL' 시트에 링크를 제출**해주세요. 



> ✅ **과제 제출 시 반드시 “Workbench 실습 화면 (캡처)” 를 첨부해주세요!**
>
> - 테이블 생성, 수정, 삭제 명령이 실행된 화면 또는 결과가 확인되는 캡처를 첨부합니다.
> - Github에 정리하는 실습 TIL 링크를 **스프레드시트 'SQL_MASTER' 시트에 제출**해주세요.



<!-- 이번 주차는 SELECT 구문에 대한 복습입니다. 개념 정리는 책을 읽으면서 평소 잘 못 알고 있거나 헷갈리는 개념을 위주로 정리해주세요. -->

> **이번 주차는 SELECT 구문의 복습으로 프로그래머스에서 한 문제를 풀어야합니다. 문제를 풀고, 정답 인증을 해주세요**



## SQL_MASTER_3rd_TIL

## 3장. SQL 기본 문법

### 01. 기본 중에 기본 SELECT ~FROM ~WHERE

### 02. 좀 더 깊게 알아보는 SELECT 문

### 03. 데이터 변경을 위한 SQL 문



## 4장. SQL 고급 문법

### 01. MySQL의 데이터 형식 

### 02. 두 테이블을 묶는 조인

### 03. SQL 프로그래밍



## 🏁 주차별 학습 (Study Schedule)

| 주차  | 공부 범위                  | 완료 여부 |
| ----- | -------------------------- | --------- |
| 1주차 | **데이터베이스와 SQL**     | ✅         |
| 2주차 | **실전용 SQL 미리 맛보기** | ✅         |
| 3주차 | **기본, 고급 DML 복습**    | ✅         |
| 4주차 | **테이블과 뷰**            | 🍽️         |
| 5주차 | **인덱스**                 | 🍽️         |
| 6주차 | **스토어드 프로시져**      | 🍽️         |
| 7주차 | **SQL 파이썬 연결하기**    | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 개념정리

## 01. SQL 기본 문법

~~~
✅ 학습 목표 :
* 테이블에서 데이터를 추출하는 SELECT 문을 완벽히 이해할 수 있다.
* 여러 건의 데이터를 그룹으로 묶는 방법을 능숙하게 사용할 수 있다.
* 데이터를 입력, 수정, 삭제 하는 방법을 익히고 활용할 수 있다. 
~~~

LIKE '%'-무엇이든 '_'-한글
IN('A','B','C')
BETWEEN 1 AND 3
LIMIT 시작, 개수


AUTO_INCREMENT: 자동으로 숫자를 입력해준다는 의미
ex)
CREATE TABLE TB1 (
COL1 INT AUTO_INCREMENT NOT NULL PRIMARY KEY,
~~)

-SELECT LAST_INSERT_ID(); -- 자동 증가로 입력된 마지막 숫자
-ALTER TABLE TB1 AUTO_INCREMENT=100; -- 자동 증가로 입력되는 다음 값을 100으로 설정
-SET @@auto_increment_increment = 3; -- 자동 증가 시 증가되는 


INSERT INTO TB1 [(COL1, COL2, ...)] VALUES (VAL1, VAL2,...)
INSERT INTO TB1 VALUES (VAL1, VAL2,...) (VAL1, VAL2, ...) (VAL1, VAL2, ...) ~~

INSERT INTO TB1
  SELECT COL1, COL2 FROM TB2; -- TB2의 데이터를 한번에 TB1에 입력

  
DESC TB1; -- Describe의 약자로 테이블 구조를 출력

UPDATE TB1
  SET COL1 = VAL1 -- WHERE 문이 없을 경우, 모든 행의 값 변경


대용량 테이블 삭제 방법
1) DELETE FROM TB1: 빈 테이블을 남김, 오래 걸림
2) TRUNCATE TABLE TB1: 빈테이블을 남김, 빠름
3) DROP TABLE TB1: 테이블 자체를 삭제, 빠름


## 02. SQL 고급 문법

~~~
✅ 학습 목표 :
* 다양한 데이터 형식에 대해 이해할 수 있다.
* 두 테이블을 연결하는 조인을 이해하고 활용할 수 있다.
* SQL에서 일반 프로그래밍 기능을 구현할 수 있다. 
~~~

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->



<br>

---

# 2️⃣ 확인문제

## 문제 1

> **🧚다음 쿼리는 조건에 따라 다른 결과를 출력하는 구문입니다. 아래 빈칸에 들어갈 적절한 SQL 키워드를 채우세요.**

~~~sql
SELECT member_id, name,
       ( ______
           ______ join_date IS NULL ______ '미가입',
           ______ join_date IS NOT NULL ______ '가입완료'
       ______ ) AS join_status
FROM Member
______ name;
~~~

> **또한, 이 쿼리는 무엇을 하기 위해 작성된 것인지도 간단히 작성해주시면 됩니다.**



~~~
순서대로 CASE, WHEM, THEN, WHEN, THEN, END, ORDER BY

Member 테이블로부터
join_date가 null 값일 경우 '미가입'으로, null 값이 아닐 경우 '가입완료'로 표시하는 join_status 열과
member_id, name 열을
name열에 따라 정렬하여 조회하는 쿼리이다.
~~~



---

# 3️⃣ 실습 문제

https://school.programmers.co.kr/learn/courses/30/lessons/131534

> 프로그래머스 : 상품을 구매한 회원 비율 구하기 (Lv 5)

<!-- 이 주석을 지우고 문제의 코드와 코드에 대한 설명과 '정답입니다' 문구를 캡쳐해서 올려주세요 -->



# 참고자료

**이번 주차에서는 강의에서 05, 06, 07편을 보면서 관계를 연결하는 방법을 워크벤치에서는 어떻게 하는지 미리 예습하는 느낌으로 시청해주시면 됩니다.**



[참고 외부자료는 여기를 클릭해주세요.](https://www.youtube.com/playlist?list=PL_RECGqDS3ieZFybjCx0kTYkPK-TioY1S)

<br>

### 🎉 수고하셨습니다.
