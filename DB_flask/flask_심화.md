## RDB로 리소스 관리 및 저장하기  

관계형 데이터베이스 정의 : 데이터를 저장하는 공간, 서비스를 개발하는 곳에서는 빠질 수 없는 중요한 요소, 키와 값들의 간단한 관계를 테이블 화 시킨 데이터베이스  

관계형 데이터베이스 특징 : DML을 사용해서 데이터 간 결합, 제약조건 등의 설정등을 통해 데이터를 추출할 수 있음  

데이터베이스의 종류는 크게 관계형 데이터베이스와 NoSQL로 나누어짐  

## RDB와 Flask  

파이썬은 오픈 소스와 상용 데이터베이스에 대한 대부분의 데이터베이스 엔진을 위한 패키지를 가지고 있음  

Flask에서 입력받은 내용을 DB에 저장할 수 있음  
**효율적인 데이터 관리 가능**  
예시 : 
```python
#app.py
from flask import Flask, render_template, request, url_for, redirect
# sqlite를 import 하세요.
import sqlite3  

app = Flask(__name__)
conn = sqlite3.connect('database.db')
print ("Opened database successfully")
conn.execute('CREATE TABLE IF NOT EXISTS Board (name TEXT, context TEXT)')
print ("Table created successfully")
value = [['Elice', 15], ['Dodo', 16], ['Checher', 17], ['Queen', 18]]
for i in range(4):
    conn.execute(f"INSERT INTO Board(name, context) VALUES('{value[i][0]}', '{value[i][1]}')")
conn.commit()
conn.close()


@app.route('/')
def board():
    con = sqlite3.connect("database.db")
    cur = con.cursor()
    cur.execute("select * from Board")
    rows = cur.fetchall()
    con.close()
    print("DB:")
    for i in range(len(rows)):
            print(rows[i][0] + ':' + rows[i][1])
    return render_template('board.html', rows = rows)

@app.route('/search', methods = ['GET', 'POST'])
def search():
    if request.method == 'POST':
        result = request.form['search']
        # 데이터베이스를 연결하세요.
        con = sqlite3.connect("database.db")
        # cursor 객체를 만드세요.
        cur = con.cursor()
        # Board 테이블에서 요청받은 result가 있는지 찾는 쿼리를 실행하세요.
        cur.execute(f"SELECT * FROM Board WHERE name ='{result}' or context = '{result}'")
        # 쿼리 실행 결과를 rows 변수에 저장하세요.
        rows = cur.fetchall()
        # DB의 연결을 해제하세요.
        con.close()

        return render_template('search.html', rows = rows)
    else:
        return render_template('search.html')

if __name__ == '__main__':
    app.run(debug=True)
```

```html
<!-- serch.html -->
<!doctype html>
<html lang="ko">
 <head>
  <meta charset="UTF-8">
  <meta name="Generator" content="EditPlus®">
  <meta name="Author" content="">
  <meta name="Keywords" content="">
  <meta name="Description" content="">
  <title>SQLite3 게시판 등록</title>

  <style type="text/css">
	body{ text-align: center; }
  </style>
 </head>
 <body>
	<form action = "/search" method = "POST">
		<input type = "text" name = "search" />
		<input type = "submit" value = "검 색" /><br>
	</form>
	<h4>검색결과</h4>
    {% if rows%}
	<table border=1 width="600" align="center">
		<thead>
		<td>이름</td>
		<td>내용</td>
		</thead>
	{% for row in rows %}
		<tr>
			<td>{{ row[0] }}</td>
			<td>{{ row[1] }}</td>
		</tr>
	{% endfor %}
    {% else %}
        <p> 검색결과가 없습니다. </p>
    {% endif %}
	</table>
 </body>
</html>
```

```html
<!--board.html-->
<!doctype html>
<html lang="ko">
 <head>
  <meta charset="UTF-8">
  <meta name="Generator" content="EditPlus®">
  <meta name="Author" content="">
  <meta name="Keywords" content="">
  <meta name="Description" content="">
  <title>SQLite3 게시판 등록</title>

  <style type="text/css">
	body{ text-align: center; }
  </style>
 </head>
 <body>
	<h3>게시판</h3>
	<h4>목록보기</h4>
	<table border=1 width="600" align="center">
		<thead>
		<td>이름</td>
		<td>내용</td>
		</thead>
	{% for row in rows %}
		<tr>
			<td>{{ row[0] }}</td>
			<td>{{ row[1] }}</td>
		</tr>
	{% endfor %}
	</table>
 </body>
</html>
```  

## JWT (JSON Web token)  
: 두 개체에서 JSON 객체를 사용하여 통신  
- **JSON 포맷을 이용하여 사용자에 대한 속성을 저장하는 Web Token**    
- 토큰 자체를 정보로 사용하는 Self-Contained 방식으로 정보를 안정하게 전달  

**JWT 생김새**  

- header : 토큰의 타입과 알고리즘을 저장  
- payload : 토큰에 담을 정보를 넣음  
- signature : 헤더와 정보의 인코딩 값들과 관련된 비밀키가 들어있음  

JWT는 위의 세가지로 이루어지며, JSON 형태인 각 부분은 Base64로 인코딩되어 표현됨 (각각의 부분을 이어주기 위해 (.) 구분자를 이용하여 구분함)  

### Heder  
토큰의 헤더는 typ와 alg 총 두 가지 정보로 구성됨  
typ : 토큰의 타입을 지정  
alg : 알고리즘 방식을 지정  

### Payload  
: 토큰에서 사용할 정보의 조각들인 클레임이 담겨 있음  
: 총 3가지로 나뉘며, JSON 형태로 다수의 장소를 넣을 수 있음  
: 충돌 방지를 위해 유니크한 네임을 URL 형식으로 가지고 있어야 함  

### Signature  
: JWT의 마지막 부분인 서명은 토큰을 인코딩하거나 **유효성 검증을 할 때 사용**하는 고유한 암호화 코드  

## ORM
: 데이터베이스에 객체를 통해 접근하는 방법 (객체 관계 매핑)  
: SQL 질의어가 없어도 데이터베이스를 다룰 수 있도록 도와줌  
: DB에 대한 큰 고민 없이, 데이터베이스를 코드로 다룰 수 있음  
: 테이블 구조가 변경될 때, ORM 모델만 수정하면 됨  
: 코드로 작성하기 때문에 쿼리를 직관적으로 이해할 수 있음  
 
SQL Alchemy : 파이썬 ORM 라이브러리 (파이썬 코드에서 Database와 연결하기 위해 사용하는 라이브러리)  

