# flask  

## 웹 서버의 동작과정  
클라이언트가 서버로 요청을 하고, 요청을 받은 서버는 요청에 해당하는 데이터를 응답으로 돌려줌  

서버의 응답으로 클라이언트가 보게 되는 데이터는 HTML, JSON, XML등 다양한 형태가 될 수 있음  

**미리 약속한 규칙을 통해서 클라이언트가 요청하면 정해진 데이터로 서버가 응답한다.**  

**API** : 정해진 방식으로 정해진 데이터의 통로 역할을 함  
즉 클라이언트가 요청하면 서버가 API(즉 url 주소 : https://www.naver.com)를 통해 데이터를 보내줌  

## flask framework  
framework : 하나의 결과물을 만들기 위해서 제공하는 '틀', 미리 작성되어 잇는 함수 이상의 기능을 제공  

flask : python을 사용해서 웹 서버를 만들 수 있게 도와주는 Web Framework  

- 나만의 서버를 쉽게 작성 할 수 있다.  
- 간단한 코드로 빠르게 실행 가능하다.  
- 원하는 기능을 유연하게 확장되기 편리하다.  

Flask Simple Web Server 만들기  
```python
from flask import Flask 
app = Flask(__name__) 

@app.route("/") # app.route는 서버에 접속할 수 있는 url 만들어 줌  
def print_hello(): # app.route의 url에서 실행할 함수  
    return "hello" 

# 위 세 줄이 하나의 API 역할을 함  

if __name__ == "__main__": # 파일 이름이 main일 때만 app.run()실행  
    app.run()
```  

## URL 연결 후 데이터를 화면에 나타내기  
JSON 형식의 데이터 나타내기  

```python
from flask import Flask, jsonify  
app = Flask(__name__)

@app.route("/")
def elice_json():
    my_data = {"name":"pwd"} # 다음 데이터를 화면에 전달해줌  
    return jsonify(my_data)

if __name__ == "__main__":
    app.run()
```  

HTML 형식의 데이터 나타내기  
- 파일 준비하기  
templates   
ㄴ index.html (template 폴더 아래에 넣어주면 flask가 인식)  
app.py  

- app.py 준비하기  
```python
from flask import Flask, render_template  
app = Flask(__name__)  

@app.route("/") # API 통로 한 개당 함수 한 개  
def index_html():
    return render_template("index.html") 
    # template 폴더 안의 index.html 파일을 불러와 줌  

if __name__ == "__main__":
    app.run()
```  

## REST API  
HTTP URL을 통해 자원을 명시하고, HTTP Method(POST, GET, PUT, DELETE)를 통해 해당 자원에 대한 CRUD Operation을 제공하는 것  

다양한 클라이언트가 생겨남에 따라서 REST API가 필요하다.  
REST API는 메시지가 의도하는 바를 URL에서 나타내므로, 쉽게 기능을 파악할 수 있음  
HTTP 표준 프로토콜에 따르는 플랫폼에서 사용 가능하다.  
서버와 클라이언트의 구분을 명확하게 할 수 있다.  
REST API의 표준이 존재하지 않는 단점이 있다.  

## HTTP Method  
GET과 POST는 HTTP Metho 중 하나임  
GET = 데이터를 URL 뒤에 ?와 함께 사용함  
예시 : http://사이트의_주소?데이터 = 123  

POST = 특정 양식에 데이터를 넣어 전송하는 방법임 (**보안이 더 좋음**)  
예시 : http://사이트의_주소  

GET 요청 예시  
```python
@app.route('url1', methods = ["GET"])
# URL 뒤에 ?name = elice를 넣어 GET 요청을 함  
def elice():
    name = request.args.get['name']
    result = "hello. " + name
    return result
```  

POST 요청 예시  
```html
<!--index.html-->
<html>
<body>
    <form actrion = '/login' method = 'post'>
        <p>
            아이디 : <input type = 'text' name = 'id'>
        </p>
        <p>
            비밀번호 : <input type = 'password' nmae = 'pwd'>
        </p>
        <button type = 'submit'> <!--form형식으로 전송이 됨-->
    </form>
</body>
</html>  
```  

```python
from flask import *
app = flask(__name__)

@app.route("/", methods = ["GET"])
def elice():
    return render_template("index.html")

@app.route("/login", methods = ["POST"])
def elice_post():
    id = request.form['id']
    pwd = request.form['pwd']
    if id == 'elice' and pwd = '1234':
        return 'Hi! Elice"
    else:
        return "ERROR"
```  

## Blueprint와 Jinja Template  
Blueprint : API들을 분류 및 관리해줌  
Flask의 기능이 점점 늘어날수록, 자연스럽게 코드의 양이 증가한다. 이때, Blueprint를 사용해서 길어진 코드를 모듈화해주어 수정 개발과 유지보수에 용이하게 코드를 관리할 수 있다.  

```python
# app.py : 서버 실행 만을 위한 파일
from flask import Flask  
from first_api import bp  

app = Flask(__name__)
app.register_blueprint(bp) # 코드 주목  

if __name__ == '__main__':
    app.run(debug=True)
```

```python
# first_api.py
from flask import Blueprint, jsonify
bp = Blueprint('bp', __name__)

@bp.route('/first', methods = ['GET'])
def first_route():
    return jsonify ('first page')

@bp.route()
def ... :...
```

Jinja2 : 파이썬에서 가장 많이 사용되는 템플릿   
서버에서 받아온 데이터를 효과적으로 보여주고 비교적 간략한 표현으로 데이터를 가공할 수 있음  

- Jinja2 Template에서 데이터 넘겨주기 - 단일변수  
```python
# app.py  
@app.route("/")
def elice():
    my_list = [1, 2, 3, 4, 5]
    return render_template(
        'index.html',
        data = my_list
    )
```   

```html
<!--index.html-->
<html>
    <head>
        <title> jinja example </title>
    </head>
    <body>
        <!--jinja template이용해 파이썬 코드 작성-->
        {{ data }}
        {% for d in data %} 
            {{ d }}
        <!--딕셔너리 키 이용할 경우-->
        <!--{{ data.get('name') }}-->
    </body>
</html>
```  

## Authentication vs Authorization  
Authentication : 사용자가 누구인지 확인하는 절차  
Authorization : 클라이언트가 하고자 하는 작업이 해당 클라이언트에게 허가된 작업인지 확인  

쿠키 : 클라이언트에 저장되는 키/값이 들어 있는 데이터, 사용자가 따로 요청하지 않아도, Request 시에 자동으로 서버에 전송한다.    
세션 : 쿠키를 기반으로 하지만 서버 측에서 관리하는 데이터, 클라이언트에 고유 ID를 부여하고 클라이언트에 알맞은 서비스를 제공한다. 서버에서 관리하기 때문에 보안이 쿠키보다 우수하다.  

로그인 예제  
```python  
user_id = request.form['user_id']
user_pw = request.form['user_pw']
user = {'user_id' : 'elice', 'user_pw' : '1234'}

if user is not None:
    if user_id == user['user_id'] and user_pw == user['user_pw']:
        session['login'] = user.id
        return jsonify({"result":"success"})
    else:
        return jsonify({"result":"fail"})
```  
## 로깅  
로깅 : 프로그램이 작동할 때 발생하는 이벤트를 추적하는 행위, ㅍ로그램의 문제들을 파악하고 유지보수하는데 사용  
**로깅-level**  
- DEBUG : 상세한 정보  
- INFO : 일반적인 정보  
- WARNING : 예상치 못하거나 가까운 미래에 발생할 문제  
- ERROR : 에러 로그, 심각한 문제  
- CRITICAL : 프로그램 자체가 실행되지 않을 수 있는 문제  

기본 로거 레벨 세팅이 WARNING이기 때문에 설정을 해줘야 함 (그 이하의 레벨은 출력되지 않을 수 있음)  

```python
# 변경 전  
import logging  
if __name__ == '__main__':
    logger.info("hello elice!")
```

```python
# 변경 후  
import logging  
if __name__ = '__main__':
    logger = logging.getLogger()
    logger.setlevel(logging.DEBUG)
    logger.info("hello elice!")
```  

```python
# 404 에러를 제어하는 코드를 추가하세요.
@app.errorhandler(404) # 404 에러 잡아줌  
def page_not_found(error):
    app.logger.error(error) #에러 발생 관리자가 식별가능하게 해줌
    return render_template("page_not_found.html")
```  

## Ajax란?  

동기 : 앞의 작업이 끝나지 않으면 다음 작업을 할 수 없다.  
비동기 : 앞의 작업 상태와 상관없이 다음 동작을 수행할 수 있다.  

이러한 비동기 처리 방식에는 Fetch, AXIOS, AJAX가 있음  

**Ajax의 형태**  
```javascript
$.ajax({
    url : 'URL 주소', // Ajax로 요청을 보낼 주소를 적는 곳
    type : '메서드', // Ajax로 보낼 방법을 적는 곳 
    data : {}, // Ajax 통신으로 보낼 데이터를 적는 곳
    success : function(res){ // 통신이 성공한 후 실행되는 함수
        console.log(res)
    }
})  

///HTML  
<button onclick = ajaxTest()> 호출 </button>
```  

