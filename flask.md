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
