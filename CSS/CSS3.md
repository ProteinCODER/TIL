# CSS3

h1 {color: red;} 

- h1 = 선택자

- color= 스타일 속성
- red; = 스타일 값

`h1 태그의 color 스타일 속성에 스타일 값으로 red를 적용합니다`



## 1. 기본선택자

####  1) 전체 선택자

- ``` html
  <head>
      <style>
          * {color: red;}
      </style>
  </head>
  ```

- 전체 선택자를 통해 모든 태그의 color 스타일 속성을 red 값으로 변경

####  2) 태그 선택자

- ``` html
  <head>
      <title>CSS3</title>
      <style>
          h1 {color :red;}
          p {color : blue;}
      </style>
  </head>
  ```

- 태그 선택자를 통해 각 태그별 색상 변경 가능

- ``` html
  <style>
      body,p,h1,h2,h3,h4,h5,h6 {margin:0;padding0;}
  </style>
  ```

- 선택자를 여러 개 입력해 적용할 때 쉼표를 사용

####  3) 아이디 선택자

- ```html
  <head>
      <style>
          #headeer {
              width: 800px; margin:0 auto;
              background: red;
          }
          #wrap {
              width: 800px; margin:0 auto;
              overflow: hidden;
          }
          #aside {
              width: 200px; float: left;
              background: green;
          }
          #content {
              width: 600px; float:left;
              background:yellow;
          }
      </style>
  </head>
  <body>
  	<div id="header">
  		<h1>#header 태그</h1>
  	</div>
  	<div id="wrap">
  		<div id="aside">
  			<h1>#aside 태그</h1>
  		</div>
  		<div id="content">
  			<h1>#content 태그</h1>
  		</div>
  	</div>
  </body>
  ```

- 웹 페이지 내부에서 id 속성 중복해서는 안된다

####  4) 클래스 선택자

- 클래스 선택자는 특정한 클래스가 있는 태그를 선택할 때 사용

- ``` html
  <head>
      <style>
          .select {color: red;}
      </style>
  </head>
  <body>
  <ul>
       <li class="select">배</li>
       <li>감</li>
       <li class="select">사과</li>
       <li>당근</li>
  </ul>
  </body>
  
  ```

- 클래스 선택자 여러 개도 가능

- ``` html
  <head>
      <style>
          .item {color: red;}
          .header {background-color:blue;}
      </style>
  </head>
  <body>
      <h1 class ="item header">    <!-- item 공백 header로 여러개 사용 가능-->
          이 태그는 푸른 배경에 빨간 글씨가 나옵니다. 
      </h1>
  </body>
  ```

#  

## 2. 속성 선택자

| 형태            | 설명                                           |
| --------------- | ---------------------------------------------- |
| 선택자[속성]    | 특정한 속성이 있는 태그 선택                   |
| 선택자[속성=값] | 특정한 속성 내부 값이 특정 값과 같은 태그 선택 |

- input 태그는 이름은 같지만 type 속성에 따라 형태가 다르기 때문에 속성 선택자를 많이 사용

- ``` html
  <head>
      <style>
      input[type="text"] {background: red;}
      input[type="password"] {background: blue;}
      </style>
  </head>
  <body>
      <form>
          <input type="text">
          <input type="password">
      </form>
  </body>
  
  ```



## 3. 후손선택자와 자손선택자

####  1) 후손 선택자

| 형태            | 설명                             |
| --------------- | -------------------------------- |
| 선택자A 선택자B | 선택자A의 후손인 선택자 B를 선택 |



- #header 아래 h1 태그, #section 아래 h1 태그 색깔 넣기

- ``` html
  <head>
      <style>
          #header h1 {color: red;}
          #section h1 {color: blue;}
      </style>
  </head>
  ```



####  2) 자손 선택자

| 형태                | 설명                            |
| ------------------- | ------------------------------- |
| 선택자 A > 선택자 B | 선택자 A의 자손인 선택자 B 선택 |

- 바로 아래있는 `자손`에만 적용되는 것 자손 아래있는 `후손`은 적용안됨.

- ``` html
  <head>
      <style>
          #header > h1 {color:red;}
          #section >h1 {color:orange;}
      </style>
  </head>
  ```

- table 태그 요소는 자손 선택자 비추천(tbody도 추가해야함)

- ``` html
  <head>
          <style>   
              table > tbody >tr >th {
                  color: red;
              }
          </style>
  </head>
  ```



## 4. 반응 상태 구조 선택자

####  1) 반응 선택자

- 반응 선택자는 사용자 반응으로 생성되는 특정한 상태를 선택

- ``` html
  <head>
      <style>
          h1:hover {color: red;}  <!-- 사용자가 마우스 커서를 갖다댔을때-->   
          h1:active {color: blue;} <!-- 사용자가 마우스로 클릭했을 때-->
      </style>
  </head>
  ```

####  2) 상태 선택자 

- 상태 선택자는 입력 양식의 상태를 선택할 때 사용

| 형태      | 설명                     |
| --------- | ------------------------ |
| :checked  | 체크 상태의 input 태그   |
| :focus    | 포커스를 맞춘 input 태그 |
| :enabled  | 사용가능한 input 태그    |
| :disabled | 사용 불가능한 input 태그 |

- ``` html
  <head>
      <style>
          /* input 태그 사용가능할 때 background color 속성에 white 키워드 적용*/
          input:enabled {background-color: white;}
      </style>   
  </head>
  ```

####  3) 구조 선택자

- 구조 선택자는 특정한 위치에 있는 태그를 선택할 때 사용
- 수열의 결과 값에 해당하는 위치에 있는 태그에 스타일을 적용

| 형태            | 설명                                               |
| --------------- | -------------------------------------------------- |
| :first-child    | 형제관계에서 첫 번째로 등장하는 태그 선택          |
| :last-child     | 형제관계에서 마지막으로 등장하는 태그 선택         |
| :nth-child      | 형제관계에서 앞에서 수열 번째로 등장하는 태그 선택 |
| :nth-last-child | 형제관계에서 뒤에서 수열 번째로 등장하는 태그 선택 |





----

# CSS3 단위

####  1. 키워드 단위

- W3C에서 미리 정의한 단어, 키워드를 스타일 값으로 입력하면 키워드에 해당하는 스타일이 자동으로 적용

####  2. 크기 단위

- CSS3에서 가장 많이 사용하는 단위

- | 종류 | 설명                      |
  | :--- | ------------------------- |
  | %    | 백분율 단위 (상대적 지정) |
  | em   | 배수 단위 (상대적 지정)   |
  | px   | 픽셀 단위 (절대적 지정)   |

####  3. 색상 단위

- RGB: RED GREEN BLUE
- RGBA: RED GREEN BLUE ALPHA (알파값은 투명도를 나타냄0.0[완전투명]~1.0)
- HEX: RGB 색상 조합을 16진수로 나타낸 것. #000000

####  4. URL 단위

- 이미지나 글꼴 파일 불러오기



---

# CSS 속성

####  1. 박스 속성

- 박스 속성은 웹페이지의 레이아웃을 구성할 때 가장 중요

| margin  | 테두리와 다른태그 사이의 테두리 바깥쪽 여백                  |
| ------- | ------------------------------------------------------------ |
| border  | 테두리                                                       |
| padding | 테두리와 글자 사이의 테두리 안쪽 여백, 배경색은 padding 영역까지만 적용 |
| width   | 글자를 감싸는 영역의 가로 크기                               |
| height  | 글자를 감싸는 영역의 세로 크기                               |

- width 와 height  속성
  - 글자를 감싸는 영역의 크기 지정	
- padding 속성
  - 테두리와 글자 사이 간격 지정
  - 테두리 바깥 쪽 여백 지정
- margin 속성
  - 테두리와 다른 태그 간격 지정

   <b><width와 height 속성 적용 예제></b>

- ``` html
  <head>
      <style>
          div {
              width: 100px; height: 100px;
              background-color: red;
          }
      </style>
  </head>
  ```

<b>  <margin과 padding 속성 적용 예제></b>

- ``` html
  <head>
      <style>
          div {
              width: 100px; height: 100px;
              background-color: red;
              border: 20px; solid balck;
              margin: 10px; padding:30px;
          }
      </style>
  </head>
  ```

<b><네 방향 속성 지정하기 예제></b>

- ``` html
  <head>
      <style>
          div {
              width: 100px; height: 100px;
              background-color: red;
              /*위 오른쪽 아래 왼쪽 */
              margin: 0 30px 0 30px;
              padding: 0 30px 0 30px;
          }
      </style>
  </head>
  ```

####   1) 박스 테두리

- 테두리 두께: border-width 속성

- 테두리 형태: border-style 속성

- 테두리 색상: border-color 속성

- 테두리 둥글게: border-radius

- ``` html
  <head>
      <style>
          .box {
              border: thick dashed black;
          }     /* 테두리 두께 형태 색상 지정 */
      </style>
  </head>
  ```



####  2. 가시 속성

- 태그가 화면에 보이는 방식을 지정하며, 대표적으로 display 속성이 있다.

- | 키워드       | 설명                            |
  | ------------ | ------------------------------- |
  | none         | 화면에 보이지 않음              |
  | block        | 블록 박스 형식으로 지정         |
  | inline       | 인라인 박스 형식으로 지정       |
  | inline-block | 블록과 인라인의 중간형태로 지정 |

- 

