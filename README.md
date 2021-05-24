# CSS
## 1. CSS의 개념
- 기본적인 HTML 구조를 스타일을 추가할 수 있어요. 
```CSS
div {
  font-size : 50px;
  color : blue;
  text-decoration : underline;
  margin : 20px;
}
```
- div라는 태그를 { } 안에서 스타일링 해주는 거예요.
- 이 div는 특정 요소를 선택하는 ___선택자___ 라고합니다.
> 선택자 { 속성 : 값 } ;
## 2. 선언 방식
### 2-1) 내장 방식
- 별도의 css 파일 없이 html 안에서 <style> 태그 안에서 사용합니다.
- 하지만.. css html js 서로 파일을 분리하는 것이 유지 보수 측면에서 좋겠죠? 권장하지 않아요.
### 2-2) 인라인 방식
```html
<div style = "color" : red;> </div>
```
- 편리해보이지만 CSS 우선순위 개념에서 인라인 방식이 너무 우선적입니다.
- 너무 지나치게 우선해서 덮어써가며 수정하고 싶어도 수정이 안되는 경우도 있어요. (유지보수가 힘들 수 있어요.)
### 2-3) 링크 방식 (병렬 방식)
```html
<link rel="stylesheet" href="./css/main.css">
```
- 링크를 통해 외부 css파일을 링크하는 방식입니다.
### 2-4) import 방식 (직렬 방식)
- html 내부에서는 👇👇👇
```html
<link rel="stylesheet" href="./css/main.css">
```
- css 내부에서는 👇👇👇 아래처럼 직렬로 연결합니다.
```css
@import url("./box.css"); // 또 다른 css 파일의 경로
```
- css가 또 다른 css파일을 부르는 구조입니다.
- main.css가 html에 연결이 되어 main.css가 box.css를 import 하기 전까지는 box.css는 html에 적용이 안 됩니다. (연결이 지연될 수 있어요.)
  
## 3. CSS 선택자
### 3-1) 기본 선택자
> 전체 선택자
```css
* {
  color : red;  
}
  ```
  - 모든 요소를 선택합니다.
  > 태그 선택자
  ```css
   li {
      color : red;
  }
  ```
  - 특정 태그 이름을 기준으로 선택합니다. 가장 기본적이죠?
  > 클래스 선택자 . 
  ```css
  .orange {
    color : red;
  }
  ```
  ```html
  <li class="orange"> 오렌지 </li>
  <div class="orange"> 오렌지 </div>
  ```
  - .이 꼭 필요합니다. 
  > 아이디 선택자 #
   ```css
  #orange {
    color : red;
  }
  ```
  ```html
  <li id="orange"> 오렌지 </li>
  ```
### 3-2) 복합 선택자
  - 기본 선택자를 조합해서 사용하는 겁니다.
  > 일치 선택자 
  - 선택자 A 와 선택자 B를 동시에 만족하는 요소 선택
  ```css
  span.orange {
    color : red;
  }
  ```
  - 태그는 span, 클래스는 orange 인 경우에 스타일 적용해!
  
  > 자식 선택자 >
  ```css
  ul > .orange {
    color : red;
  }
  ```
  ```html
  <ul>
    <li> 사과 </li>
    <li class = "orange"> 오렌지 </li>
  </ul>  
  ```
  - 부모요소가 ul인 자식 중에서 class가 oragne인 친구들만 스타일 적용해!
  
  > 하위 선택자 (띄어쓰기)
  ```css
  div .orange {
    color : red;
  }
  ```
  - 공백문자로 구분합니다.
  - div라는 태그 선택자 + class가 orange인 친구를 찾자.
  - 하위 선택자를 더 많이 사용합니다.
  
  > 인접 형제 선택자
  ```css
  .orange + li {
    color : red; 
  }
  ```
  ```html
  <ul>
    <li> 사과 </li>
    <li class = "orange"> 오렌지 </li>
    <li> 망고 </li>
    <li> 수박 </li>
  </ul>  
  ```
  - 같은 부모를 공유하는 li 태그 중 바로 **다음 형제 하나만** 골라요.
  - 신기하게도 오렌지가 아니라 망고가 선택되게 됩니다.
  
  > 일반 형제 선택자
  ```css
  .orange ~ li {
    color : red; 
  }
  ```
  ```html
  <ul>
    <li> 사과 </li>
    <li class = "orange"> 오렌지 </li>
    <li> 망고 </li>
    <li> 수박 </li>
  </ul>  
  ```
  - 같은 부모를 공유하는 li 태그 중 바로 **다음 형제 모두**를 골라요.
  - 망고와 수박이 선택됩니다.
### 3-3) 가상 클래스 선택자
  > Hover
  - **마우스 올리면 변화**를 만들 수 있어요.
  ```css
  a:hober {
    color : red;
  }
  ```
  - 마우스 커서를 a 태그 위에 올리면 빨간색으로 변하는 예제입니다.
  
  > Active
  - **마우스를 클릭하고 있는 동안 변화**를 만들 수 있어요.
    ```css
  a:active {
    color : red;
  }
  ```
  
  > Focus
  - 포커스는 가능한 요소가 일반적으로 input 요소입니다.
  - 마우스 눌렀을 때 켜집니다.
  ```css
  input:focus {
    background-color : orange;
  }
  ```
  - input 박스를 누르면 변화가 일어나요.
  - focus가 가능한 요소는 select, text area, input ... 정도가 있어요.
  - div같이 안되는 요소에는 html에서 tabindex="-1" 속성을 주면 되긴하는데 권장하지 않아요.
  
  > First Child 
  - 형제 요소 중 선택자가 첫째라면 선택합니다.
  ```css
  .fruits span:first-child{
    color : red;
  }
  ```
  - first-child 👉 형제 요소 중 첫째만 선택할건데
  - span 👉 span 태그를 가지는 친구여야하고
  - .fruit 띄어쓰기👉 fruit 클래스를 가지는 요소의 후손이여야해.
