몽고 DB는 DB 접속 -> 정보 저장 -> 정보 확인 순으로 이루어짐  

NoSQL의 경우  
1. 질의 명령어가 SQL이 아님  
2. 정보의 형식을 미리 정하지 않음  
3. _id 값이 자동 저장되었음  

MongoDB는 위 NoSQL의 특징을 가짐  
: 덜 제한적인 일관성 모델을 제공하는 데이터베이스  

서버에 요구되는 정보 처리량의 급속한 증가로, 정보 처리량을 늘리려면 규칙을 깨야하는 상황이 NoSQL DBMS의 유행 배경  

**안정성을 포기하면서 확장성과 성능 최적화에 특화시킴**  

**임시 정보를 굳이 안정적으로 저장할 필요가 없었음 (시간 낭비)**  

MongoDB : 현대적 설계로 고성능을 내면서 동시에 많은 기능과 안정화가 이루어진 다목적 DB  

현재는 처리할 데이터량이 많아서 분산 컴퓨팅이 빈번하다. 현대적 DBMS는 분산 컴퓨팅을 하는 것이 기본값  

### **분산 컴퓨팅의 방식**  

복제 : 복사하여 저장하는 방식 (안정성을 높임)  
**원본 서버가 망가져도 정상 서비스 가능**  

샤딩 : 나누어 저장하는 방식  
: 성능을 향상하기 위한 방식  

### 분산 컴퓨팅 관련 MomgoDB 주의점  
Mongo DB : 데이터가 의도치 않게 중간 상태로 저장될 수 있음 (안정성 떨어짐)  
(근데 분산컴퓨팅 할 경우 안정성까지 고려하면 부하가 많이 걸려 기본 설정이 분산컴퓨팅 상황으로 가정되어 있음)  
MySQL : 데이터가 항상 저장 완료하거나 저장 실패한 상태로만 존재  
Write-Concern, Read-Concern 설정을 제대로 알아야 함  

### JS 친화적 MongoDB  
분산 컴퓨팅 기본값 설정의 문제점은 입문이 너무 어려움  
MongoDB는 JSON과 유사한 BSON 구조로 정보를 저장  

MongoDB는 범용적인 DBMS로 활용 가능하다.  
단, 일반적인 상황에서 활용하기에는 무리가 있다.  

사용하기 바람직한 상황  
1. 프로젝트 언어를 JS로 통일시키고자 할 때  
2. 기존의 JSON 방식의 DB에서 좀 더 많은 기능과 성능이 필요할 때  
3. 저장할 정보의 형태가 자주 변경되는 경우  
4. 비 정형화된 정보를 전산화할 때 (수기 작성 데이터, 로그 데이터 등)  
5. 안정성보다 높은 성능이 필요한 경우  


**안 되는 상황**  
1. 높은 성능보다 안정성, 무결성이 중요한 경우  
(결제 시스템, 예약 시스템)  
2. 복잡한 쿼리가 빈번한 경우  
(JOIN, UNION과 같은 연산을 처리할 때 좀 더 복잡해짐)  
(RDB와 비교햇을 때 없는 함수가 꽤 있다.)  

 ## Mongo DB의 구조  
 데이터베이스> 컬렉션(테이블)> 도큐먼트(로우)의 3단계 구조  

 **Pymongo**  

 ```py
# mongoDB를 사용할 수 있게 도와주는 파이썬 모듈
import pymongo  

# url (내 pc내부(localhost) + Mongo DB 기본 포트)  
connection = pymongo.MongoClient("mongodb://localhost:27017/")

# 접속할 데이터베이스로 접근
# 만약 데이터베이스가 없으면 자동으로 생성한 후 접속  
db = connection.get_database("testDB")  

# 컬렉션에 접근  
# 컬렉션이 없을 때 자동으로 생성됨  
collection = db.get_collection("testCollection")  

# 컬렉션에 도큐먼트 저장   
collection.insert_one({"hello":"world"})  

# 데이터베이스 목록 조회  
print(connection.list_database_names())

# 컬렉션 목록 조회  
print(db.list_collection_names())  

# pprint로 도큐먼트 목록 조회  
pprint(list(collection.find()))  
```  

BSON : JSON의 일부로써 MongoDB 도큐먼트로 데이터를 저장하기 위한 방식  
데이터 타입으로는 NUlL, Undefind, Double, Integer, String, Object, Array, Boolean, Date, ObjectId 등이 있음  

ObjectId : MongoDB에서 각 Document의 prinmary Key값, 즉 식별값으로 사용된다.  
**샤딩이나 복제로 인한 혼동을 막기 위함**  

```py
# python에서는 다음과 같이 BSON을 사용함  
# python에서는 자료형을 하나하나 임포트 해주어야 하는 경우가 있음  
from bson import ObjectId  
from datetime import datetime  
collection.insert_one({
    "_id" : ObjectId("54c21354ef5132c54d")
    "name" : {"first": "sue", "last": "Turing"},
    "age" : 26,
    "is_alive": True,
    "ViewTime" : dateTime(2017,10,24,5.2.46)
})
```  

### 도큐먼트 생성  

pprint : pretty print (from pprint import pprint)   

```py
from pprint import pprint  
result = collection.insert_one(
    {document}
)
# 출력값 : 609fce475cfb965
print(result.inserted_id)  
# 출력값 : ObjectId('609fce475cfb965')
pprint(result.inserted_id)  

# 컬렉션에 다수의 도큐먼트 삽입  
result = collection.insert_many(
    [{document}, {document}] # 리스트 형으로 삽입
)
```  

따라서 주어진 정보로 게시글을 insert_one으로 저장하고,   
반환된 Objectid로 해당 게시글 접속 URL을 접속하고, URL을 반환  

### 도큐먼트 검색 기초  
커서란 쿼리 결과에 대한 포인터  

```py
result = collection.find(
    {query}
)
# list로 내용물을 한번에 불러옴
print(list(result))

#for 문으로 내용들을 하나씩 처리할 수 있음  
for document in result:
    print(document)
```

쿼리 : 원하는 정보를 걸러내기 위한 깔데기  
```py
# 쿼리 사용 예시
projection = {"_id" : False} # SELECT와 비슷한 기능

result = list(col.find( # 출력을 위해 list형으로 바꿔줌
    {}, # WHERE와 비슷한 기능임 (현재 조건이 없으므로 비어 있음) 
    projection 
))
```  

### 도큐먼트 수정  

```py 
#one은 하나만, many는 여러개를 수정
result = collection.update_one(
    {query}, # query로 검색
    {update}, # 변경할 사항을 적음
     # True 시 결과가 없어도 해당 도큐먼트를 생성해서 위 값을 자동으로 설정해줌   
    upsert : Boolean  
)
print(result.matched_count) # 찾은 도큐먼트 수  
print(result.modified_count) # 변경된 도큐먼트 수 

inventory.update_one(
    {"item" : "canvas"} # 쿼리
    {"$set" : {"qty" : 10}} # 해당 필드만 수정
    {"$unset" : {"qty" : False}} # qty 필드를 없앰
)
```  

### 도큐먼트 삭제
```py
result = collection.delete_one( # one 또는 many  
    {query} # 쿼리로 검색하고 첫 번째 도큐먼트를 삭제  
)
print(result.deleted_count)
```  

# 쿼리 연산자  
사용하게 될 쿼리와 연산자는 SQL과 Mongo DB간에 많이 다르다.  
```py
# SQL
SELECT * FROM table WHERE column = "value"
# Mongo DB
collection.find({"field":"value"}, {})  
```  
P
모든 연산자는 안쪽에서 쓰이지만, 예외적으로 $or, $and, $nor 세 개의 연산자는 가장 바깥에 쓰인다.  

### 점 표기법  
: BSON 내부의 Object에 접근하기 위한 방법  

```py
"name" : {"first" : "sue", "last" : "Turing"}

# 점 연산자로 내부에 접근할 수 있다.  
{"name.first" : 'sue'}  

"groups" : {"news", "sports"}

# 점 연산자로 배열의 요소를 찾을 수 있다.  
{"groups.0": "news"}
```  

### 비교 연산자  
$eq (equals)  
**$gt** (greater than)  
$gte (greater than or equals)  
**$lt** (less than)  
$lte (less than or equals)  
$ne (not equal)  
$in 
$nin  

```py
# 좋아요 수가 10초과 30미만인 도큐먼트 검색  
articles.find({"likes": {"$gt":10, "$lt" : 30}})  

# 수량이 5 또는 15인 아이템 도큐먼트 검색  
inventory.find({"qty" : {"$in" : [5, 15]}})  
```  

### 논리 연산자  
$or  
$and  
$nor : 주어진 조건 중 하나라도 false일 때 true  
$not : 주어진 조건이 false일 때 true  

```py  
# 게시물 중 제목이 aritlcle01이거나 작가가 Alpha인 도큐먼트
articles.find({"$or": 
                [{"title" : "article01"}, 
                {"writer" : "Alpha"}]
            }
        )

# 좋아요 수가 11 이하가 아닌 도큐먼트
articles.find({"likes" : 
                {"$not" : 
                    {"$lte" : 11}}
})
```  

### 문자열 연산자  
$regex : 특정 정규 표현식과 맞는 문자열을 매칭
```py  
{<field> : {"$regex" : 'pattern', "$options": '<options>'}}
# i = 대소문자 무시  
# m = 정규식에서 anchor(^)사용시 값에 \n 있다면 무력화  
# x = 정규식 안에 있는 whitespace를 모두 무시  
# s = dot(.) 사용 할 때 \n을 포함해서 매치 
```  
$text : 문자열 검색의 기능을 수행  
```py
"$text" : {"$search" : <string>, # 검색할 내용
            "$language"  : <string>, # 선택적 검색하는 언어
            "$caseSensitive" : <boolean>, # 선택적. False 일 경우 대소문자 무시
            "$diacriticSensitive" : <boolean> # 선택wjr. p hat과 같이 위 문자를 구분할지 선택  
} 
```  

**문자열 인덱스를 사전에 사용 해야만 text를 사용 가능**  

### 배열 연산자  

$all : 순서와 상관없이 배열 안의 요소가 모두 포함되면 선택
$elemMatch : 이 연산자에 작성된 조건과 맞는 배열 속 요소를 가진 도큐먼트를 선택  

```py  
survey.find(
    {"results" : {"$elemMatch" : {"product" : "xyz", "score" : {"$gte": 8}}}}
)
```    
$size: 해당 배열의 크기가 같은 도큐먼트를 선택  
```py
scores.find({results: {"$size":3}})
```  

### 세 가지 집계 방법론과 효율성  
1. 데이터베이스의 정보를 불러와 애플리케이션 단계에서 집계 (제일 자유도 높음)  
2. MongoDB의 맵 리듀스 기능을 이용  
: 관련된 정보끼리 그룹화    
3. MongoDB의 집계 파이프라인 기능을 이용 (제일 효율적)  
: 한 데이터 처리 단계의 출력이 다음 단계의 입력으로 연결된 구조    

**집계 연산을 초기에 할 수록 유리하다**   

