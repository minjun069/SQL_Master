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

LIKE '%'-무엇이든 '_'-한글자    
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

● 데이터 형식  
-정수형  
<img width="590" height="194" alt="image" src="https://github.com/user-attachments/assets/16893d6b-34ad-4367-8dd0-da8d135330d5" />

-문자형  
<img width="886" height="116" alt="image" src="https://github.com/user-attachments/assets/b6db250e-7bd4-45c0-9b40-c7e16bb6ae1c" />   
<img width="886" height="150" alt="image" src="https://github.com/user-attachments/assets/81102318-bc71-4926-9d3d-f3351795cf34" />   
TEXT 형식은 긴 스크립트를, BLOB는 사진이나 동영상을 저장할 때 사용

-실수형   
<img width="890" height="106" alt="image" src="https://github.com/user-attachments/assets/98f34c7e-65d6-40f8-8b5d-ed3398dad299" />

-날짜형   
<img width="894" height="158" alt="image" src="https://github.com/user-attachments/assets/416d418a-b314-471c-9bc4-7c0083c8caf3" />


● 데이터 형 변환   
-명시적 변환   
<img width="384" height="80" alt="image" src="https://github.com/user-attachments/assets/e83dec36-e61d-43aa-9576-bd0befc8d779" />

-암묵적 변환   
<img width="810" height="82" alt="image" src="https://github.com/user-attachments/assets/e9b2cbd7-a282-43b4-a476-35f5c2b4481d" />   
연산 시 시스템 내에서 자동으로 변환 후 연산하는 경우 

● 변수 사용   
<img width="554" height="88" alt="image" src="https://github.com/user-attachments/assets/f4e11890-1c04-4cff-8255-52f814b00352" />   
변수 사용시 MYSQL 종료하면 재사용할 수 없음

<img width="818" height="110" alt="image" src="https://github.com/user-attachments/assets/4d8b3d1d-e927-450b-931f-15cf50177ea5" />    
LIMIT에는 직접 변수 사용이 안 되지만, PREPARE-EXCUTE 문으로 우회 사용 가능


● 스토어드 프로시저   
코딩 시 SQL문은 두 문장 이상 사용 시 항상 BEGIN ~ END로 묶어준다.

-IF~ELSE문  
<img width="194" height="116" alt="image" src="https://github.com/user-attachments/assets/be10d68c-ea8f-4935-97e6-15b9f4fa6cb6" />

-CASE문   
<img width="234" height="356" alt="image" src="https://github.com/user-attachments/assets/f378412f-c9a8-4930-8257-705afb4f8e5e" />

-WHILE문   
<img width="224" height="104" alt="image" src="https://github.com/user-attachments/assets/f0a73865-5868-48ed-a69d-554dd1fa7be7" />

● 동적 SQL   
-PREPARE & EXCUTE   
사용 예시   
<img width="808" height="194" alt="image" src="https://github.com/user-attachments/assets/4fbc7b65-3e12-42ea-9d97-ad3f618d7c0c" />


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
>
~~~sql
SELECT 
    YEAR(SALES_DATE) AS YEAR, 
    MONTH(SALES_DATE) AS MONTH, 
    COUNT(DISTINCT USER_ID) AS PURCHASED_USERS,
        ROUND(
        COUNT(DISTINCT USER_ID) /
        (SELECT COUNT(DISTINCT USER_ID) 
         FROM USER_INFO 
         WHERE JOINED BETWEEN '2021-01-01' AND '2021-12-31'),
        1
    ) AS PUCHASED_RATIO
    
FROM ONLINE_SALE
WHERE USER_ID IN (
    SELECT USER_ID 
    FROM USER_INFO 
    WHERE JOINED 
    BETWEEN '2021-01-01' AND '2021-12-31'
)
GROUP BY YEAR, MONTH
ORDER BY YEAR, MONTH
~~~


# 참고자료

**이번 주차에서는 강의에서 05, 06, 07편을 보면서 관계를 연결하는 방법을 워크벤치에서는 어떻게 하는지 미리 예습하는 느낌으로 시청해주시면 됩니다.**



[참고 외부자료는 여기를 클릭해주세요.](https://www.youtube.com/playlist?list=PL_RECGqDS3ieZFybjCx0kTYkPK-TioY1S)

<br>

### 🎉 수고하셨습니다.
