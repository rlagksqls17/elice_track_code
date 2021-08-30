# 데이터 분석  

## 문자열

### .startswith()  

```python
word = "superman"
print(word.startswith('s')) # True

if word.startswith('a'):
    print("a로 시작하는 단어입니다.")
```

### .split()

```python
numbers = "   1   2   3   "
print(numbers.split()) # ['1', '2', '3']

print(numbers.split(' ')) # ['', '', '1', '' ,'2', '', '3', '', '']
```

### .append()

```python
numbers = []
numbers.append(1)

print(numbers)  # [1]

numbers.append(2)
print(numbers) # [1, 2]
```

### .lower()

```python
intro = "My name is Elice"
lower_intro = intro.lower()
print(lower_intro)

# "my name is elice"
```

### .replace()

```python
intro = "제 이름은 Elice입니다."
print(intro.replace(' ', ''))
# "제이름은Elice입니다."


'/* elice */'.replace('/', '').replace('*', '').replace(' ', '')
# 'elice'
```



# Math

## sqrt

```python
import math

xa = 0
ya = 0
xb = 2
yb = 2

math.sqrt(((xb - xa) ** 2) + ((yb - ya) ** 2))
```



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
member_list = 모델이름.query.filter((Member.name == key1) & (Member.age==key2)).all()  

# or 선택  
member_list = 모델이름.query.filter((Member.name == key1) | (Member.age==key2)).all()

# 정렬  
    if q == '1':
        # 오름차순 정렬
        data = User.query.order_by(User.age.asc()).all()
    else:
        # 내림차순 정렬
        data = User.query.order_by(User.age.desc()).all()
```

### 삽입  

```python
# 파일 열어서 삽입
@app.route('/', methods=['GET', 'POST'])
def _update():
    if(Member.query.count()==0):
        file = open("member.txt", 'r')
        for i in file.readlines():
            a, b, c,= i.split(',')
            user = Member(int(a), b, c)
            db.session.add(user)
        db.session.commit()
        file.close()
        
# User 모델에 삽입     
user = User(name, email, description)
db.session.add(user)
```

### 수정  

```python
search_id = request.form['id']
change_name = request.form['name']
change_addr = request.form['addr']
target_member = Member.query.filter((Member.id == int(search_id))).all()[0]
target_member.name = change_name
target_member.addr = change_addr
```



### 커밋

```python
# 해당 db 모델을 수정후에 커밋 해줘야 함
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

### 데이터 수정  

```python
# form형식을 통해 데이터를 받음
data = {
    "show_id": request.form['show_id'] # name
}
# set : data를 써서 collection 업데이트
col.update_one(query, {"$set": data}) 
```

### 데이터 삭제  

```python
@app.route("/delete/<_id>")
def delete(_id):
    query = {"_id" : ObjectId(_id)}
    col.delete_one(query)
    return redirect("/")
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
# app.py
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
# main.py
data = {
    "show_id": request.form['show_id'] # name
}

## register.html  
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>HTML for python flask</title>
</head>

<body>
    <form action = "" method="post">
        <p>name : <input type="text" id = "username" name = "username"></p>
        <p>password : <input type="password" id = "password" name = "password"></p>
        <p>이름과 비밀번호를 입력하고 생성버튼을 누르세요.<br> <input type = "submit" value = "생성" onclick = "alert('생성 완료!')" /> </p>
    </form>
</body>
</html>
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

### redirect  

```python
# URL을 새롭게 지정  
return redirect("이동할 URL")

# id 변수 포함시켜 리다이렉트
return redirect(f"/netflix/{_id}")
```

### url_for  

```python
@app.route("/")
def home():
    if session.get('logged_in'): # true이면
        return render_template('loggedin.html')
    else: # false면
        return render_template('index.html')

@app.route('/login', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        name = request.form['username']
        password = request.form['password']
        try:
            if name in userinfo:
                # 비밀번호 검증 후 일치하는 경우 초기 페이지로 이동하세요.
                if password in userinfo.values():
                    session['logged_in'] = True
                    # ***여기가 중요***  
                    return redirect(url_for('home'))
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

### blueprint

```python
# app.py
from flask import Flask
from api import bp

app = Flask(__name__)
app.register_blueprint(bp)

# api.py
from flask import Blueprint

bp = Blueprint('main', __name__)

	# 작성한 게시글을 볼 수 있도록 함수를 완성하세요.
@bp.route("/post",methods=["POST"])
def create_post():
    content = request.form['content']
    return jsonify({'result':'success'})
```

### request  

```python
from flask import request

@friends.route("/friends/age")
def friends_age():
    # friends/age?flag=1로 접근 가능
    q = request.args.get("flag")
```

### migrate

https://flask-migrate.readthedocs.io/en/latest/

## 로그인 코드 예제  

```python
# api.py
from flask import redirect, request, render_template, jsonify, Blueprint, session, g
from models import User
from db_connect import db
from flask_bcrypt import Bcrypt

board = Blueprint('board',__name__)
bcrypt = Bcrypt()


@board.before_app_request
def load_logged_in_user():
    user_id = session.get('login')
    if user_id is None:
        g.user = None
    else:
        g.user = db.session.query(User).filter(User.id == user_id).first()


@board.route("/",methods=['GET'])
def home():
    return render_template("base.html")

@board.route("/join",methods=["GET","POST"])
# 1. 회원가입
def join():
    if request.method == 'GET':
        return render_template('join.html')
    else:
        # 아이디와 비밀번호를 받아옴
        user_id = request.form['user_id']
        user_pw = request.form['user_pw']
        pw_hash = bcrypt.generate_password_hash(user_pw)

        user_info = User.query.filter(User.user_id == user_id).first()
        # Ajax에 결과값을 넘겨줌
        if user_info:
            return jsonify({"result" : "id_check"})

        if len(user_pw) < 6:
            return jsonify({"result" : "pw_check"})


		# 모델을 세션(쿠키 데이터와 비슷)에 추가 (db.session)
        user = User(user_id, pw_hash)
        db.session.add(user)
        db.session.commit()
        
        
        
        return jsonify({"result":"success"})

# 2. 로그인
@board.route("/login", methods=['GET','POST'])
def login():
    if request.method == 'GET':
        return render_template('login.html')
    else:
        user_id = request.form['user_id']
        user_pw = request.form['user_pw']
        # id를 User 모델에서 걸러옴
        user = User.query.filter(User.user_id == user_id).first()
        # 결과를 Ajax로 넘겨줌
        if user is not None:
            if bcrypt.check_password_hash(user.user_pw, user_pw):
                # session의 로그인 영역에 id 넘겨줌
                session['login'] = user.id
                return jsonify({"result": "success"})
            else:
                return jsonify({"result": "fail"})
        else:
            return jsonify({"result": "fail"})

@board.route("/logout")
def logout():
    session['login'] = None
    return redirect('/')
```

```jsx
<script>
    function regist() {
        let user_id = $("#userId").val()
        let user_pw = $("#userPw").val()
        let user_pw2 = $("#userPw2").val()

        if (user_id == '' || user_pw == '') {
            alert("아이디와 패스워드를 입력해 주세요");
            return;
        }

        if (user_pw != user_pw2) {
            alert("비밀번호를 확인해 주세요!")
            return;
        }
        /* 지시사항 2번을 참고하여 코드를 작성하세요. */
        $.ajax({
            url: '/join',
            type: 'post',
            data: {
                'user_id': user_id,
                'user_pw': user_pw
            },
            success: function (res) {
                if (res['result'] == 'id_check'){
                    alert("이미 존재하는 ID입니다.")
                }
                // response 값에 따라 출력값이 달라짐
                else if (res['result'] == 'pw_check'){
                    alert("비밀번호를 6자리 이상 입력하세요.")    
                }
                if (res['result'] == 'success') {
                    alert("회원가입 성공!");
                    window.location.href = '/';
                }
            }
        })
    }
```

### JWT  

jwt는 서버와 클라이언트의 각각의 역할에 집중할 수 있는 매개체  

세션 관리를 하지 않고 JWT로 인증을 수행하므로 더는 인증을 위한 세션을 관리하면서 서버의 리소스를 낭비하지 않아도 됨

```python
from flask import Flask, request, render_template, jsonify
# jwt 모듈을 import하세요.
import jwt

app = Flask(__name__)
encryption_secret = "secret_elice"
algorithm = "HS256"

origin = {"name":"elice", "password":"elice@1234"}


@app.route("/", methods=["GET","POST"])
def jwt_route():
    # 조건문을 이용해 API 요청을 구분하세요.
    if request.method == 'GET':
        return render_template("index.html")    
    # 아니면 포스트
        # index.html에서는 ID와 PW를 각각 username과 password라는 변수에 담아 POST 방식으로 보냅니다. 
        # 작성된 API에서 POST로 보낸 변수들을 각각 id, pw 변수에 저장하세요.
    username = request.form['username']
    password = request.form['password']
        # 토큰 발급 전, 서버에 저장되어있는 아이디와 패스워드의 값과 일치 하는지 확인하세요. 
        # 저장된 유저의 정보와 입력된 정보가 일치한다면 5번~7번까지의 과정을 작성하고, 
        # 일치하지 않는다면 화면에 return jsonify("User Not Found")를 출력하세요.
    if origin['name'] != username or origin['password'] != password:
        return jsonify("User Not Found")
            # 정보가 일치하는 경우 사용자 변수를 만들기 위한 dictionary를 선언하세요.
    data_to_encode = {"name" : username, "password" : password}
            # 인증이 완료되면 전송할 encode, decode 정보를 저장하세요.
    encoded = jwt.encode(data_to_encode, encryption_secret, algorithm=algorithm)
            # 저장한 정보를 json 형태로 전송하세요.
    print(encoded)
    encoded = encoded.decode()
    print(encoded)
    decoded = jwt.decode(encoded, encryption_secret, algorithms=[algorithm])
        # 정보가 일치하지 않는 경우 "User Not Found"를 화면에 출력하세요.
    data = {"encoded" : encoded, "decoded" : decoded}

    return jsonify(data)
    
    
    
if __name__ == "__main__":
    app.run(debug = True)

    # decode는 byte를 받는게 아니라 문자열을 받는다...?
    # 그냥 돌리면 byte를 안 받으니까 에러가 나고,
    # 따라서 byte를 문자열로 바꾸기 위해 .decode()를 쓴다
    # 즉, jwt.decode와 byte.decode는 역할이 완전히 다르다!
    # jwt decode : 문자열 형식의 JWT -> JSON (딕셔너리)
    # byte decode : byte -> 문자열

if __name__ == "__main__":
    app.run(debug = True, port=1234)
```

### CORS  

flask에서는 flask-cors를 import를 설치하고 CORS(app) 한 줄을 추가해주면 됨 (보안의 목적으로 다른 서버에서 우리 서버에 데이터를 요청하는 것을 막음)  
