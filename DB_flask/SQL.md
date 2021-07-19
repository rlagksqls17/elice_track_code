# SQL  
## SQL이란  
데이터베이스 : 여러 사람이 공유해 사용할 목적으로 통합하여 관리되는 데이터의 모음  
데이터 베이스의 종류에 따라 사용 방법이 조금씩 다르지만 데이터베이스에서 검색과 분석에 사용되는 기본 사용 방법은 데이터베이스 종류와 상관없이 동일  

SQL : **Structured Query Language**  

### 테이블에서 데이터 검색하기  
가장 많이 사용되는 데이터베이스는 관계형과 비관계형이 있음  
**SQL은 관계형 데이터베이스**  
: 하나 이상의 테이블로 이루어지며 서로 연결된 데이터를 가짐  

테이블은 레코드(Record)와 컬럼(Column)으로 구성되어 있음  

**desc**    
테이블의 구조를 확인 가능 (데이터의 타입 또한 확인 가능)  
```sql  
desc employees ; --employees라는 테이블을 확인   
```  

**select**  
: 검색을 위한 명령어  
```sql
SELECT title, author --SELECT + 컬럼  
FROM book;  
--book이라는 테이블에서 title과 author 컬럼을 중심으로 검색  

SELECT *  
FROM book;  
-- 검색할 데이터에 * 을 입력하면 모든 데이터 검색  
```    
: DISTINCT 쓸 시 뒤에 나오는 컬럼의 중복을 제거하고 보여줌  
: DISTINCT 뒤에 2개 이상의 컬럼을 적을 시 한 쪽 컬럼에 중복이 있어도 다른 쪽 컬럼의 값이 다르면 데이터 간 서로 다르게 취급됨   

```sql  
select distinct emp_no 
from salaries ;
```  

**where**     
: 검색하고자 하는 데이터의 조건을 설정할 수 있는 명령  
```sql  
SELECT *
FROM book  
WHERE title = '돈키호테';  -- WHERE + 데이터  
```  
  
### 여러 개의 조건을 추가하기   

- 비교연산자를 사용하여 검색  

```sql  
SELECT * 
FROM score  
WHERE korean >= 90;  -- <, >, >=, <= 사용 가능  
```  

- 복합조건연산자를 사용하여 검색  
```sql  
SELECT *
FROM score  
WHERE korean >= 90 OR math > 80; -- AND, OR, NOT 사용 가능  
```  

```sql  
-- 책들의 정보가 담긴 테이블의 구조를 출력합니다. 수정하실 필요는 없습니다.
DESC book;

-- 해당하는 작가가 쓴 책만 골라서 출력합니다.
SELECT *
FROM book
WHERE author IN ('William Shakespeare', 'John Ronald Reuel Tolkien', 'Joanne Kathleen Rowling');
```  

- 기타 연산자를 사용하여 검색  
BETWEEN : A가 10과 20 사이에 포함된 값 (A BETWEEN 10 and 20)    
IN : B에 A가 포함된 값 (A IN B)  
NOT IN : B에 A가 포함되지 않은 값 (A NOT IN B)  

## 데이터를 제어하는 DML  

DML : 데이터 조작어  
DDL : 데이터 정리어  
DCL : 데이터 제어어  
TCL : 트랜젝션 제어어  

### 테이블에서 유사한 값 찾기  

LIKE : 특정 문자가 포함된 문자열을 찾고 싶을 때 사용하는 명령  

```sql  
SELECT *  
FROM book  
WHERE title LIKE '어린왕자';  -- =이 아니라 LIKE  
```

```sql  
SELECT *  
FROM book  
WHERE title LIKE '%왕자'; -- 왕자로 끝나는 책 검색  
WHERE title LIKE '%린왕%';
```  

### 데이터 정렬하기  

**ORDER BY**  : 데이터를 검색할 때 정렬하여 결과를 출력하는 명령어  

```sql
SELECT *
FROM score
ORDER BY math DESC; -- 내림차순 정렬 조건 (구조 보여주는 DESC 와 다름)
ORDER BY math ASC; -- 오름차순 정렬 조건
```  

### 테이블에 데이터 삽입하기  
INSERT : 관계형 데이터베이스의 테이블에 값을 저장하는 명령  

```sql  
INSERT INTO book(컬럼1, 컬럼2, 컬럼3) --컬럼을 명시하지 않아도 순서대로 값을 삽입
VALUES (컬럼데이터1, 컬럼데이터2, 컬럼데이터3)  
```  

### 테이블의 데이터 수정하기  
UPDATE : 관계형 데이터베이스의 테이블에서 이미 저장된 값을 수정하는 명령  

```sql  
UPDATE book  
SET title = 수정할 값  
WHERE title = 조건  
```  

### 테이블의 데이터 삭제하기  
DELETE : 관계형 데이터베이스의 테이블에서 이미 저장된 값을 **삭제**하는 명령  

```sql  
DELETE  
FROM book
WHERE 조건 --WHERE 조건이 없을 시 모든 데이터 삭제가 됨  
```  

## SQL과 함수  

1. 행 함수 : 데이터 값을 계싼하거나 조작  
2. 그룹 함수 : 행의 그룹을 계산하거나 요약  
3. 열의 데이터 타입을 변환   

**COUNT** : 검색한 결과의 데이터의 개수를 가져오는 내장함수 (NULL 인 데이터는 제외)  

```sql
SELECT COUNT(id) FROM book; --명령 + 검색할 컬럼  
-- book 테이블 안에 있는 id 컬럼의 개수를 검색  
SELECT COUNT(*) FROM book; 
-- 검색할 데이터에 *을 입력하면 모든 데이터 검색  
```  

**LIMIT** : 테이블에서 출력하고자 하는 데이터의 개수를 제한하는 명령  

```sql
-- book 테이블에서 데이터를 5개만 가져오기 
SELECT * FROM book LIMIT 5;  
-- 2번째 데이터부터 5개를 가져오기  
SELECT * FROM book LIMIT 1, 5;  
```  

**SUM** : 지정한 컬럼들의 값을 모두 더하여 총점을 구해주는 내장함수  

```sql
SELECT SUM(검색할컬럼) FROM grade;
```  

**AVG** : 지정한 컬럼들의 평군값을 구해주는 내장함수  
```sql
SELECT AVG(korean), AVG(english), AVG(math) FROM grade;  
-- 컬럼 중복 선택 가능  
```  

**MAX** : 테이블에 존재하는 데이터에서 최대값을 가져오는 내장함수  
(숫자형뿐만 아니라 문자형도 가능 (가장 높은 문자열 (ㅎ, z)))  
```sql
SELECT MAX(korean) FROM grade;
```

**MIN** : 테이블에 존재하는 데이터에서 최솟값을 가져오는 함수  
(숫자형뿐만 아니라 문자형도 가능)  
```sql
SELECT MIN(english) FROM graed;  
```  

## SQL로 데이터 그룹 짓기   
**GROUP BY**  
```sql  
SELECT 검색할 컬럼 + 적용할 함수  
FROM rental  
GROUP BY 컬럼 --그룹의 기준 컬럼  
```  

### 데이터 그룹에 조건 적용하기  

**HAVING 조건**  
```sql
-- rental 테이블에서 user_id가 같은 1개 초과의 데이터가 몇 개 있는지 검색   
SELECT user_id, COUNT(*)  
FROM rental  
GROUP BY uesr_id  
HAVING COUNT(user_id) > 1; --즉 GROUP BY의 서브옵션임  
```

### INNER JOIN : 두 개의 테이블에서 조회하기  
: 테이블을 웬만하면 기능별로 나누어 보관하는 편인데,   
: 이때 두 테이블의 정보를 한 번에 조회하기 위해 사용함  

```sql  
SELECT * --검색할 컬럼  
FROM rental --테이블  
INNER JOIN user --연결할 테이블  
ON user.id = rental.user_id; --특정 컬럼 기준으로 합침 (조건)  
```  

### LEFT JOIN : 왼쪽 테이블의 **모든 값**을 포함하여 연결  

즉 LEFT JOIN을 사용하면 왼쪽 테이블에서 null값도 포함시킬 수 있음  
```sql  
SELECT *
FROM user
LEFT JOIN rental
ON user.id = rental.user_id;
```

INNER JOIN : A와 B 겹치는 부분  
LEFT JOIN : A, A와 B 겹치는 부분  

### RIGHT JOIN : 오른쪽 테이블의 **모든 값**을 포함하여 연결  
```sql  
SELECT *
FROM user --테이블
RIGHT JOIN rental --연결할 테이블  
ON user.id = rental.user_id 
-- LEFT JOIN과 달리 기준 테이블의 컬럼을 기준으로 정하는 것이 아닌 대상 테이블(오른쪽)의 컬럼을 기준으로 정함  
```  

## 서브쿼리  
: 하나의 쿼리 안에 포함된 또 하나의 쿼리  
: 메인 쿼리가 서브쿼리를 포함하는 종속적인 관계  

```sql
SELECT * FROM employee  
WHERE 급여 > --연산자 오른쪽에
(SELECT 급여 FROM employee WHERE 이름 = 'elice') --서브 쿼리
```

**주의사항**  
1. 서브쿼리는 괄호와 함께 사용한다.  
2. 서브쿼리 안에서 ORDER BY 절은 사용할 수 없다.  
3. 서브쿼리는 연산자의 오른쪽에 사용되어야 한다.  
4. 서브쿼리는 오로지 SELECT문으로만 작성 가능하다.  

### 반환에 따른 분류  
: 결과가 한 행만 나오는 서브쿼리, 서브쿼리가 결과에 1개의 값만 반환하고, 이 결과를 메인쿼리로 전달하는 쿼리  

```sql  
SELECT * FROM employee  
WHERE 급여>
(SELECT 급여 FROM employee WHERE 사원번호 = 1);
```  

단일 행 서브쿼리와 다중 행 서브쿼리가 있음  
```sql  
-- 다중 행 서브쿼리 기본 문법  
SELECT * FROM employee  
WHERE 급여 IN (
    SELECT max(급여)
    FROM employee 
    GROUP BY 부서번호
);
```  

다중 행 연산자  
**IN** : 하나라도 만족하면 반환  
**ANY** : 하나라도 만족하면 반환, 비교 연산 가능  
**ALL** : 모두 만족하면 반환, 비교 연산 가능  

**다중 행 연산자 사용 예시**  
1 IN (!, 2, 3, 4) -> 참  
10 < ANY (1, 2, 3, 4)(최대값 4) -> 거짓  
99 >= all(99, 100, 101)(최댓값 101) -> 거짓   

### 위치에 따른 분류  
스칼라 서브쿼리 : SELECT 절에서 사용하는 서브쿼리, 오로지 한 행만 반환하고 마치 JOIN을 사용한 것과 같은 결과를 나타냄  

```sql
-- 스칼라 서브쿼리 사용 방법  
SELECT students.name, (
    SELECT math
    FROM middle_test as m
    WHERE m.student_id = students.student_id
) AS middle_avg
FROM students;
```  

