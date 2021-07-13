# SQL  
## SQL이란  
데이터베이스 : 여러 사람이 공유해 사용할 목적으로 통합하여 관리되는 데이터의 모음  
데이터 베이스의 종류에 따라 사용 방법이 조금씩 다르지만 데이터베이스에서 검색과 분석에 사용되는 기본 사용 방법은 데이터베이스 종류와 상관없이 동일  

SQL : **Structured Query Language**  

## 테이블에서 데이터 검색하기  
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
SELECT title, author 
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
WHERE title = '돈키호테';  
```  
  
## 여러 개의 조건을 추가하기   

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

