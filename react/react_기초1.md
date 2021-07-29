## SPA (Single Page Application)  

**전통적인 페이지**  
최초에 서버로부터 HTML을 전달 받고 페이지의 변경이 필요할 때 다시 서버에 요청하여 HTML을 전달받음  
: 이 과정에서 페이지를 처음부터 다시 불러옴  

**SPA**  
최초에 서버로부터 HTML을 전달 받고 페이지의 변경이 필요할 때 변경이 필요한 부분을 **JSON으로 전달***받는다.  
: 즉 변경된 부분만 계산하여 다시 그리게 됨  

특징 1  
: React에서 서비스를 개발하는 데 있어 독립적인 단위로 쪼개어 구현 
: component는 Hook과 함께 개발자의 생산성과 코드의 재사용성을 높임  

특징 2  
**virtual DOM**  
: 가상적인 표현을 메모리에 저장하고 ReactDOM과 같은 라이브러리에 의해 실제 DOM과 동기화하는 프로그래밍 개념  

특징 3  
**JSX**  
: JavaScript 내에서 UI를 작성하기 위해 개발자에게 익숙한 환경을 제공, HTML과 유사함  

## React 특징 분석하기  
**컴포넌트**  
: 하나의 블록을 만들어서 필요한 곳에 조립하게 됨  

**State**  
: 컴포넌트 내에서 State를 이용하여 데이터를 유동적으로 관리함.  
: State가 변경될 때마다 컴포넌트가 다시 렌더링 됨  

## Create React App (CRA)  
: React 프로젝트를 손쉽게 생성할 수 있도록 도와주는 Boilerplate  
: 수많은 React 용 보일러 플레이트가 있지만 Facebook에서 직접 만들어서 관리하는 Create React App이 가장 많이 쓰임  
: 프로젝트 생성에 필요한 다양한 기능을 Command로 제공  

장점  
1. 개발자가 온전히 React App 개발에 집중할 수 있도록 함  
: 상대적으로 덜 중요한 코드는 노출되지 않음  
: 강력한 Command 지원  

2. 모든 브라우저에서 해석될 수 있도록 transcompile 지원  
: Babel (transcompile 라이브러리 중 가장 유명)  
: 배포 시 코드 번들링  
: Webpack   

3. **Server-side Rendering 지원**    

## Node.js  
: 주로 서버 프로그래밍에 사용되는 JavaScript 기반의 소프트웨어 플랫폼  
: 2009년 발표, 2021년 기준 v16까지 업데이트  
: 프론트엔드 개발자의 접근성 높아짐  
: HTTP 통신 관련 라이브러리 내장  
: NPM을 통한 방대한 라이브러리 제공  
: Create React App으로 프로젝트 생성 시 개발 환경 및 테스트 서버로 이용됨  

## NPM 
: Node.js 환경에서 사용하는 각종 패키지들을 관리하는 저장소  
: Node.js 설치 시 함께 설치됨  
: 패키지 관리 뿐만 아니라 서버 실행 및 관리에 필요한 다양하고 편리한 명령어 제공  
: 우리가 사용할 React와 관련된 모듈들이 NPM에서 배포되고 있음  

## React 디렉토리 구조 살펴보기  
./node_modules/  
: npm을 이용해 설치한 패키지들 모음  

./public  
: 정적인 파일들을 모아놓는 곳  

./src/  
: 리액트 개발을 위한 파일들을 모아 놓는 곳  

./.gitignore  
: Git을 이용할 경우 불필요한 파일을 무시할 수 있도록 하는 설정파일  

./package.json  
: 프로젝트에 관한 정보와 사용하는 패키지들을 명세하는 파일  

./README.md  
: 내 프로젝트에 관한 설명을 작성하는 파일  

## 라이브러리 설치와 사용  
npm install <패키지 명> 을 적음으로써 설치 가능  
yarn은?  

```js  
// CSS나 import 하는 것 만으로 역할을 하는 라이브러리인 경우 패키지 명을 바로 import
import "패키지명"  

// 기본적으로 패키지를 불러와 활용할 때에는 할당할 이름을 작성  
import something from "패키지명"  

// 패키지 내의 일부 메소드나 변수만 가져올 때는 구조분해를 하여 가져옴  
import {a, b} from "패키지명"  

// 패키지에 default로 export 되는 객체가 존재하지 않을 경우 * as 이름으로 불러옴
import = as something from "패키지명"

// 별도의 CSS 파일을 작성 후 프로젝트에 적용하고 싶은 경우 사용  
import "./App.css"
```

## JSX  
: 함수 호출과 객체 생성을 위한 문법적 편의를 제공하는 JavaScript의 확장  
: HTML과 비슷하게 생겼으나 JavaScript이고 HTML과 다른 부분이 있음  

장점   
1. 개발자 편의성 향상  
2. 협업에 용이, 생산성 향상  
3. 문법 오류와 코드량 감소  

특징  
1. HTML 태그 내에 Javascript 연산  
2. class = 대신 className =  
3. 스타일은 object로  {{ }}
4. 닫는 태그 필수  />
5. 최상단 element는 반드시 하나  

## Component   

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
// class Component
class Hello extends Component{
    render(){
        const {name} = this.props
        return <div>{name}님 안녕하세요.</div>
    }
}

// Function Component => 주로 사용
const Hello = (props) => {
    const {name} = props
    return <div>{name}님 안녕하세요.</div>
}
```

4. Controlled Component/Uncontrolled Component 

 ## ReactDOM  

DOM(Document Object Model) : 객체지향 모델을 통해 구조화된 문서를 표현  

**React는 실제 DOM을 추상화하여 가상 DOM에 만들어두고, 데이터가 업데이트 되면 한번에 렌더링함**
