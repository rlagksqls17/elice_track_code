## CSS란  
: Cascading Style Sheet  
: 문서의 레이아웃과 스타일 정의 
: HTML로 작성된 정보를 꾸며주는 언어  
    
## CSS 구성요소  
```css
선택자:{속성:속성값;}
```
선택자 : 디자인을 적용할 HTML 영역  
속성 : 어떤 디자인을 적용할지 정의  
속성값 : 어떤 역할을 수행할지 구체적으로 명령

## CSS와 HTML 연동 방법 3가지
**Inline Style sheet**  
태그 안에 직접 원하는 스타일을 적용  
**Internal Style Sheet**  
< style > Tag 안에 넣기  
**External Sytle Sheet**  
link로 불러오기  
      
```css
      <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>CSS 연동 방법</title>
  
  <style>
    h1 {background-color: yellow; } 
  </style> <!-- 두번째 연동방식 -->
  
  <link rel = "stylesheet" href = "index.css"> <!-- 세번째 연동방식, html과 css를 분리, 가독성 좋음-->
    
</head>
<body>
  
  <h1 style = "color: red;"> Hello World </h1> <!-- 첫번째 연동방식 -->
  
</body>
</html>
```  
      
## CSS 선택자   
: HTML의 어떤 요소에 CSS를 적용할 것인가  
      1. Type Selector : 특정 태그에 스타일을 적용  \<h2\>\{\}\</h2\>  
      2. Class Selector : 클래스 이름으로 특정 위치에 스타일을 적용 .coding\{\}  
      3. ID Selector : ID를 이용하여 스타일을 적용 #coding\{\}  
 
```  
   <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>CSS 선택자</title>
  
  <style>
      h2{
          color: red;
      }
      .bg{
          color: green;
      }
      #bg{
          color: yellow;
      }
  </style>
</head>
<body>
  
  <h2> Type Hello World</h2> <!-- 타입 선택자 -->  
  <h2 class = "bg">Class Hello World</h2> <!-- 클래스 선택자, id보다는 좀 더 작은 개념-->  
  <h2 id="bg">Id Hello World</h2> <!-- ID 선택자-->
  
</body>
</html>   
```
      
## CSS 우선순위  
      
1. 항상 나중에 적용한 코드가 우선순위가 높다.  
2. 디테일한 선택자일수록 우선순위가 높다.   
3. class는 type보다 우선순위가 높다.
4. ID는 Class보다 우선순위가 높다. 즉 ID \> Class \> Type  
      
```  
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>CSS 우선 순위</title>
  
  <style>
  
      p{
          color: red;
      }
      p{
          color: blue;
      }
      header h3{
          background-color: green;
      }
      h3{
          background-color: yellow;
      }
      .color{
          color: blue;
      }
      h4{
          color: red;
      }
      
  </style>
</head>
<body>
  
  <p>순서 캐스케이딩</p>
  <header>
      <h3>디테일 캐스케이딩</h3>
  </header>
  
  <h4 id = "color" class = "color">선택자 캐스케이딩</h4>
</body>
</html>   
```
## CSS 속성  
**width, height**: 일정 크기의 공간을 만들 수 있음  
```html
<p clsss = "paragraph"> 프로그래밍을 배워봐요! </p>  

.paragraph{ width: 500px; height: 500px; }
```

**font-** : size, family, style, weight  
```html  
<p class = "paragraph"> 즐거운 웹프로그래밍!</p>  

.paragraph{
    font-size: 50px; /*글자크기*/
    font-family: Arial, sans-serif; /*글꼴, 입력한 순서대로 우선순위 적용, 마지막에 작성하는 디폴트 값*/
    font-style: italic; /*글자 기울기*/
    font-weight: bold; /*글자 두께*/  
}
```

**border** : 테두리를 만들어 줌  
```html
<p class = "paragraph"> 즐거운 웹프로그래밍!</p>

.paragraph{
    width: 500px;
    weight: 500px;
    border-style: solid;
    border-width: 10px;
    border-color: red;
}
```  

**background** : 배경  
```html
.paragraph{
    background-color: yellow;
    background-image: url(이미지 경로);
    background-repeat: no-repeat;
    background-position: left;
}
```  


