# javascript

### 변수 생성  

```js
// 선언과 변경이 자유로운 변수  
let a;

// 왠만하면 const 사용
// 값을 바꿀 수 없는 상수  
const b;
```

#### Destructuring assignment(Object)  

```js
// Past
var a = {x: 1, y: 2, z: 3};
var c0 = a.x;
var c1 = a.y;
var c2 = a.z; 

// New  
const b = {i: 1, j: 2, k: 3};
const {c0, c1, c2} = b;

// 리스트형의 경우 리스트 쓰기
const array = [5, 2];
const [a, b] = array;
```

### Array

```js
// 배열 생성
let lists = new Array();
let a = [0, 1, 2, 3, 4, 5];

// 배열의 요소를 하나씩 꺼내서 출력
b.forEach(function(item){
    console.log(item);
});
b.forEach => item => console.log(item)

// 순차적으로 함수를 실행하여 새로운 배열을 반환
const newB = b.map(function(item){
    return item * 2;
})

// 말그대로 필터  
const newB = b.filter(function(item){
    return item > 3;
})

//리스트 끝에 요소 추가  
lists.push(i)
```

#### spread syntax  

```js
const numbers = [1, 2, 3];
// _를 사용해 리스트를 넣어줌
//1 
function getSum(_n){
    let sum = 0;
    // n은 리스트
    n.forEach((item) => {
        sum += item;
    });
    return sum;
}

// 함수 호출
getSum(_numbers);

// 2
// ...numbers = [1, 2, 3]
const newNumbers = [0, ...numbers, 4, 5, 6]
```

### 문자열  

#### template literals

```js
// past
const text1 = "Hello" + name;

// now  
const text2 = `hello ${name}`;
```

### 객체

#### Shorthand property names  

```js
const username = "김민수";

const age = 21;

// `Shorthand property names` 표현을 이용하여 `username`과 `age`를 갖는 객체를 생성합니다.
const person1 = {
    username,
    age
};
// `console.log`를 이용하여 방금 만든 객체를 출력합니다.
console.log(person1);
```

#### spread syntax  

```js
const user = {name: "1", age :23, school: "d"}

// 두 객체를 합성 시 겹치는 key가 있을 경우 나중에 오는 값이 들어감
const newUser = {...user, grade:3 age:24}

function Test({name, age} = user){
    
}
```

#### Optional chaining  

```js
//! past
var x;
//값이 있는지 없는지 모를때 if문을 추가해야함
if(a && a.b && a.b.c){
    x = a.b.c;
}

// Now  
// 유효한 속성인지 검사하지 않고 값을 읽을 수 있음
// 유효한 속성이 아닐경우 undefined를 반환해줌  
const y = a?.b?.c;  
```



### for 문  

```js
for (i = 2; i < 201; i++){
        continue; // 컨티뉴 문
    }
```

### if 문  

```js
if(j != 1 && j != i){
    break; // 브레이크 문
}
```

### 함수 생성  

```js
function calcRectArea(width, height) {
  return width * height;
}
```

#### arrow function   

```js
// function 표현 보다 구문이 짧음  
const d = (x, y) => {
    console.log(x, y);
}
d(7, 8)
```



### 요소선택  - jquery

```javascript
let user_id = $('#userId').val
var user_id = $('#userId').val
```

```html
<div class="card">
    <div class="card-body">
        <div class="mb-3 row">
            <label class="col-sm-2 col-form-label">ID</label>
            <div class="col-sm-10">
                <!-- userId의 값을 선택-->  
                <!-- 작성된 값을 가지고 옴-->
                <input type="text" id='userId' class="form-control" placeholder="elice">
```

  ### 요소선택  - vanila

```js
// 주어진 classname을 갖는 요소의 목록을 반환
const elementsByClassName = document.getElementsByClassName('className')

// 주어진 tag를 갖는 요소의 목록을 반환  
const elementsByTagName = document.getElementsByTagName('tagName')

// 주어진 name을 갖는 요소의 목록을 반환  
const elementsByName = document.getElementsByName('name')

// 주어진 id를 갖는 요소를 반환  
const elementsById = document.getElementById('id')
```

```html
// 요소를 선택해 스타일을 바꿈  
<!-- test2.html -->
<div class="test" name="test">
	<test>테스트 1</test>
	<p class="test">테스트 2</p>
	<p id="test">테스트 3</p>
	<p name="test">테스트 4</p>
</div>

// test2.js
const elementById = document.getElementById("test")
elementById.style.color = "red"
```

```js
// element 안의 HTML을 선택해 value로 세팅  
element.innerHTML = value  

// element 안의 text를 선택해 value로 세팅  
element.innerText = value  

// input 태그의 값을 변경할 때 사용  
inputElement.value = value  
```

### 요소변경  - vanila

#### setAttribute  

```js
var blockOne = document.getElementById('red');

function changeColorRed(){
    // 해당 요소의 html에 red라는 클래스를 추가
    blockOne.setAttribute('class', 'red');
}
```

#### setInterval

```jsx
//jsx
function tick() {
  const element = (
    <div>
      <h1>{new Date().toLocaleTimeString()}</h1>
    </div>
  );
  ReactDOM.render(element, document.getElementById('root'));
}

// tick 함수를 1초에 한 번씩 호출 (1000)
setInterval(tick, 1000);
```



### 요소출력  

#### document.write('element')

```js
const student = {
    name: "elice",
    age: 7,
    address: "England",
    favorite: ["rabbit", "blue", "ribbon"]
}

// 웹 화면에 출력
document.write(student.name)   

// 줄 바꿈 출력 (개행)
document.write ('<br />')  
```

#### console.log ('element')

```js
// 웹 콘솔에 메시지 출력
console.log(obj1 [, obj2, ..., objN]);
console.log(msg [, subst1, ..., substN]);
```





## 이벤트  

: HTML 요소에 대한 사건의 발생    

#### addEventListener  

```js
function scrollUp(e) {
    /*1. 함수를 적용할 target 변수 지정하기*/
    var target = document.getElementById(e)
    /*2. 버튼 클릭 시 화면의 최상단으로 이동하기*/
    target.addEventListener('click', function(){
        window.scrollTo({top:0, left:0, behavior:'smooth'})
    })
}

scrollUp('scroll-btn')

// html
/* <body>
  <button class="scroll-top" id="scroll-btn">TOP</button>
</body> */
```

#### event.target.value

```jsx
// React  
class InputUserData extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: "엘리스 토끼",
      job: "developer"
    };
  }

  //name 데이터를 변경하는 메소드
  onNameHandler = event => {
    //setState를 사용해 name 데이터 업데이트 기능을 구현
    this.setState({
        // 삽입된 입력값 (name)은 event.target.value를 통해 가져올 수 있음
        // event.target은 자바스크립트에서 이벤트에 대상을 얻기 위해 사용됨
        name : event.target.value
    });
      
  render(){
      const { name, job } = this.state;
      return (
      	<div>
        <div>
             name: <input type="text" value={name} onChange={this.onNameHandler} /> 
        </div>
        </div>
      )
  }
  };
```



### **onload**  

 화면이 실행되거나 꺼졌을 때 발생

```html
<!-- test4.html -->
<html>
	<head>
		<script src="./test4.js"></script>
	</head>
	<body>
		<p id="test">test</p>
	</body>
</html>

// test4.js
// html 파일을 열었을 때 어떻게 될까요?
window.onload = () => {
	document.getElementById("test").style.color = "blue";
}
```

### **onchange**  

: 주로 폼에서 사용, 데이터가 변경되었을 때 발생  

```html
<!-- test5.html -->
<html>
	<head>
		<script src="./test5.js"></script>
	</head>
	<body>
		<input id="username" type="text" placeholder="아이디" onchange="changeHandle()"></input>
	</body>
</html>

// test5.js
const changeHandle = () => {
	console.log(document.getElementById("username").value);
}
```

### onsubmit  

```html
<!-- test6.html -->
<html>
	<head>
		<script src="./test6.js"></script>
	</head>
	<body>
		<form onsubmit="submitHandle()">
			<input id="username" type="text" placeholder="아이디"></input>
			<input id="password" type="password" placeholder="비밀번호"></input>
			<button type="submit">로그인</button>
		</form>
	</body>
</html>

// test6.js
const submitHandle = () => {
	const username = document.getElementById("username").value;
	const password = document.getElementById("password").value
	alert(`${username}과 ${password}로 로그인을 시도합니다`);
}
```

### onclick  

: 어떠한 요소가 클릭되었을 때 발생  

```html
<!-- test7.html -->
<body>
  <button id="btn" onclick = "changeButtonOnclick();">버튼을 눌러주세요</button>
</body>

// test7.js
var target = document.getElementById('btn');

function changeButtonOnclick() {
    target.Text = '버튼 클릭 성공!'
}
```

### onkeydown  

: 키가 눌렸을 때 발생하는 이벤트  

```html
<!-- test8.html -->
<html>
	<head>
		<script src="./test8.js"></script>
	</head>
	<body>
		<input id="username" type="text" placeholder="아이디" onkeydown="keyDownHandle(event)"></input>
		<input id="password" type="password" placeholder="비밀번호" onkeydown="keyDownHandle(event)"></input>
		<button onclick="clickHandle()">로그인</button>
	</body>
</html>
// test8.js
const clickHandle = () => {
	const username = document.getElementById("username").value;
	const password = document.getElementById("password").value;
	alert(`${username}과 ${password}로 로그인을 시도합니다`);
}

const keyDownHandle = (event) => {
  if(event.keyCode == 13){
    clickHandle();
  }
}
```

### onmouseenter

: 마우스를 올렸을 때 이벤트 발생

# React  

### 디렉토리 구조 살펴보기  

**./node_modules/** 

: npm을 이용해 설치한 패키지들 모음 

**./public** 

: 정적인 파일들을 모아놓는 곳 

**./src/** 

: 리액트 개발을 위한 파일들을 모아 놓는 곳 

**./.gitignore** 

: Git을 이용할 경우 불필요한 파일을 무시할 수 있도록 하는 설정파일 

**./package.json** 

: 프로젝트에 관한 정보와 사용하는 패키지들을 명세하는 파일 

**./README.md** 

: 내 프로젝트에 관한 설명을 작성하는 파일 

```js
// CSS나 import 하는 것 만으로 역할을 하는 라이브러리인 경우 패키지 명을 바로 import
import "패키지명" 

// 기본적으로 패키지를 불러와 활용할 때에는 할당할 이름을 작성 
import something from "패키지명" 
import Axios from "axios";

// 패키지 내의 일부 메소드나 변수만 가져올 때는 구조분해를 하여 가져옴 
import {a, b} from "패키지명" 

// 패키지에 default로 export 되는 객체가 존재하지 않을 경우 * as 이름으로 불러옴
import = as something from "패키지명"

// 별도의 CSS 파일을 작성 후 프로젝트에 적용하고 싶은 경우 사용
// import 시 style이 적용 됨  
import "./App.css"  
```

 ### jsx  

특징 

HTML 태그 내에 Javascript 연산 

class = 대신 className = 

#### 중괄호 ({})

jsx 중괄호 안에는 여러 **자바스크립트 표현식**을 사용 가능  

```jsx
const expression = 3*5
const element = <h1>3*5= {expression}</h1>;
```

#### **스타일은 object로 {{ }}**  

```jsx
//HTML의 인라인 스타일은 ""(큰따옴표)로 감싼 string으로 정의하지만 React에서는 {}(중괄호)로 감싼 object로 정의합니다.  
const App = () => (
    <div style={{ 
        padding: 30,  
        color: "red", 
        backgroundColor: "blue" 
    }}>Hello world!</div>
)
```

```jsx
import React from 'react';
import './App.css';

function App() {
  return (
    <div className="App">
        <div style = {{
        padding: 48,
        backgroundColor: "blue",
        color: "red"}}>안녕하세요.</div>
    </div>
  );
}

export default App;
```

```jsx
// 기존 JSX 문법 대신 React.createElement() 메소드 이용 가능  
// React에서 자동으로 코드 내 버그를 체크한다는 장점
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```

닫는 태그 필수 />

#### **최상단 element는 반드시 하나**   

```jsx
// 함수
const App = () => {
    return(
    <> {/* React.Fragment */}
     <div>Hello</div>
     <div>World</div>
    </>
    )
};

// 변수  
const element = (
    <div>
        <h2>코더랜드에 오신것을 환영합니다:)</h2>
        <h2>즐거운 React! 함께 공부해봐요~</h2>
    </div>
);
```

### Component   

1. React에서 페이지를 구성하는 최소단위 

```jsx
const MyComponent = {{ children }} => {
    return <div style = {{
            padding: 20,
            color: "blue"
        }}>
    {children}
    </div>;
}

// 컴포넌트 사용  
const App = () => {
    return {
        <div>
        <p>안녕</p>
        <MyComponent>반가워</MyComponent>
        <div>바이바이</div>
        </div>
    };
}
```

2. Component의 이름은 대문자로 시작 

3. Class Component/Function Component로 나뉨 

```jsx
// Function Component => 주로 사용
// 화살표 함수  
const Hello = (props) => {
    const {name} = props
    return <div>{name}님 안녕하세요.</div>
}
// 기본 함수  
function Clock(props) {
  return (
    <div>
      <h1>{props.date.toLocaleTimeString()}.</h1>
    </div>
  );
}  
// class Component
// 만들 때는 React.Component를 상속받고 render() 메소드를 구현해야 함  
class Clock extends React.Component {
  render() {
    return (
      <div>
        <h1>{this.props.date.toLocaleTimeString()}.</h1>
      </div>
    );
  }
}
```

4. Controlled Component/Uncontrolled Component 

#### 컴포넌트 합성  

```jsx
class Elice extends React.Component {
  render() {
    return <h2>I am a elice!</h2>;
  }
}

// Question 클래스에서 Elice 클래스를 참조 중
class Question extends React.Component {
  render() {
    return (
      <div>
      <h1>Who are you?</h1>
      <Elice />
      </div>
    );
  }
}

ReactDOM.render(<Question />, document.getElementById('root'));
```

#### props  

```jsx
const MyComponent = (props) => {
    const { user, color, children } = props  
    
    return(
    	<div style={{ color }}>
        <p>{user.name}님의 하위 element는!</p>
            {children}
        </div>
    )
}

<MyComponent user = {{name: "민수"}} color= "blue">
<div>안녕하세요.</div>
</MyComponent>
```

#### state  

```jsx
// 원래 코드
function Clock(props) {
  return (
    <div>
      <h1>{props.date.toLocaleTimeString()}.</h1>
    </div>
  );
}

function tick() {
  ReactDOM.render(
    <Clock date={new Date()} />,
    document.getElementById('root')
  );
}

setInterval(tick, 1000);
```

```jsx
class Clock extends React.Component {
  // props, this.state를 지정
    // 불필요한 내부 데이터 은닉
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }
  // 기존 클래스 함수
  render() {
    return (
      <div>
        <h1>{this.state.date.toLocaleTimeString()}.</h1>
      </div>
    );
  }
}

// 렌더링
ReactDOM.render(
  <Clock //원래 : date={new Date()} />,
  document.getElementById('root')
);
```

**setState()**  

State를 변경하기 위해서는 직접 값을 수정하는 것이 아니라 setState() 메소드를 이용해야 함  

```jsx
// onClickEventHandler() 메소드가 호출되면 State의 name 데이터가 "엘리스 토끼"로 변경됨
onClickEventHandler = () => {
  this.setState({
    name: "엘리스 토끼"
  });
};
```



### Element

엘리멘트란 React 앱의 가장 작은 단위를 말함  

#### Render 와 ReactDOM

```jsx
// App.js
const name = 'Josh Perez';
const element = <h1>Hello, {name}</h1>;

// id가 root인 태그를 찾은 후, 정의한 엘리먼트를 ReactDOM에 렌더링
ReactDOM.render(element,document.getElementById('root'));
```

```html
<!--index.html-->
<div id = "root"></div>
```

### 생명주기  메소드

React의 생명 주기는 컴포넌트가 이벤트를 다룰 수 있는 특정 시점을 말함  

**마운트** : 컴퓨터가 실제 DOM에 삽입 되는 것 

**업데이트** : 컴포넌트가 변하는 것  

**언마운트** : 컴포넌트가 DOM 상에서 제거되는 것

#### constructor() 

State 데이터를 초기화 하는 메소드

#### render()

클래스 컴포넌트에서 반드시 구현되어야 하는 메소드  

#### componentDidMount()

컴포넌트가 마운트 된 직후 호출되는 메소드

```jsx
class Header extends React.Component {
  constructor(props) {
    super(props);
    this.state = {favoritecolor: "red"};
  }
  // setTimeout 이용해서 타이머를 실행
  // 현재 코드를 실행하면 처음에는 red가 표시되다가 1초 뒤에 yellow로 변하게 됨
  componentDidMount() {
    setTimeout(() => {
      this.setState({favoritecolor: "yellow"})
    }, 1000)
  }
  render() {
    return (
      <h1>My Favorite Color is {this.state.favoritecolor}</h1>
    );
  }
}

ReactDOM.render(<Header />, document.getElementById('root'));
```



#### componentDidUpdate()

업데이트가 진행된 직후에 호출되는 메소드  

#### componentWillUnmount()  

컴포넌트가 마운트 해제되어 제거되기 직전에 호출되는 메소드



**예제 코드 1**  

```jsx
// App.js  
import React from 'react';
import './App.css';
import Welcome from './components/Welcome'

function App() {
  return (
    <div className="App">
        <Welcome />
    </div>
  );
}

export default App;


// Welcome.js
import React from "react";

const Welcome = () => {
    const username = "철수";
    
    return(
        <h1>{username}님 안녕하세요.</h1>
    )
}

export default Welcome;
```

**예제 코드2**

```jsx
//버튼 클릭된 횟수를 저장
let value = 0


//버튼 클릭시 횟수를 증가시키는 함수를 정의합니다.
function click() {
  value += 1;
}


function tick(){
  const element = (
    <div>
      <h1>버튼을 클릭해보세요</h1>
      <button onClick={click}>Click Me!</button>
      <h2>총 {value}번 클릭했습니다.</h2>
    </div>
  );
  
  //ReactDOM과 element를 렌더링합니다.
  ReactDOM.render(element, document.getElementById('root'));
  
}

//1초마다 tick()함수 호출
setInterval(tick, 1000);

serviceWorker.unregister();
```



