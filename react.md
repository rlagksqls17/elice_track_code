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

## jsx  

특징 

HTML 태그 내에 Javascript 연산 

class = 대신 className = 

### 중괄호 ({})

jsx 중괄호 안에는 여러 **자바스크립트 표현식**을 사용 가능  

```jsx
const expression = 3*5
const element = <h1>3*5= {expression}</h1>;
```

###  **스타일은 object로 {{ }}**  

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

###  **최상단 element는 반드시 하나**   

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

## Component   

: React에서 페이지를 구성하는 최소단위 

: Component의 이름은 대문자로 시작 

### 1. Class Component

```jsx
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

### 2. Function Component

```jsx
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
```

4. Controlled Component/Uncontrolled Component 

### 컴포넌트 합성  

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

## props  

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

## state

컴포넌트 내에서 유동적으로 변할 수 있는 값을 저장

**1. Props와 state를 이용한 클래스 컴포넌트 지정**

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

**2. 일반 인수를 이용한 State**

```jsx
// onClickEventHandler() 메소드가 호출되면 State의 name 데이터가 "엘리스 토끼"로 변경됨
onClickEventHandler = () => {
  this.setState({
    name: "엘리스 토끼"
  });
};
```



## Hook

**1. Hook : state와 event를 활용한 동적 렌더링**

```jsx
// const [<상태 값 저장 변수>, <상태 값 갱신 함수>] = userState(<상태 초깃값>);
import {useState} from 'react';

function Example(){
    // hook의 이름은 use로 시작
	const [inputValue, setInputValue] = 
          useState("defaultValue");
    const handleChange = (event) => {
        setInputValue(event.target.value);
    }
    return(
    	<div>
        	<input onChange = {handleChange}
                defaultValue = {inputValue}>
            </input>
            입력값 : {inputValue}
        </div>
    )
    
}
```

**2. Hook : object를 이용한 State**  

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

**3. Hook : object+ state + event**  

```jsx
const App = () => {
    const [user, setUser] = useState({ 
    	name: "민수",
        school: "엘리스대학교"
    });
    
    const handleChange = (event) => {
        const {name, value} = event.target;
        const newUser = {...user};
        newUser[name] = value;
        setUser(newUser);
    };
    
    return(
    	<div>
        	<input name = "name" 
                onChange = {handleChange}
                value = {user.name}>
            </input>
            <input name = "school"
                onChange = {handleChange}
                value = {user.school}>
            </input>
        </div>
    )
}
```

**4. 나만의 훅**

```jsx
const useUser = () => {
  // useState()를 이용해 state 변수를 만드세요.
  const [nickname, setNickname] = useState('')

  const updateNickname = event => {
    const nickname = event.target.value

    setNickname(nickname)
  }

  return [nickname, updateNickname]
}

const User = () => {
  // React Hook을 호출하세요.
  const [nickname, setNickname] = useUser('')

  return (
    <div>
      <label>{nickname}</label>
      <input value={nickname} onChange={setNickname} />
    </div>
  )
}
```

 

### Hook의 규칙  

- 최상위에서만 Hook 호출    

: 반복문, 조건문, 중첩함수 내에 Hook 호출 금지  

: 따라서 React가 useState()와 useEffect()가 여러 번 호출되는 중에도 Hook의 상태를 올바르게 유지할 수 있도록 해줘야 함  

- 오직 React 함수 내에서 Hook을 호출해야 함  
- 또는 나만의 hook에서 hook 호출 가능

: 함수 컴포넌트에서만 Hook 호출  

> Hook 호출 순서에 React가 의존함



## Effect Hook  

함수형 컴포넌트에서 side effects들을 실행하는 것  

```jsx
import { useEffect } from 'react';
// EffectCallback : Deps에 지정된 변수가 변경될 때 실행할 함수
// Deps : 변경을 감지할 변수들의 집합  
const App = () => {
    useEffect(EffectCallback, [Deps?])
}
// Deps에 아무것도 안 넘겨주면 컴포넌트의 생성과 소멸 시에만 Effect Callback 함수가 호출됨
// useEffect의 이펙트 함수 내에서 다른 함수를 return 할 경우 state가 변경되어 컴포넌트가 다시 렌더링되기 전과 컴포넌트가 없어질 때 호출할 함수를 지정하게 됨
const App = () => {
    
    useEffect(() => {
        console.log("컴포넌트 생성");
        
        return () => {
            console.log("컴포넌트 소멸");
        }
    }, 
    []);
    return <div></div>
}
```



React 컴포넌트 안에서 **데이터를 가져오거나 구독하고, DOM을 직접 조작하는 작업을 side effects라고 함**. 이러한 과정은 다른 컴포넌트에 영향을 줄 수도 있어 렌더링과정에서는 구현불가  

Effect Hook의 useEffect()는 함수형 컴포넌트 내에서 이런 side effects를 수행할 수 있게 해줌  

즉 지정한 State나 Prop가 변경될 때마다 이펙트 콜백 함수가 호출됨

버튼 클릭 대마다 1씩 카운트를 하는 카운터 컴포넌트에서 매 렌더링, State 업데이트 시에 count를 갱신하고 싶을 때  

**componentDidMount()** 와 **componentDidUpdate()**를 사용  

```jsx
import React, { useState, useEffet } from 'react';

const Example = () => {
    const [count, setCount] = useState(0);
    // 모든 렌더링 요소마다 원하는 작업 수행 가능하여 
    // 코드 중복할 필요가 없음
    // 생명주기 메소드 사용할 필요 없음
    // EffectCallback : Deps에 지정된 변수가 변경될 때 실행할 함수
// Deps : 변경을 감지할 변수들의 집합
    useEffect() => {
        document.title = `You cheked ${count} times`, count
    }
    
    return(
    	<div>
        	<p> you clicked {count} times </p>
            <button onClick={() => setCount(count + 1)}> Click Me</button>
        </div>
    )
}
```

## useMemo  

지정한 State나 Props가 변경될 경우 해당 값을 활용해 계산된 값을 메모이제이션 하여 제 랜더링 시 불필요한 연산을 줄임

```jsx
import React, {useState, useMemo} from 'react';

// 지속적으로 메모리를 쓰기 때문에 성능하락 이슈가 있을 수 있음
const App = () => {
    const [firstName, setFirstName] = useState('철수')
    const [lastName, setLastName] = useState('김')
    
    const fullName = useMemo(() => {
        return `${firstName} ${lastName}`
    }, [FirstName, lastName])
}

```

## useCallback  

함수를 메모이제이션하기 위해 사용하는 Hook이다. 컴포넌트가 재렌더링될 때 불필요하게 **함수가 다시 생성되는 것을 방지**한다. 

**시간이 걸리는 Return**  

```jsx
// 지속적으로 메모리를 쓰기 때문에 성능하락 이슈가 있을 수 있음
const App = () => {
    const [firstName, setFirstName] = useState('철수')
    const [lastName, setLastName] = useState('김')
    
    // 이름과 성이 바뀔 때마다 풀네임을 return하는 함수를 메모이제이션  
    const getFullName = useCallback(() => {
        return `${firstName} ${lastName}`
    }, [firstName, lastName])
    
    return <>{getFuallName()}</>
}
```

### Promise  

resolve : 로직이 성공 시 실행하면 fulfilled(이행) 상태가 되게 해주는 callback함수임  

reject : 로직이 실패하였을 때 실행하면 rejected 상태가 되게 해주는 callback 함수임

```jsx
function getUser(id) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log("Reading from a database....");
			if(id !== 1){
				reject("User not found!");
			}
      resolve({ id: id, username : "test" });
    }, 2000);
  });
}


getUser(1)
	.then((user)=>{
		console.log(user);
	})
	.catch((e)=>{
		console.error(e);
	});
```

## Async/Await  

es6에서 나온 개념  

then을 통한 chaining 제거  

promise 반환하는 함수 앞에 await을 명시  

async함수는 항상 promise 함수 반환  

```jsx
// 제일 문제가 없음
function getUser(id) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log("Reading from a database....");
			if(id !== 1){
				reject("User not found!");
			}
      resolve({ id: id, username : "test" });
    }, 2000);
  });
}

function updateUser(username) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log("Update User");
			if(username !== "test"){
	      reject(new Error("Error occured in repositories"));
			}
			resolve({id:1,username:"test2"});
    }, 2000);
  });
}

async function delayGetUser() {
	try {
		const user = await getUser(1);
		const updatedUser = await updateUser(user.username);
		console.log(updatedUser);
		return updatedUser;
	} catch(err){
		console.log(`Error : ${err.message}`);
	}
}

async function main(){
	const user = await delayGetUser();
	console.log(user);
}
```



## useRef  

컴포넌트 생애 주기 내에서 유지할 ref 객체를 반환

ref 객체가 변경이 되더라도 다시 렌더링하지 않게 하도록 함

```jsx
const App = () => {
    const inputRef = useRef(null)
    const onButtonClick = () => {
        inputRef.current.focus()
    }
    return (
    	<div>
        	<input ref = {inputRef} type = "text">
            	<button onClick = {onButtonClick}>
                    input으로 포커스
                </button>
            </input>
        </div>
    )
}
```







## Element

엘리멘트란 React 앱의 가장 작은 단위를 말함  

### Render 와 ReactDOM

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

## axios  

```jsx
// 동기방식
axios.get('request url')
	.then(
	(response) => {
     	console.log("받아온 데이터", response.data)   
    })

// 비동기방식
axios.get('request url', {post 요청에 보낼 객체})
	.then(
	(response) => {
     console.log("받아온 데이터", response.data)   
    })
```





## 이벤트  

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

### 이벤트 등록

**1. 함수형 컴포넌트에 이벤트 정의**  

예제코드 1 : onClick

```jsx
function ActionLink(){ // 컴포넌트
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
```

예제코드 2: onChange, event.target.value 

```jsx
const App =() =>{
    const handleChange = (event) =>{
        console.log(event.target.value + "라고 입력")
    }
	return (
		<div>
    		<input onChange = {handleChange} />
    	</div>
		)
}
```



**2. 클래스형 컴포넌트에 이벤트 정의 (props 포함)**  

```jsx
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
```

**3. 클래스인데 props 따로 지정 안할 시 유용한 코드** 

```jsx
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

**4. 함수 안에 이벤트 등록**

```jsx
 <button onClick={
        () => {
            alert(this.state.message)
            this.setState({
                message : ''
            })
        }
    }>
</button>
```

### 인수 전달후 이벤트 등록

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
  const handleClick = (data) => {
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

### 상위 컴포넌트에 이벤트 등록  

```jsx
// props로 onchange 함수 등록  
const MyForm = ({ onChange }) => {
    return(
    	<div>
        	<span>이름: </span>
            <input onChange={onChange} />
        </div>
    )
}

// 상속 주는 컴포넌트  
// props도 가능 
const App = () => {
    const [username, setUsername] = useState('')
    return (
    	<div>
        	<h1>
            	{username}님 환영합니다.
            </h1>
            <MyForm 
                onChange = {(event) => {
                    setUsername(event.target.value)
                }} />
        </div>
    )
}
```



## 조건부 렌더링  

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
// 예제코드 2
    <div className="App">
        <button onClick={() =>
        {
            toggle();
        }}>
            {isOn ? "켜짐" : "꺼짐"}
        </button>
    </div>
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

## 기타  

### form과 props 이용한 등록과 초기화 구현

```jsx
//// App.js  
import React, { useState } from 'react';
import InsertForm from "./components/InsertForm";
import ListView from "./components/ListView";

function App() {
  const [todoList, setTodoList] = useState([]);
  
  const handleInsert = (value) => {
    setTodoList((current) => {
      const newList = [...current];
      newList.push({
        key: new Date().getTime(),
        value,
        isCompleted: false,
      });
      return newList;
    })
  }
  
  const handleComplete = (index) => {
    setTodoList((current) => {
      const newList = [...current];
      newList[index].isCompleted = true;
      return newList;
    })
  }
  
  const handleRemove = (index) => {
    setTodoList((current) => {
      const newList = [...current];
      newList.splice(index, 1);
      return newList;
    })
  }
  
  return (
    <div className="App">
        <ListView todoList={todoList} onComplete={handleComplete} onRemove={handleRemove} />
        <InsertForm onInsert={handleInsert} />
    </div>
  );
}

export default App;


//// InsertForm.js
import React, { useState, useCallback } from "react";

const InsertForm = ({ onInsert }) => {
    const [inputValue, setInputValue] = useState("");
    const handleSubmit = useCallback((event) => {
        event.preventDefault(); // 기본적인 HTML 동작으로 인해 페이지가 새로고침 되는 것을 방지
        if(typeof onInsert === "function" && inputValue) { // onInsert가 정상적인 함수인 지 확인하여 에러 방지
            onInsert(inputValue);
        }
        setInputValue("");
    },[onInsert, inputValue])

    return (
        <form onSubmit={handleSubmit}>
            <input value={inputValue} onChange={(event) => {
                setInputValue(event.target.value);
            }} />
            <button type="submit">등록</button>
        </form>
    )

}

export default InsertForm;

// ListView.js
import React from "react";

const ListView = ({todoList, onComplete, onRemove}) => {
  return (
    <div>
      <ol>
        {todoList.map((item, index) => {
          return (
            <li key={item.key}>
              <span>{item.value}</span>
              <button type="button" onClick={() => {
                if(typeof onComplete === "function") {
                  onComplete(index);
                }
              }}>완료</button>
              <button type="button" onClick={() => {
                if(typeof onRemove === "function") {
                  onRemove(index);
                }
              }}>삭제</button>
            </li>
          );
        })}
      </ol>
    </div>
  )

}

export default ListView;
```

### CSS 추가  

```jsx
import React, { useState, useCallback } from "react";

const InsertForm = ({ onInsert }) => {
    const [inputValue, setInputValue] = useState("");
    const handleSubmit = useCallback((event) => {
        event.preventDefault(); // 기본적인 HTML 동작으로 인해 페이지가 새로고침 되는 것을 방지
        if(typeof onInsert === "function" && inputValue) { // onInsert가 정상적인 함수인 지 확인하여 에러 방지
            onInsert(inputValue);
        }
        setInputValue("");
    },[onInsert, inputValue])

    return (
        <form onSubmit={handleSubmit} style={{
            baackgroundColor: "#ffffff",
            borderRadius: 16,
            marginBottom: 16,
            display: "flex",
            justifyContent: "space-between",
            alignItems: "center"
        }}>
            <input value={inputValue} onChange={(event) => {
                setInputValue(event.target.value);
            }} style={{
             flex: 1,
             border: "none",
             color: "#000000",
             padding: "6px 12px",
             backgroundColor: "transparent"
            }}/>
            <button type="submit" style={{
                border: "none",
                borderRadius: 16,
                backgroundColor: "#3ab6bc",
                color: "#ffffff",
                cursor: "pointer",
                padding: "8px 16px"
            }}>등록</button>
        </form>
    )

}

export default InsertForm;

```

### SPA  

하나의 페이지 요청으로 전체 웹앱을 사용하는 방식  

SPA는 서버에 매번 요청을 하지 않고, 단 한 번만 페이지를 받아 페이지 관련 네트워크 요청이 줄어든다.

SPA는 단 하나의 페이지를 관리하며, 모든 라우트에서 해당 페이지를 내려주는 방식이다.

SPA는 모바일 앱을 사용하는 듯한 경험을 주기 위해 자바스크립트와 History API 등의 Web API를 이용, 페이지 리로드 없는 네비게이션을 구현한다.

SPA는 페이지 요청 시 주로 빈 페이지를 전송하므로, 서버에서 모든 페이지 정보를 렌더링하는 방식의 MPA보다는 Search Engine Optimization에 불리하다.

### MPA 

서버에 미리 여러 페이지를 두고 유저가 네비게이션 시 요청에 적합한 페이지를 전달

### react-router  

**설명**

Declarative routing for React

React의 JSX를 이용하거나, History API를 사용하여 라우팅을 구현

웹에서는 react-router-dom을 사용  

적용 시, 서버의 모든 path에서 같은 앱을 서빙하도록 해야 함. React 컴포넌트를 특정 path와 연결하면, 해당하는 path로 진입 시 컴포넌트를 렌더링 하게 함.  

query, path variable 등 URL parameter를 얻어 활용함  

조건에 맞지 않을 경우 redirect함  

페이지 이동 시 이벤트 핸들러를 등록함  

/posts/my-post-1 등의 nested route를 구현함  

**사용법**  

#### BrowserRouter 컴포넌트

\<BrowserRouter\>로 감싸 Router Context를 제공해야 함  

HTML5의 History API를 사용하여, UI와 URL의 싱크를 맞추는 역할

#### Route 컴포넌트

**path와 컴포넌트를 매칭함**

Link로 특정 페이지로 이동 시 리로드 없이 페이지가 이동함  

Switch로, 매칭되는 라우트 하나를 렌더링하게 함

#### Redirect 컴포넌트  

Link와 비슷하나 렌더링 되면 to prop으로 지정한 path로 이동함  

Switch 안에서 쓰일 경우 from, to를 받아 이동하게 만듦

#### Link, NavLink 컴포넌트  

to prop을 특정 URL로 받아, 클릭 시 네비게이션 함  

anchor tag를 래핑함  

NavLink의 경우, 매칭 시 어떤 스타일을 가질지 등의 추가 기능이 있음  

to에 location object나 함수를 받을 수 있음

#### useHistory, useLocation, useParams, useRouteMatch  

최상위 컴포넌트가 아니더라도, hook으로 react-router 관련 객체에 접근할 수 있음, history, location, params, match 객체에 접근함

```jsx
import { BrowserRouter, Route, Switch } from 'react-router-dom'  
export function App(){
    return(
    	<BrowserRouter>
        	<Switch>
            	<Route path="/about"><AboutPage/></Route>
                <Route path="/contact"><AboutPage/></Route>
                // 홈페이지는 항상 밑에 두기
                // Switch는 가장 위의 매칭되는 path의 컴포넌트를 렌더링한다.
                <Route path="/"><AboutPage/></Route>
            </Switch>
        </BrowserRouter>
    )
}
```

#### private Route  

특정 조건이 충족되지 않았을 때 다른 페이지로 Redirect하도록 하는 기능, 유저의 상세페이지, 개인정보 변경 페이지 등을 만들 때 사용됨  

```jsx
// 누가 보면 안되기 때문에 PrivateRoute로 감싸줌
function PrivateRoute({component: Component, ...props}){
    return <Route {...props} render = {props => {
            // !! 는 유효한 값인지 확인
            const isLoggedIn = !!getUserInfo()
            
            if (!isLoggedIn){
                return <Redirefct to="/login" />
            }
            return <Component {...props} />
        }}
}
```

#### query string 활용하기  

```jsx
function ContactPage(){
    const location = useLocation();
    const searchParams = new URLSearchParams(location.search);
    const email = searchParams.get("email")
    const address = searchParams.get("address")
    
    return (
    	<PageLayout header = "Contact Page">
        	<em>{email}</em>
            <br />
            <strong>{address}</strong>
        </PageLayout>
    )
}
```

```python
/*
위치포인트를 0에서 시작
    거리를 담은 사전을 준비해둠
    {
        1: 1
        3: 3
        7: 7
        10: 10
        11: 11
    }
    
    while(위치포인트 1에서 끝까지)
        위치포인트가 사전의 key값보다 작은값들은 모두 1씩 감소
        위치포인트가 사전의 key값보다 큰값들은 모두 1씩 증가
        이후 사전의 값의 sum 값을 구해서 최솟값을 갱신
    
*/
```

