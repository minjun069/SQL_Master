# SQL_MASTER 4주차 정규 과제 

## Week 4 : 테이블과 뷰

📌**SQL_MASTER 정규과제**는 매주 MySQL Workbench 툴을 활용하여 **직접 데이터베이스를 설계하고 실습하는 프로젝트 기반 과제**입니다. 

이번 주는 아래의 **SQL_MASTER_4th_TIL**에 나열된 주제를 중심으로 개념을 학습하고, 주차별 **학습 목표**에 맞게 정리해주세요. 정리한 내용은 GitHub에 업로드한 후, **스프레드시트의 'SQL' 시트에 링크를 제출**해주세요. 



> ✅ **과제 제출 시 반드시 “Workbench 실습 화면 (캡처)” 를 첨부해주세요!**
>
> - 테이블 생성, 수정, 삭제 명령이 실행된 화면 또는 결과가 확인되는 캡처를 첨부합니다.
> - Github에 정리하는 실습 TIL 링크를 **스프레드시트 'SQL_MASTER' 시트에 제출**해주세요.





## SQL_MASTER_4th_TIL

## 5장. 테이블과 뷰 

### 01. 테이블 만들기 

### 02. 제약조건으로 테이블을 견고하게 

### 03. 가상의 테이블 뷰





## 🏁 주차별 학습 (Study Schedule)

| 주차  | 공부 범위                  | 완료 여부 |
| ----- | -------------------------- | --------- |
| 1주차 | **데이터베이스와 SQL**     | ✅         |
| 2주차 | **실전용 SQL 미리 맛보기** | ✅         |
| 3주차 | **기본, 고급 DML 복습**    | ✅         |
| 4주차 | **테이블과 뷰**            | ✅         |
| 5주차 | **인덱스**                 | 🍽️         |
| 6주차 | **스토어드 프로시져**      | 🍽️         |
| 7주차 | **SQL 파이썬 연결하기**    | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 개념정리

## 01. 테이블과 뷰

~~~
✅ 학습 목표 :
* 테이블의 구조에 대해 완벽하게 이해할 수 있다. 
* 테이블의 핵심인 제약조건을 학습하고 적절하게 지정할 수 있다.
* 뷰의 개념과 실제 작동하는 방법에 대해 이해할 수 있다. 
~~~

<img width="954" height="418" alt="image" src="https://github.com/user-attachments/assets/addac27c-03ee-4209-889d-b59ef79c44a4" />

<img width="870" height="331" alt="image" src="https://github.com/user-attachments/assets/aca48916-5eeb-4e57-bee0-3e13adc0974f" />

<img width="896" height="136" alt="image" src="https://github.com/user-attachments/assets/d81ac7ae-87c7-41fa-bc4d-a4a315653699" />

대표적인 제약조건들  
<img width="366" height="406" alt="image" src="https://github.com/user-attachments/assets/391635a2-bc45-4db4-ae6f-fcdcd8307e9b" />

<img width="1170" height="302" alt="image" src="https://github.com/user-attachments/assets/bafee688-7aeb-43af-a172-e4e0e9ca3462" />

-외래키  
<img width="600" height="190" alt="image" src="https://github.com/user-attachments/assets/79c5b6c1-ad9a-469a-b32c-34fa0b8dc3d8" />

<img width="674" height="228" alt="image" src="https://github.com/user-attachments/assets/cace6acc-89ea-458f-9d81-620a1c7e55a5" />  
기존 테이블의 데이터 수정, 삭제에 대응

-Check
<img width="774" height="40" alt="image" src="https://github.com/user-attachments/assets/f37dcaa2-64c3-42f8-a5ca-186ae8c3437d" />

<img width="924" height="136" alt="image" src="https://github.com/user-attachments/assets/b3b3a265-b1bb-4e1e-8f0e-030d6532416e" />

-Default  
<img width="614" height="40" alt="image" src="https://github.com/user-attachments/assets/67039498-9c7b-4f50-9417-430ba01205f0" />

<img width="592" height="90" alt="image" src="https://github.com/user-attachments/assets/1083342f-aadf-456f-a757-0e3a84682d4c" />

뷰  
<img width="676" height="190" alt="image" src="https://github.com/user-attachments/assets/bd281cea-733a-4a3b-91bd-ff68fc056e53" />

뷰 사용 시 장점: 보안 & 쿼리 단순화  

뷰 생성/수정/삭제: CREATE/ALTER/DROP VIEW 뷰_이름  
*CREATE OR REPLACE VIEW 뷰_이름: 기존에 뷰가 있어도 덮어쓰기 가능  
*SHOW CREATE VIEW 뷰_이름: 소스 코드 확인  

뷰를 통해 데이터 수정/삭제 가능,  
데이터 삽입 시에는 뷰가 참조하지 않는 원본 테이블의 컬럼 속성에 따라 안 될 수 있음  

-뷰의 조건을 만족하지 않는 데이터는 입력되지 않도록 옵션 지정  
<img width="630" height="184" alt="image" src="https://github.com/user-attachments/assets/91a29fe0-b537-4ca3-a4ae-f3111122b351" />

복합 뷰: 두 개 이상의 테이블로 만든 뷰. 읽기 전용(데이터 입력/수정/삭제 불가능).

*뷰가 참조하는 테이블 삭제 시, 뷰 조회 불가


<br>

---

# 2️⃣ 확인문제 & 추가학습

## 문제 1

> **🧚 온라인 쇼핑몰 DB를 설계하려 한다. 아래 스키마와 요구사항을 만족해야 한다.**
>
> - CATEGORY(CAT_ID, CAT_NAME)
> - PRODUCT(PROD_ID, PROD_NAME, PRICE, CAT_ID, STATUS)
> - 제약조건 요구:
>   1. CATEGORY.CAT_ID는 기본키
>   2. PRODUCT.PROD_ID는 기본키, PROD_NAME은 NULL 불가
>   3. PRODUCT.CAT_ID는 존재하는 카테고리만 허용(삭제 시 자식은 NULL 처리)
>   4. PRODUCT.PRICE는 0 이상
>   5. PRODUCT.STATUS는 'ACTIVE' 또는 'INACTIVE'만 허용
> - 운영팀 전용 뷰 V_ACTIVE_PRODUCT는 **활성 상품만** 조회하며, 뷰를 통해 INSERT/UPDATE 시에도 활성 상태만 들어오도록 강제해야 한다.
>
> **아래 보기 중 옳은 것을 모두 고르시오**

~~~sql
A. 
CREATE TABLE CATEGORY (
  CAT_ID   NUMBER      PRIMARY KEY,
  CAT_NAME VARCHAR(50) UNIQUE
);

B. 
CREATE TABLE PRODUCT (
  PROD_ID   NUMBER       PRIMARY KEY,
  PROD_NAME VARCHAR(100) NOT NULL,
  PRICE     NUMBER       CHECK (PRICE >= 0),
  CAT_ID    NUMBER,
  STATUS    VARCHAR(10)  CHECK (STATUS IN ('ACTIVE','INACTIVE')),
  CONSTRAINT FK_PROD_CAT
    FOREIGN KEY (CAT_ID) REFERENCES CATEGORY(CAT_ID)
      ON DELETE SET NULL
);

C. 
ALTER TABLE PRODUCT
  ADD CONSTRAINT UQ_PROD_NAME UNIQUE (PROD_NAME);
  
D. 
CREATE VIEW V_ACTIVE_PRODUCT AS
SELECT PROD_ID, PROD_NAME, PRICE, CAT_ID, STATUS
FROM PRODUCT
WHERE STATUS = 'ACTIVE'
WITH CHECK OPTION;

E. 정답은 없다. 왜냐하면 V_ACTIVE_PRODUCT는 집계가 없기 때문에 반드시 업데이트 불가능한 비갱신 뷰이다. 
~~~

A, B, D  
C는 PRODUCT 테이블의 PROD_NAME 열에 고유한 값들만 입력되도록 UNIQUE 제약 조건을 추가하는 쿼리이다.  
해당 요구는 본문에 없다.

E: VIEW는 원본 테이블 변경에 따라 갱신된다. 따라서 틀린 설명이다.



## 추가학습 : 정규화

> **🧚. 다음 아래의 키워드를 참고하여 데이터 베이스의 정규화에 대한 개념을 더 공부하고 난 이후, 아래에 공부한 내용을 자유롭게 정리해주세요.**

~~~
데이터베이스 정규화
1NF: 모든 속성은 단일한 값을 갖고 여러 값을 가질 수 없다.
2NF: 1NF + 부분 함수 종속 제거 (부분 함수 종속: 기본키가 복합키일 때, 기본키 전체가 아닌 일부만으로도 특정 속성이 결정되는 경우)
3NF: 2NF + 이행적 함수 종속 제거 (이행적 함수 종속: A → B, B → C이면 A → C가 성립하는 경우)
BCNF: 결정자(다른 속성의 값을 결정하는 것이 가능한 속성)가 존재할 때, 그 결정자가 반드시 후보키여야 하는 상태.
4NF: BCNF + 다치 종속 제거 (다치 종속: 키 하나가 여러 독립적인 다중값 속성을 
5NF: 4NF + 조인 종속 제

*키
-슈퍼키: 테이블의 각 행을 유일하게 식별할 수 있는 속성들의 집합.
-후보키: 슈퍼키 중 불필요한 속성을 뺄 수 없는 최소키 (최소성: 불필요한 속성을 더는 뺄 수 없는 상태)
-기본키: 후보키 중 하나를 선택한 것. 실제로 사용하는 대표.
-대체키: 기본키로 선택되지 않은 나머지 후보키.
-외래키: 다른 테이블의 기본키를 참조하는 키. 데이터 무결성 보장을 위해 사용.

~~~



<br>

### 🎉 수고하셨습니다.
