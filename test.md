# Open API  

RESTful API 를 하나의 문서로 정의하기 위한 문서 표준  

OpenAPI Specification으로 정의됨  

Swagger 등의 툴로, Open API로 작성된 문서를 파싱해 테스팅 도구로 만들 수 있음  

프론트엔드 개발자, 백엔드 개발자와의 협업 시 주요한 도구로 사용  

API의 method, endpoint를 정의하고, endpoint마다 인증 방식, content type 등 정의함, 이후 body data, query string, path variable 등을 정의하고, 요청과 응답 데이터 형식과 타입을 정의해서 data model을 활용함  

# CORS  

Cross-Origin Resource Sharing  

브라우저는 모든 요청 시 Origin 헤더를 포함함  

서버는 Origin 헤더를 보고, 해당 요청이 원하는 도메인에서부터 출발한 것인지를 판단, 다른 Origin 에서 온 요청은 서버에서 기본적으로 거부함  

그러나, 보통 서버의 endpoint와 홈페이지 domain은 다른 경우가 많음, 따라서 **서버에서는 홈페이지 domain을 허용하여, 다른 domain이라 하더라도 요청을 보낼 수 있게 함.**  

서버는 Access-Control-Allow-Origin 외에 Access-Control-*을 포함하는 헤더에 CORS 관련 정보를 클라이언트로 보냄  

CORS는 웹 사이트에 악성 script가 로드되어, 수상한 요청을 하는 것을 막기 위함. 반대로, 익명 유저로부터의 DDos 공격 등을 막기 위함. 서버에 직접 CORS 설정을 할 수 없다면, Proxy 서버 등을 만들어 해결  

# 상태관리

```python
컴포넌트 내에서 유동적으로 변할 수 있는 값을 저장

앱 상에서의 데이터를 메모리 등에 저장하고 하나 이상의 컴포넌트에서 데이터를 공유하는 것 

앱이 사용하는 데이터가 점점 많아지고, 유저와의 인터렉션 시 임시로 저장하는 데이터가 많아지는 경우 상태관리를 고려

# 상태 관리 기술이 해결하는 문제들
SPA에서 페이지 로딩 시마다 모든 데이터를 로딩한다면 사용자 경험 측면에서 MPA를 크게 넘어서기 힘듦  

오히려 네트워크 요청 수가 많아져 더 느릴 수도 있음  

변경이 잦은 데이터가 아니라면, 데이터를 캐싱하고 재활용함

변경이 잦다면, 데이터의 변경 시점을 파악해 최적화
ex) : 일정 시간마다 서버에 저장, 타이핑 5초 후 서버에 저장

def Prop drilling:
    컴포넌트가 복잡해지는 경우, 상위 부모와 자식 컴포넌트 간의 깊이가 커짐  
    최하단의 자식 컴포넌트가 데이터를 쓰기 위해 최상위 컴포넌트로부터 데이터를 보내야 하는 상황이 발생  
    이때 Context API 등을 활용, 필요한 컴포넌트에서 데이터를 가져올 수 있음 (컴포넌트 간의 결합성을 낮춤)
    
# 장점
높은 품질의 코드를 작성하는 데 유리  
성능 최적화, 네트워크 최적화 등에 유리  
데이터 관리의 고도화  

# 단점
Boilerplate 문제
파악해야 할 로직과 레이어가 많아짐 
잘못 사용할 경우 앱의 복잡도를 높이거나 성능을 악화
(global state의 잘못된 사용시 앱 전체 리렌더링 발생)
```

## Flux Pattern  

```pascal
2014년에 facebook에서 제안한 웹 애플리케이션 아키텍처 패턴 
Unidirection data flow를 활용, 데이터의 업데이트와 UI 반영을 단순화  
React의 UI 패턴인 합성 컴포넌트와 어울리도록 설계  
redux, react-redux 라이브러리의 Prior art

Flux는 하나의 Action이 하나의 Update만을 만들도록 함
data와 업데이트가 한 방향으로 흐르므로 UI의 업데이트를 예측하기 쉬움

Action -> Dispatcher -> Store -> View 순으로 데이터 흐름
Store는 미리 dispatcher에 callback을 등록해 자신이 처리할 action을 정의  
action creator는 action을 생성하여 dispatcher로 보냄
dispatcher는 action을 store로 넘김  
sotre는 action에 따라 데이터를 업데이트 후, 관련 view로 변경 이벤트 발생
View는 그에 따라 데이터를 다시 받아와 새로운 UI를 만듦
유저 인터렉션이 발생하면 View는 action을 발생

하나의 유저 인터렉션에 여러 Action을 생성 가능  
```

![image-20210810213413135](C:\Users\joo\AppData\Roaming\Typora\typora-user-images\image-20210810213413135.png)

## MVC Pattern

```html
<Model View Controler>
MVC 패턴에서는 View에서 특정 데이터를 업데이트 하면 연쇄적인 업데이트가 일어남  
특정 유저의 인터렉션이 여러 UI 컴포넌트가 사용하는 데이터에 영향을 줄 때, MVC만으로는 앱의 복잡도를 낮추거나 업데이트의 흐름을 따라가기 어려움
```

# Pigma  

react 개발 시 편리한 시각화를 도움  

https://figma.com/

