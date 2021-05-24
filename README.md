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
  
  > Last Child 
  - first-child라 똑같지만 막내를 찾는 겁니다.
  
  > Nth Child 
  - 비슷합니다.
  ```css
  .fruits *:nth-child(2){
    color : red;
  }
  ```
  👆👆 둘째를 찾을 건데 어떤 태그든 상관없이 fruits class의 후손이면 됨.
   ```css
  .fruits *:nth-child(2n){
    color : red;
  }
  ```
  👆👆 2번째, 4번째, ... 친구들을 찾을 겁니다.
  
  > 부정 선택자
  - Not 사용
  ```css
  .fruits *:note(span){
    color :red;
  }
  ```
  👆👆 span 제외하고 fruits class 내 모든 태그들을 선택합니다.
  
  ### 3-4) 가상 요소 선택자
  > Before
  - 콜론이 두 개!
  - before라는 가상의 요소를 만들어서 class 가 덮은 요소 앞에 삽입하는 선택자입니다.
  ```css
  .box::before {
    content:"앞!";
  }
  ```
  ```html
  <div class="box">
    뒤!
  </div>
  ```
  👉 출력이 **뒤!** 가 아니라** 앞! 뒤!** 로나옵니다.
  
  > After
  - 반대 개념이겠죠?
  ```css
  .box::after{
    content: "";
    display: block;
    width :30px;
    height :30px;
    background :royalblue;
  }
  ```
  - content는 필수로 써야합니다.
  - inline 방식이라 width,hegiht,background가 적용이 안됩니다.
  👉 ```css display: block; ```   속성을 추가하면 적용이 됩니다.
  
  ### 3-5) 속성 선택자
  > 속성만으로 찾기
  ```css
  [disabled] {
    color : red;
  }
  ```
  - disabled 라는 속성을 가진 태그들을 선택합니다.
   ```css
  [type] {
    color : red;
  }
  ```
  - type 이라는 속성을 가진 태그들을 선택합니다.
  > 속성= "값" 
   [type="password"] {
    color : red;
  }
  ```
  ❗️ 태그 없이도 속성,값으로 스타일을 적용시킬 태그들을찾을 수 있어요.
  
  
  ## 4. 스타일 상속
  - class에 스타일을 적용하면 class 하위 요소까지 상속되어 적용됩니다.
  ❗️ **글자/문자 관련 속성들이 대부분 상속됩니다.**<br>
  ### 4-1) 강제 상속 
  - css에서 attribute의 값을 inherit로 주면 됩니다.
  - inherit을 주면 원래 안되는 width, height, .... 같은 속성들도 부모의 것을 그대로 가져 옵니다.
  👇👇 부모 값이 바뀌면 따라서 바뀌어요.
  ```css
  .parent {
  width: 300px;
  height :400px;
  background-color:orange;
  }
  .child {
    width:100px;
    height: inherit;
    background-color : orange;
  }
  ```
  
  ## 5. 선택자 우선순위
  - 어떤 CSS 속성을 먼저 적용을 해줘야할까요?
  1. 점수 높은 선언부터!
  2. 점수 같으면 마지막에 해석된 선언이 우선!<br>

❗️❗️❗️ 우선순위 파악이 생각보다 어렵습니다!
|속성|점수|코드|
|:---:|:---:|:---|
|!important|99999999점| ```css color : red !important ```
|직접 명시 (inline 선언 방식)|1000점|```css <div  ```|
|ID 선택자|100점|```css #color_yellow { ... }  ```|
|class 선택자|10점|```css .div { ... } ```|
|태그 선택자|1점|```css div { ...} |
|전체 선택자|0점|*|
|상속|0점|```css body {...} ```|
<br>
  
![image](https://user-images.githubusercontent.com/32920566/119309432-43ec8100-bca9-11eb-9d66-96ad48355c65.png)
