# javascript

### 변수생성

```js
// 선언과 변경이 자유로운 변수  
let a

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

## 구문

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

### 에러 캐치  

```js
try {
    ···
} catch(e) {
    ···
}

if (error) return "error!"
```

## 함수 생성  

```js
function calcRectArea(width, height) {
  return width * height;
}
```

### arrow function   

```js
// function 표현 보다 구문이 짧음  
const d = (x, y) => {
    console.log(x, y);
}
d(7, 8)
```

## DOM

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

## this  

```js
// call 또는 apply의 첫 번째 인자로 객체가 전달될 수 있으며 this가 그 객체에 묶임
var obj = {a: 'Custom'};

// 변수를 선언하고 변수에 프로퍼티로 전역 window를 할당
var a = 'Global';

function whatsThis() {
  return this.a;  // 함수 호출 방식에 따라 값이 달라짐
}

whatsThis();          // this는 'Global'. 함수 내에서 설정되지 않았으므로 global/window 객체로 초기값을 설정한다.
whatsThis.call(obj);  // this는 'Custom'. 함수 내에서 obj로 설정한다.
whatsThis.apply(obj); // this는 'Custom'. 함수 내에서 obj로 설정한다.
```

## bind  

```js
// f.bind(someObject)를 호출하면 f와 같은 본문(코드)과 범위를 가졌지만 this는 원본 함수를 가진 새로운 함수를 생성합니다. 새 함수의 this는 호출 방식과 상관없이 영구적으로bind()의 첫 번째 매개변수로 고정됩니다.

function f() {
  return this.a;
}

var g = f.bind({a: 'azerty'});
console.log(g()); // azerty

var h = g.bind({a: 'yoo'}); // bind는 한 번만 동작함!
console.log(h()); // azerty

var o = {a: 37, f: f, g: g, h: h};
console.log(o.a, o.f(), o.g(), o.h()); // 37, 37, azerty, azerty
```

## 비동기  

: 초기 웹 환경에서는 서버에서 모든 데이터를 로드하여 페이지를 빌드했으므로 자바스크립트에서는 별도의 비동기 처리가 필요하지 않음. Ajax 기술의 등장으로 **페이지 로드 없이** **client-side에서 서버로 요청을 보내 데이터를 처리**할 수 있게 됨. XMLHttpRequest라는 객체를 이용해 서버로 요청을 보낼 수 있게 됨. 자바스크립트는 single-thoreaded language이므로, 만일 서버 요청을 기다려야 한다면 유저는 멈춰있는 브라우저를 보게 될 것. 따라서 **동기가 아닌 비동기 처리를 이용해 서버로 통신할 필요가 있음**. 비동기 요청 후, main thread는 유저의 입력을 받거나 페이지를 그리는 등의 작업을 처리. 비동기 응답을 받으면 응답을 처리하는 callback 함수를 task queue에 넣고, event loop는 main thread에 여유가 있을 때 task queue에서 함수를 꺼내 실행  

**동기** : 해당 코드블록을 실행할 때 스레드의 제어권을 넘기지 않고 **순서대로 실행**하는 것을 의미 **(Call stack에 넣어짐)**

```js
console.log("This is synchronus...")

for (let i = 0; i < 1000000000; ++i){
    console.log("I am blocking the main thread")
}

console.log("This is synchronus...DONE!")
```

**비동기** : 코드의 순서와 다르게 실행 됨, 가장 밑의 코드가 실행이 될 수도 있음, 비동기 처리 코드를 감싼 블록은 task queue에 넣어짐, main thread가 동기 코드를 실행한 후에 제어권이 돌아왔을 때 event loop가 task queue에 넣어진 비동기 코드를 실행 함 **(Task queue에 넣어짐)**

```js
setTimeout(() => console.log("This is asynchronus..."), 5000)  

console.log("This is synchronous...")

// 오랜시간 main thread가 실행되기 때문에 포문이 끝날때 까지 setTimeout()이 기다려지게 됨
for (let i = 0; i < 1000000000; ++i){
    console.log("I am blocking the main thread...")
}
```

```js
request("user-data", (userData) =>{
    console.log("userData 로드")
    saveUsers(userData)
});

console.log("DOM 변경")
console.log("유저 입력")
```

**브라우저의 main thread는 자바스크립트 코드에서 동기적으로 처리되어야 할 코드 실행 외에도, 웹 페이지를 실시간으로 렌더링하고 유저의 입력을 감지하고, 네트워크 통신을 처리하는 등 수많은 일을 처리**

비동기 작업을 할당하면, 비동기 처리가 끝나고 브라우저는 task queue에 실행 코드를 넣음. main thread는 event loop를 돌려 task queue에 작업이 있는지 체크하고 task 실행  

![image-20210810151013455](C:\Users\joo\AppData\Roaming\Typora\typora-user-images\image-20210810151013455.png)

### Callback patter n  

비동기 처리 후 실행될 코드를 Callback function으로 보내는 것  

비동기 처리가 고도화되면서 Callback hell 단점이 부각됨  

```js
function fetchUsers(onSuccess){
    return request('/users', onSuccess)
    .then(onSuccess)
    // Error handling 
    .catch(onError)
    
    // or
    return request('/users').then(onSuccess, onError)
}

 
```



### Promise  

Promise를 활용하여 비동기 처리의 순서 조작, 에러 핸들링, 여러 비동기 요청 처리 등을 쉽게 처리할 수 있게 됨. **즉 하나의  deps로 처리**  

**데이터가 떨어졌을 때 어떤 처리를 할 것인지 미리 약속하는 프록시(Proxy)** (.then, .catch, .finally 등)  [전체 정보](https://promisesaplus.com/)

```js
function fetchUsers(onSuccess){
	return request('/users').then(onSuccess)
}
```

```js
function returnPromise() {
    return new Promise((resolve, reject) => {
    setTimeout(() => {
         const randomNumber = generateRandomNumber(100)
         if (randomNumber < 50) resolve(randomNumber)
         else reject(new Error("Random number is too small."))
    	})                    
    })
}

returnPromise()
  .then(num => {
    console.log("First random number :", num)
  })
  .catch(error => {
    console.log("Error occured: ", error)  
  })
  .finally(() => {
    console.log("Promise returned.")
  })
```

Promise 객체는 pending, fulfilled, rejected 3개의 상태를 가짐, **fulfilled, rejected 두 상태를 settled 라고 지칭**  

**pending** : 비동기 실행이 끝나기를 기다리는 상태

**fulfilled** : 비동기 실행이 성공한 상태

**rejected** : 비동기 실행이 실패한 상태  

#### Multiple Promise handling  

Promise 객체는, settled 되더라고 계속 핸들러를 붙일 수 있음 (핸들러 순서대로 호출됨)

**Promise all()** :모든 프로미스가 fulfilled 되길 기다림. 하나라도 에러 발생시, 모든 프로미스 요청이 중단됨  

```js
Promise.all(
	users.map(user => request('/users/detail', user.name))
    // [Promise, Promise, Promise ...]
)

.then(console.log) // [UserNameData, UserNameData, ...]
.catch(e => console.error("하나라도 실패했습니다."))
```

**Promise.allSettled()** : 모든 프로미스가 settled 되길 기다림  

```js
// 재귀 함수임
function saveLogRetry(logs, retryNum){
    if (retryNum >= 3) return; //no more try
    
    Promise.allSettled(logs.map(saveLog))
    	.then((results) => {
          return results.filter((result) => 
          	result.status === "rejected");
    })
    	.then((failedPromises) => {
        saveLogRetry(
        	failedPromises.map((promise) => promise.reason.failedLog),
            
          	retryNum + 1
        )
    })
}
```

**Promise.race()** : 넘겨진 프로미스들 중 하나라도 settled되길 기다림  

```js
function requestWithTimeout(request, timeout = 1000){
    return Promise.race([request, wait(timeout)]).then((data) => {
        console.log("요청 성공.")
    	return data;
    })
}

requestWithTimeout(req)
	.then(data => console.log("data : ", data))
	.catch(() => console.log("타임아웃 에러!"))  
```

**Promise.any()** : 넘겨진 프로미스 중 하나라도 fulfilled 되길 기다림  

```js
function getAnyData(dataList){
    Promise.any(dataList.map((data) => request(data.url)))
      .then((data) =>{
        console.log("가장 첫 번째로 가져온 데이터 : ", data);
    })
      .catch((e) => {
        console.log("아무것도 가져오지 못했습니다.")
    })
}
```

## async/await  

promise 체인을 구축하지 않고도, **Promise를 직관적으로 사용할 수 있는 문법**  

async function을 만들고, Promise를 기다려야 하는 표현 앞에 await을 붙임  

```js
// async : 단일 await
async function fetchUsers(){
    try{
        const users = await request('/users')
        console.log("users fetched")
        return users
    } catch (e) {
        console.log("error : ", e)
    }
}

// Promise  
function fetchUsers(){
    return request('/users')
    .then(users => console.log("users fetched."))
    .catch(e => console.log("error : ", e))
}

// async : 여러 개의 await  
async function fetchUserWithAddress(id){
    try{
        const user = await request(`/user/${user.id}`)
        const address = await request(`/user/${user.id}/address`)
        return {...user, address}
    } catch (e) {
        console.log("error : ", e)
    }
}

// Error 통제  
async function fetchUserWithAddress(id) {
    try {
        const user = await request(`/user/${user.id}`)
        if (!user) throw new Erro("No user found.")
        
        const address = await request(`/user/${user.id}/address`)
        if (!address.userId !== user.id) throw new Error("No address match with user.")
        
        return {...user, address}
    } catch(e) {
        console.log("user fetch error :", e)
    }
    }
}

// async/await - Promise와의 조합  
async function fetchUserWithAddress(id){
    return await Promise.all([
        (async () => await request(`/users/${id}`))(),
        (async () => await request(`/users/${id}/address`))(),
    ])
}

fetchUserWithAddress('1234')
.then(([user, address]) => ({...user, address}))
.catch(e => console.log("Error :", e))
```

