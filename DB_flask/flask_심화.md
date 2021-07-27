# REST API  

자원을 이름으로 구분하여 해당 자원의 상태를 주고받는 모든 것  
**REST는 자원의 표현에 의한 상태 전달**  

무엇을 서버에 요청할 것인지, 어떻게 요청할 것인지를, API만 보고 알 수 있도록 함  

REST 서버는 API를 제공하고, 클라이언트가 사용자 인증 등을 관리하게 됨 (**즉 각각의 역할이 구분됨**)   
서로 간 의존성이 줄어든다  

따라서 **다른 곳에 이 API를 제공하기가 쉬워짐**    

REST는 상태정보를 따로 저장하고 관리하지 않음. 세션 정보나 쿠키 정보를 별도로 저장하고 관리하지 않기 때문에 API 서버는 들어오는 요청만을 단순히 처리  

URL과 URI는 해당 파일이 실제로 해당하는 주소에 존재하는가에 따라 차이가 있음   

REST API에서 동작을 표현하는 방법은 HTTP Method이다.  
GET, POST, PUT, DELETE  

1. 리소스 요청은 주로 동사보다는 명사를 사용  
ex) GET/memebers/delete/1 는 GET/members/1로  

2. 슬래시는 계층 관계를 나타냄  
ex) http://elice.example.co.kr/lecture/python  

3. 파일 확장자는 URI에 포함하지 않음  
4. 긴 URI에서는 밑줄보다는 하이픈을 사용  
ex) http://elice.example.co.kr/board.free-talk  

## HTTP 응답 상태 코드  

200 : 정상적으로 수행  
201 : 성공적으로 리소스 생성  
400 : 클라이언트의 요청이 부적절할 때  
401 : 인증되지 않은 상태에서 리소스 요청  
404 : 응답하고 싶지 않은 리소스, 혹은 없는 리소스를 요청  
500 : 서버에 문제가 생겼을 때  

## flask-restful  
flask는 return 값을 jsonify로 주어서 RESTful API를 만들 수 있음  

flask-restful : 좀 더 RESTful에 맞게 서버를 만들 수 있는 라이브러리  

**앞의 실습에서는 render_template() 메소드를 이용해 HTML에 출력 결과를 띄워 값들을 확인했다. 그리고 HTML에서 Jinja2 문법으로 해당 내용을 띄울 수 있었다. 하지만 이는 API 서버를 개발한 것이 아닌, Flask를 활용해 웹 애플리케이션을 개발한 것이다.**  

**REST API 서버를 개발할 때는, 서버 측에서 직접 rendering 하며 페이지를 보여주는 것이 아닌, 웹 페이지를 구성하는데 필요한 정보를 반환해주도록 해야 한다.**  

**따라서 백엔드 서버는 클라이언트와 데이터를 주고받음으로써 통신을 하게 됨**  

## flask-Test  
**장점**  
1. 테스트 환경 세팅 자동화  
2. 통합 테스트 시간을 줄임   
3. 외부와 의존성 있는 로직을 테스트하기 편리  
: 외부와 통신하는 로직을 Mock으로 처리해두면, 외부에서 발생할 수 있는 여러 환경을 가짜로 구성 가능  
4. 전체 테스트 자동화  

예제  
```py  
# flask  
@app.route('/mysum', methods = ['GET'])
def add():
    data = request.args  
    num1 = int(data.get("a"))
    num2 = int(data.get("b"))
    return jsonify(
        {'result':num1 + num2}
    )

# test  
def test_get():
    response = app.test_client().get(
        'mysum?a=10&b=20',
    )
    data = json.loads(
        response.get_data()
    )
    assert response.status_code == 200
    assert data['result'] == 200  
```  

