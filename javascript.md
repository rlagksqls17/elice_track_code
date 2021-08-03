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
//numbers라는 arrary, 1~5까지 아이템이 존재한다.
const numbers = [1, 2, 3, 4, 5]; 
//각 아이템의 2배를 저장
const doubled = numbers.map(number => number * 2); 
// 결과: [2, 4, 6, 8, 10]
console.log(doubled); 

// 말그대로 필터  
const newB = b.filter(function(item){
    return item > 3;
})

//리스트 끝에 요소 추가  
lists.push(i)

//**jsx**
const listItems = numbers.map(number =>
  <li>{number}</li> /*컴포넌트의 리턴 값*/
);

function NumberList(props) {
  const numbers = props.numbers;
  const listItems = numbers.map((number) =>
   /*li태그에 직접 key값을 부여*/ 
   // 보통 데이터의 id 값을 key값으로 부여
   // <태그명 key = 'key 데이터'></태그명>
    <li key={number.id}>
      {number}
    </li>
  );
  return (
    <ul>{listItems}</ul>
  );
// 혹은 map() 전체를 JSX 안에 넣으면 코드가 깔끔해질 수 있음  
function NumberList(props) {
  const numbers = props.numbers;
  return (
    <ul>
      {numbers.map((number) =>
        <ListItem key={number.toString()}
                  value={number} />
      )}
    </ul>
  );
}
}

function NumberList(props) {
  const numbers = props.numbers;
  const listItems = numbers.map((number) =>
    // ListItem 컴포넌트를 추출한 경우
    // 키 값을 지정해야합니다! : 배열값을 반환하기 때문이죠.
       <ListItem key={number.toString()}
              value={number} />
  );
  return (
    <ul>
      {listItems}
    </ul>
  );
}
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

#### string.includes('검색할 문자')

```jsx
(password.includes('#') == true)
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
    // 해당 요소의 html에 red라는 클래스를 변경
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

: HTML 요소에 대한 사건의 발생  (React도 동일)

#### addEventListener  

```js
function scrollUp(e) {
    /*1. 함수를 적용할 target 변수 지정하기*/
    var target = document.getElementById(e)
    /*2. 버튼 클릭 시 화면의 최상단으로 이동하기*/
    target.addEventListener('click', function(){
        window.scrollTo({top:0, left:0, behavior:'smooth'})
    })
    // 밖으로 뺄 때는 다음과 같이 사용
    // target을 함수 밖에서 정의해야 함
    target.addEventListener('click', scrollUp)
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

## import  

```jsx
// 권장
import {sayHi, sayBye} from './say.js';
// 비권장
import * as say from './say.js';
// 이름을 바꿔서 모듈을 가져옴
import {sayHi as hi, sayBye as bye} from './say.js';
```



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
      // Class가 아닌 ClassName을 사용
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
    // 정의는 return 문 밖에서
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

// 구조 분해 할당으로 간결하게 props를 받아오는 방법
const Welcome = (props) => {
    const { a, b, c } = props;
    return <div>...</div>
}
```

#### state  

컴포넌트 내에서 유동적으로 변할 수 있는 값을 저장

```jsx
// props 사용 시 코드
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

```jsx
import {useState} from 'react';

function Example(){
    // 초기값 0
    const [count, setCount] = useState(0);
     // state 변경시 리액트가 자동으로 렌더링 해줌
    // set 함수를 씀으로써 리액트가 자동으로 알아차림
    return (
    	<div>
            <p>버튼을 {count}번 눌렀습니다.</p>
            <button onClick={() => setCount(count + 1)}>
                
                
            // 여러줄로 사용하려면 다음과 같이 이벤트 등록
            setCount({current} => {
                    return current + 1
                })
                클릭
            </button>
        </div>
    );
}
// 또는
  return (
    <div className="App">
        <span>{count}회 클릭하였습니다.</span>
        <button onClick={() => {
            setCount(count+1);
        }}>클릭</button>
    </div>
  );
```

```jsx
// 오브젝트를 갖는 State를 만들 때 주의사항  
// 바로 object나 array 내부의 값만 변경할 경우 React가 새로운 값으로 변경된 것을 인지하지 못한다.
import { useState } from "react";

const [user, setUser] =
      useState({name:'민수', grade: 1})
	setUser((current) => {
        // 객체 복사
        const newUser = {...current}
        newUser.grade = 2
        return newUser
    })	
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

#### export

```jsx
export default Student;
```



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

### 이벤트  

1.리액트에서 이벤트의 이름은 카멜(Camel) 표기법으로 사용  

2.이벤트에 실행할 코드 전달(X) 함수 형태의 객체 전달(O)

```jsx
<input type = "text"
    name = "message"
    placeholder = "input message"
    // 이벤트 이름은 카멜 표기법으로 사용
    onChange = {
        // 이벤트를 실행할 코드를 그대로 전달하는 것이 아니라 아래 onClick 처럼 함수의 형태로 객체 전달
        // onChange = {함수명}
        (e) => {
            console.log(e.target.value)
        }
    }
```

3. 직접 만든 리액트 컴포넌트에는 이벤트를 자체적으로 설정할 수 없음 (<div><button><p><input>)  

```jsx
// 안 되는 예제 코드  
render() {
    return (
        <EventPractice onLoad={
            ()=>{
            console.log("test");
            }
        }/>
    );
}
```

#### 이벤트 등록

```jsx
// 함수형 컴포넌트에 이벤트 정의
function ActionLink(){
	// 등록 부분
    function handleClick(e){
        console.log('The link was clicked');
    }
    // 이벤트 호출 부분
	return (
	<a href= "#" onClick = {handleClick}>
	 Click me    
	</a>
		);
}

// 클래스형 컴포넌트에 이벤트 정의 (props 포함)
class Header extends React.Component {
  constructor(props) {
    super(props);
    this.state = {favoritecolor: "red"};
 // 1. 이벤트 바인딩
     this.이벤트명 = this.이벤트명.bind(this);
  }
    
// 2. 이벤트 정의  
    이벤트 명 = () =>{
        
    }
    
// 3. 이벤트 호출
  render() {
    return (
      <h1 onClick = {this.이벤트명}>My Favorite Color is {this.state.favoritecolor}</h1>
    );
  }
}

// 클래스인데 props 따로 지정 안할 시 **유용한 코드**  
import React from "react";

export default class Example2 extends React.Component {
  state = {
    text: "텍스트",
  };

  handleChange = (e) => {  // <- input값으로 text 변경 함수
    this.setState({
      text: e.target.value,
    });
  };

  render() {
    return (
      <div>
        <input onChange={this.handleChange} /> // <-변경된 곳
        <h1>{this.state.text}</h1>
      </div>
    );
  }
}
```

#### 이벤트 핸들링 하기  

```jsx
// 1. 함수로 작성하여 핸들링 하기   
<button onClick={
        () => {
            alert(this.state.message)
            this.setState({
                message : ''
            })
        }
    }>
</button>
// 2. 함수 미리 작성 후, 핸들링  
constrcutor(props){
    super(props);
    // 바인딩 : 해당 함수를 인지시켜줌
    this.handleClick = this.handleClick.bind(this);
}

handleClick(){
    console.log("message == ",this.state.message);
    this.setState({
            message : ''
    })
}
```

#### 이벤트 핸들러에 인수 전달하기  

```jsx
// id 값을 추가 인수로 전달해야 하는 경우  
// e : React 이벤트를 나타내는 인자
<button onClick={(e) => this.이벤트명(매개변수, e)}></button>
// bind를 사용하는 경우 e를 따로 전달해주지 않아도 됨
// 명시적으로 bind 지정 필요
<button onClick={this.이벤트명.bind(this, 매개변수)}></button>

// 예제 코드  
class EventClass extends React.Component {
  constructor(props) {
    super(props);
    // binding이 필요없음
  }

  //handleClick 이벤트를 정의합니다. 인자값을 받아 alert()을 출력합니다.
  handleClick = (data) => {
    alert(`전달받은 인자값: ${data}`)
  }


  render() {
    var data = "ABCDEFG"
    return (
      //data값을 인자값으로 제공하는 이벤트 핸들러를 작성합니다. 
      <button onClick = {(e) => this.handleClick(data,e)}>
        버튼을 눌러주세요!
      </button>
    );
  }
}
```

#### 조건부 렌더링  

```jsx
// 1
function Greeting(props) { //인사하는 컴포넌트 선언
  const isLoggedIn = props.isLoggedIn; //props에서 받아온 isLoggedIn값을 inLoggedIn 변수에 할당
  if (isLoggedIn) { //할당한 변수의 값을 if문으로 확인 (= 조건별로 구분하기)
    return <UserGreeting /> //true일 때 실행되는 컴포넌트
  }
  return <GuestGreeting /> //false일 때 실행되는 컴포넌트

  ReactDOM.render(
    //isLoggedIn={true}; 로 하면 어떤 컴포넌트가 실행될지 생각해보세요!
    <Greeting isLoggedIn={false} />, //Greeting이라는 컴포넌트를 불러올 때, isLoggedIn이라는 props를 주고, props의 false 값을 할당합니다.
    document.getElementById('root')
  );
}

// 2  
class LoginControl extends React.component {
  constructor(props) {
    super(props)
    this.handleLoginClick = this.handleLoginClick.bind(this);
    this.handleLogoutClick = this.handleLogoutClick.bind(this);
    this.state = {isLoggedIn: false};
  }

  handleLoginClick() {
    this.setState({isLoggedIn: true})
  }

  handleLogoutClick() {
    this.setState({isLoggedIn: false})
  }

  render() {
    const isLoggedIn = this.state.isLoggedIn;
    let button; //버튼 변수 선언 (바로, 이 변수가 element variables 입니다.) 컴포넌트를 이 변수에 할당할 수 있다는 의미입니다. (어려운 개념이 아니니, 겁 먹지 마세요!)

    if(isLoggedIn) {
      button = <LogoutButton onClick={this.handleLogoutClick} />; //로그인 상태일 경우, button변수에 LogoutButton 엘리먼트를 할당
    } else {
      button = <LoginButton onClick={this.handleLoginClick} />; //로그 아웃 상태일 경우, button변수에 LoginButton 엘리먼트를 할당
    }

    return (
      <div>
        <Greeting isLoggedIn={isLoggedIn} /> //Greeting 컴포넌트를 보여주고 있다.
        {button} //button 엘리먼트를 렌더링하고 있다.
      </div>
    )
  }
}

ReactDOM.render(
  <LoginControl />,
  document.getElementById('root')
);

// 3. JSX로 구현하기  
function Mailbox(props) { //Mailbox라는 function component 선언
  const unreadMessages = props.unreadMessages; //읽지 않은 메세지 값을 받아 unreadMessages 변수에 할당
/* 조건부 렌더링 부분! */
  return (
    <div>
      <h1>Hello!</h1>
            /*이 부분이 true이면 렌더링, false면 렌더링 하지 않는다.*/
      {unreadMessages.length > 0 && /* unreadMessages 의 길이가 0보다 크면 아래 <h2> 태그를 렌더링 */
        <h2>
          You have {unreadMessages.length} unread messages.
        </h2>
      }
    </div>
  );
}

const messages = ['React', 'Re: React', 'Re:Re: React']; //messages 배열에 3가지 값을 담았습니다.
ReactDOM.render(
  <Mailbox unreadMessages={messages} />, // props 값을 받는다.
  document.getElementById('root')
);

// 4. 
render() {
  const isLoggedIn = this.state.isLoggedIn;
  return (
    <div>
            {/* 중괄호 안에서 isLoggedIn이 true이며 LogoutButton 컴포넌트를 렌더링, false면 LoginButton 컴포넌트를 렌더링 */}
      {isLoggedIn ? ( 
        <LogoutButton onClick={this.handleLogoutClick} />
      ) : (
        <LoginButton onClick={this.handleLoginClick} />
      )}
    </div>
  );
}
```

#### &&  

```jsx
expr1 && expr2 // expr1이 true값을 반환할 수 있으면 expr2를 반환하고, 그렇지 않으면 expr1을 반환합니다.
true && expr // expr을 반환합니다.
false && expr // false를 반환합니다.
```

#### ?

```jsx
(조건) ? expr1 : expr2

function Check(props){
//Check의 props를 변수에 저장합니다.
  const data = parseInt(props.num);
  return(
    <div>
      <h2>{data > 0 ? "양수입니다" : "양수가 아닙니다."}</h2>

    </div>
  )
}
```

#### e.preventDefault()

React에서 이벤트가 실행될 때, 페이지가 자동으로 새로고침 되는데 이를 방지하기 위해서임   

```jsx
//<a href ="#">는 링크를 설정하지 않은 상태이기 때문에 현재 페이지로 이동하여 새로고침 된다. 이를 방지하는 것이 e.preventDefault()
<a href="#" onClick={handleClick}>
    Click me
</a>  

function handleClick(e) {
    e.preventDefault();
    console.log('The link was clicked.');
}
```

### 



 github 블로그를 직접 같이 만들어 보는 시간을 정해보았습니다 **(시간 조정 투표중)**. 엘리스 2기 스터디 (LMS 시스템) -> 마이블로그 1팀에서 화면 공유를 하며 진행할 예정입니다.  

몇 가지 세팅을 해주셔야 할 게 있습니다!  

1. 기존에 github 계정에서 (.io) 레포지토리가 있는 분들은 미리 삭제를 해주시기 바랍니다.  

2. https://gitforwindows.org/ 다음 사이트에서 git bash를 다운 받아주시기 바랍니다.(비쥬얼스튜디오에 있으시더라도 되도록 다운 부탁드립니다.)  

3. https://remotedesktop.google.com/support/ 컴퓨터 원격 지원을 위해 이 링크에서 요청하는 확장프로그램을 설치 바랍니다.

4. 맥 사용자 분의 경우 제가 도움을 드리기 힘듭니다 ㅠㅠ. 따라서 이 링크를 참고하셔서 만들어보시는 것이 더 도움이 될 것입니다.  

   https://devinlife.com/howto%20github%20pages/github-prepare/

