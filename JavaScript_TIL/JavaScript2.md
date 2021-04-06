

# 문서 객체 모델



##  1. 문서 객체 모델의 기본 용어와 개념

>  `문서객체`: HTML 태그를 자바스크립트에서 사용할 수 있는 객체로 만든 것
>
>  `문서 객체를 조작하다`= 태그를 조작한다



- 웹페이지를 처음 생성할 때, HTML 태그로 적힌 문서 객체를 생성하는 것  = `정적생성`
- 웹페이지를 실행 중에 자바스크립트를 사용해 문서 객체를 생성하는 것 = `동적생성`

---

#### -  웹페이지 실행 순서

- 위쪽에서 아래쪽으로 실행

  ``` html
  <!--<이벤트 사용>--> 
  <head>
      <script>
       window.onload= function() {
           //h1 태그 배경 색상변경
           document.querySelector('h1').style.backgroundColor='red' ;
           //h2 태그 글자 색상 변경
           document.querySelector('h2').style.color='red';
       };
      </script>
   </head>
   <body>
       <h1>Process- 1</h1>
       <h2>Process- 2</h2>   
   </body>
  ```

  



##  2. 문서 객체 선택

> 이미 존재하는 HTML 태그를 자바스크립트에서 문서 객체로 변환하는 것 = `문서 객체를 선택한다`
>
> 문서객체를 조작하려면 먼저, 문서객체를 선택해야 한다.



- ##### 1개 선택

  | 메소드                          | 설명              |
  | ------------------------------- | ----------------- |
  | document.getElementById(아이디) | 아이디로 1개 선택 |
  | documnet.querySeletor(선택자)   | 선택자로 1개 선택 |

  - document.getElement.ById 메소드 id 속성 중복 시 문제 생긴다.

- ##### 여러 개 선택

  | 메소드                                 | 설명                        |
  | -------------------------------------- | --------------------------- |
  | document.getElementByName(이름)        | name 속성으로 여러 개 선택  |
  | document.getElementByClassName(클래스) | class 속성으로 여러 개 선택 |
  | document.querySelectorAll(선택자)      | 선택자로 여러 개 선택       |



``` javascript
<head>
    <script>
     window.onload= function() {    //이벤트 연결
         var header= document.getElement.ById('header');  //문서객체 선택
     
        header.style.color= 'orange';
        header.style.background= 'red';
        header.innerHTML= 'From JavaScript';
                 // innerHTML = 태그 내부를 의미하는 속성
    };
    </script>
</head>
```



``` javascript
//querySelector() 메소드를 활용해 문서 객체 1개 선택
<head>
    window.onload= function () {
      var header= document.querySelector('h1');   <!--이벤트 연결-->
      
    header.style.color= 'orange';
    header.style.background.color= 'black';
    header.innnerHTM= 'From JavaScript';
    };
</head>
```

``` javascript
//querySelectorAll( ) 메소드 활용해 여러 개 문서 객체 선택
<head>
    window.onload= function () {
    var headers= document.querySeletorAll('h1');
    
    for (var i= 0;i< headers.length; i++) {
           header.style.color= 'orange';
           header.style.background= 'red';
           header.innnerHTML='From JavaScript';
                                    }
    };
</head>
```



##  3. 문서 객체 조작

> 현대적인 방법으로 만든 웹사이트 소스 코드를 보면, HTML태그에 어떠한 내용도 입력되지 않은 것을 볼 수 있다.
>
> 이는 SPA사이트라서 처음에는 웹사이트를 읽어 들일때만 틀만 읽어들이고, 이 후에 자바스크립트 문서 객체를 조작해서 모든 내용을 집어 넣기 때문이다.



-  `SPA(Single Page Application)` : 웹페이지를 한 번만 읽어들이고, 사용자가 조작할 때 웹페이지 내용을 자바스크립트를 사용해 바꾸는 형태의 웹페이지

  

  - #### 효과

  1. 웹 페이지를 여러번 요청하지 않아도 되어 서버부담이 줄어든다.
  2. 사용자가 웹페이지를 이동할 때 새로 웹페이지를 읽어들이며, 발생하는 깜박임도 없어진다.



####   1) 글자 조작

| 속성        | 설명                                                       |
| ----------- | ---------------------------------------------------------- |
| textContent | 문서 객체 내부 글자를 순수 텍스트 형식으로 가져오도록 변경 |
| innnerHTML  | 문서 객체 내부 글자의 HTML 태그를 반영해 가져오도록 변경   |

``` HTML
<head>
    <script>
      window.onload= function () {    //이벤트 연결
          var output= '';             // 변수 선언
          for(var i= 0;i< 10;i++) {
              output +='<h1>Header'+i+'</h1>';
          }
          document.body.textCotent= output;   // 문서 객체 내부글자 순수 텍스트형식 변경
          // document.body.innerHTML= output; // 문서 객체 내부글자 HTML 태그 반영해서 변경
      };
    </script>
</head>
```



####   2) 스타일 조작

> 자바스크립트는 스타일시트에서 사용하던 스타일 속성이름 그대로 입력이 불가능하다. 특수문자'-'를  식별자에 사용 불가능하기 때문이다. 따라서, -으로 연결된 속성은 연결된 단어의 첫글자를 대문자로 연결해야 한다. EX) backgroundColor

- 문자열을 사용해 스타일 속성에 접근할 때는 '-'사용가능

  ``` javascript
  var header= document.getElementById('header')
  header.style.backgroundColor='red';
  
  document.body.style['background-color']= 'red';  
  ```



####   3) 속성 조작

| 메소드                          | 설명      |
| ------------------------------- | --------- |
| setAttribute(속성이름, 속성 값) | 속성 지정 |
| getAttribute(속성이름)          | 속성 추출 |



##### <img 태그 속성 조작>

``` html
<head>
    <script>
     window.onload= fucntion () {                       // 이벤트 연결
         var image= document.getElementById('image');   // 변수 선언
         
         image.src= 'http://placehold.it/300x200';     // 이미지 속성 변경
         image.width= 300;
         image.height= 200;
     };
    </script>
</head>
<body>
    <img id='image'>
</body>
```



##### <body 태그 속성 조작>

``` html
<head>
    <script>
     window.onload= function() {                           // 이벤트 연결
         document.body.setAttribute('data-custom','value');    //속성 지정
         
         var dataCustom= document.body.getAttribute('data-custom');  //속성 추출
         alert(dataCustom);
     }
    </script>
</head>
```

- body 태그에 data-custom 속성을 지정한 후,  속성을 다시 추출해서 출력한다.



##### <문서 객체를 사용한 시간표시>

``` html
<head>
    <script>
     window.onload= function () {                 //이벤트 연결
         var clock= document.getElementById('clock');    //문서 객체 선택    
         setInterval(function () {                     // 1초마다 함수 실행
             var now= new Date ();
             clock.innerHTML= now.toString();
         }, 1000);
     };
    </script>
</head>
<body>
    <h1 id="clock"></h1>
</body>
```



##  4. 이벤트

> 이벤트는 키보드를 누르거나 마우스를 클릭하는 것처럼 어떤 현상이 프로그램에 영향을 미치는 것을 의미한다.

- 마우스이벤트

- 키보드이벤트

- HTML 프레임 이벤트

- HTML 입력양식 이벤트

- 사용자 인터페잇 이벤트

- 구조 변화 이벤트

- 터치 이벤트

  ``` html
  window.onload= function () {};
  ```

  - `onload`를  이벤트 속성이라고 한다.
  - on을 제외한 `load`를 이벤트 이름 또는 이벤트 타입이라고 한다.
  - 이벤트 속성에 넣는 함수를 이벤트 리스너  또는 이벤트 핸들러라고 한다.

---

####   1) 이벤트 연결

> 문서객체에 이벤트를 연결하는 방식을 이벤트 모델이라고 한다.

| 구분       | 종류                                                         |
| ---------- | ------------------------------------------------------------ |
| DOM 레벨 0 | 인라인 이벤트모델 , 고전이벤트 모델                          |
| DOM 레벨 2 | 마이크로소프트 인터넷 익스플로러 이벤트 모델, 표준이벤트 모델 |

- DOM 레벨 0: 연결방식이 쉬워 널리 사용 BUT,  이벤트를 중복해서 연결할 수 없음.

- DOM 레벨 2: 이벤트 중복 연결이 가능하나, 웹 브라우저 종류에 따라 연결하는 방식이 달라 문제.

  - 인라인 이벤트 모델: 인라인 이벤트 모델은 HTML 태그 내부에 자바스크립트 코드를 넣어 이벤트를 연결하는 방식

    ``` javascript
    <head>    //button 태그 내부에 onclick 속성을 사용해 자바스크립트 코드를 입력하고 실행
    </head>
    <body>
        <button onclick="alert('click')">버튼</button>
    </body>
    ```

    ``` javascript
    <head>                  // script 태그에 인라인 이벤트 모델 사용하기
        <script>
         function buttonClick() {           //script 내부에 함수 선언 후 인라인 이벤트 속성 내부에서 해당 함수 실행
             alert('click');
         }
        </script>
    </head>
    <body>
        <button onclick="buttonClick()">버튼</button>
    </body>
    ```

    

  - 고전 이벤트 모델: 과거에 표준으로 많이 사용하던 이벤트 모델

    ``` html
    <head>
        <script>
         window.onload= function() {            //이벤트 연결
             var button= document.getElementById(`button`);       //문서 객체 선택
             button.onclick= function () {//->이벤트리스너          // 이벤트 연결
                 alert('click')
             };
         };
        </script>
    </head>
    <body>
        <button id="button">버튼</button>
    </body>
    ```

  ---

  ####   2) 이벤트 사용

  > 이벤트가 발생하면 웹 브라우저는 이벤트 정보가 담긴 이벤트 객체를 만들어 이벤트 리스너에 전달한다.
  >
  > 따라서, 이벤트 객체를 사용하면 이벤트와 관련된 정보를 알아 낼 수 있다.

  ``` html
  <head>
      <script>
       windo.onload= function(event) {   // event 는 이벤트 객체다.
          alert(event); 
       };
      </script>
  </head>
  ```

   

#####        < 기본 이벤트 제거> 

- 고전 이벤트 모델에서 기본 이벤트를 제거하려면, 이벤트 리스너의 반환값을 false로 입력합니다.
- 기본 이벤트 제거는  a태그와 form 태그에 자주 사용한다.

``` html
<head>
    <script>
     window.onload= function() {    //이벤트 연결
         var buttton= document.getElementById('button');   //문서 객체 선택
         
         button.onclick= function () {   // 이벤트 연결
             return false;      //기본 이벤트 제거
         };
     };
    </script>
</head>
<body>
    <a id="buttton" href="http://jaeyeong.co.kr">버튼</a>
</body>
```

