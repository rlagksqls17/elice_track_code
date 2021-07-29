# jsonify  

```python
@app.route('/board', methods = ['GET'])
def read():
#json 출력 형태, GET 요청을 해당 URL로 할 시 반환됨
	return jsonify({"status" : 200, "result" : board})
```

```python
a = 'a'
b = 'b'

# 출력은 ["a", "b"]
return jsonify(a, b)

# 출력은 {"a" : a, "b" : b}
return jsonify({"a" : a, "b" : b})
```



# SQLalchemy (Model)

### 시작

```python
# db_connect.py  

from flask_sqlalchemy import SQLAlchemy  
db = SQLAlchemy()  
```

```python
# models.py  
from db_connect import db  

class Member(db.Model):
    id = db.Column(db.Integer, primary_key = True)
    name = db.Column(db.String(20), nullable = False)
    age = db.Column(db.Integer, nullable = False)  
    
    def __init__(self, name, age):
        self.name = name
        self.age = age  
```

```python
# app.py
from flask import Flask, render_template,request,redirect,url_for
from models import Member
from db_connect import db

app = Flask(__name__)

app.config['SQLALCHEMY_DATABASE_URI'] = "mysql+pymysql://root:devpass@127.0.0.1:3306/elice_flask_board"
app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False 

db.init_app(app)
```

### 쿼리    

```python
모델.query.all() # 모두 선택  

# and 선택  
member_list = Member.query.filter((Member.name == key1) & (Member.age==key2)).all()  

# or 선택  
member_list = Member.query.filter((Member.name == key1) | (Member.age==key2)).all()
```

### 커밋

```python
# 해당 db 모델을 수정후에 커밋 해줘야 함
db.session.add(user)
db.session.commit()
```



# MongoDB(파이썬)

### 생성

```python  
# 데이터베이스와 컬렉션을 생성하는 코드
import pymongo
from pprint import pprint

# 연결
connection = pymongo.MongoClient("mongodb://localhost:27017/")

# 데이터베이스 생성
db = connection.get_database("library")

# 콜렉션 생성
col = db.get_collection("books")
```

### 데이터 삽입  

```python
# 데이터 하나 삽입
result = collection.insert_one(dictionary)    
```

```python
# 데이터 여러개 삽입  
result = collection.insert_many([dic1, dic2, ...])  
```

### 데이터 출력

```python
# title이 Romeo and Juliet인 책의 정보를 출력
print(col.find_one({"title": "Romeo and Juliet"}))

# 반복문 활용하여 도큐먼트 출력
for 도큐먼트 in 컬렉션.find():
    print(도큐먼트)

# 삽입된 도큐먼트 _id 확인
col.inseted_one(data).inserted_id 

# 삽입된 데이터들의 _id 확인  
col.inseted_many(data).inserted_ids
```

```python
# 데이터를 보기 좋게 출력
import pymongo
from pprint import pprint  
```

### 데이터 검색  

```python
result = col.find(
    {쿼리}, 
    {"_id" : False} # 해당 필드를 제외하고 검색
)

# id 검색시 ObjectId를 씀
# 이후 커서를 받지 않고 요소를 검색해서 netflix에 받음
netflix = col.find({"_id" : ObjectId(show_id)})[0]
```



---

# flask

### 기본 준비

```python
# 라이브러리 사용
from flask import Flask

# flask 모듈 실행  
app = Flask(__name__)
```

### 라우팅  (GET)

```python
@app.route("/경로/<매개변수>", methods = ['GET'])
# GET 방식으로 URL 라우팅
# 이때 <매개변수>에 정보를 넣어주면 메소드의 첫 번째 매개변수로 입력 가능
# 예제
@app.route("/netflix/<show_id>", methods=['GET'])
def show(show_id):
    if request.method == "GET":
    	netflix = col.find({"_id" : ObjectId(show_id)})[0] 
    	return render_template('show.html', netflix = netflix)
```

### 라우팅  (POST)  과  form

```python
# URL 라우팅을 POST 방식으로 함
@app.route("경로", methods=['POST'])

# request 라이브러리를 사용  
from flask import request  

# request.form을 이용해 POST를 통해 전송된 데이터를 저장 확인  
data = {
    "show_id": request.form['show_id']
}
```

### render  template, Jinja template

```python
from flask import render_template, Flask  

@app.route("/")
def 메소드 명():
    # 해당 api에서 html을 반환해줌 (장식자 : 추가 기능을 덧붙임)
    # render_template 메소드를 이용하여 다음의 html템플릿을 렌더링 한다.  
    return render_template('출력할 html')
	
def 메소드 명():    
    data = [1, 2, 3]
	# html을 반환할 때 매개변수로 data를 같이 넘겨줌
	return render_template('출력할 html', data = data)

밑에 참고
```

```html
...
<ul>
<!-- 데이터를 Jinja 템플릿으로 받음-->
{% for t in data %}
  <li><a href="/netflix/{{ t._id }}">{{ t.data }}</a></li>
{% endfor %}
</ul>
...
```

### resirect  

```py
# URL을 새롭게 지정  
redirect("이동할 URL")
```

### ajax  

```js
...
            $.ajax({
                type: 'POST', // 포스트
                url: '{{url_for("ajax")}}', // url로 보냄
                data: JSON.stringify(postdata), // 다음의 데이터를
    
                data: {'user_id':user_id, // 이 형식의 데이터는 form으로 받을 수 있음  
                'user_pw':user_pw}
    
                dataType : 'JSON', // JSON 방식으로
                contentType: "application/json",
                success: function(data){ // 성공했을 시 알림
                    alert('성공! 데이터 값:' + data.result2['id']+" " + data.result2['name']+ " " + data.result2['context'])
    			window.location.href = '/' // 해당 URL로 이동
                },
                error: function(request, status, error){ // 실패했을 시 알림
                    alert('ajax 통신 실패')
                    alert(error);
                    window.location.reload() // URL 새로고침
                }
            })
        })
 ...
```



```python
# main.py  
@app.route('/ajax', methods=['POST'])
def ajax():
    # json 형태로 데이터를 저장
    data = request.get_json() ## json형식의 ajax 데이터를 요청해서 받음
    board.append(data)
    # 지시사항을 참고하여 데이터를 반환
    
    # result로 success를 ajax를 향해 넘겨줌
    return jsonify(result = "success", result2 = data)
```

### bcrypt  

```python
from flask_bcrypt import Bcrypt  
bcrypt = Bcrypt()

# 비밀번호를 해쉬함수로 변환  
pw_hash = bcrypt.generate_passwrod_hash(user_pw)

# 비밀번호와 입력받은 비밀번호가 같은지 확인
bcrypt.check_password_hash(user.user_pw, user_pw)
```

