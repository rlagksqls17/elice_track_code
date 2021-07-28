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

