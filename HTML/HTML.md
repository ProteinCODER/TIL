# - HTML 3요소

##  1. 태그(TAG)와 요소(ELEMENT)

> 페이지를 구성하는 각 부품

- 내용을 가질 수 있는 요소
  - `<요소이름>내용</요소이름>`
  - EX) `<h1>`내용</`h1>`, `<p></p>`, `<audio></audio>`
- 내용을 가질 수 없는 요소
  - `<요소이름>`
  - EX) `<img>`, `<hr>`,` <br>`

##  2. 속성(ATTRIBUTE)

>태그에 추가 정보를 부여할 때 사용하는 것

- EX)  `<h1 title = "header" >`Hello HTML5`</h1>`
- <>= 속성 블록, title= 속성이름, header= 속성 값, Hello HTML5= 내부문자



## + 주석

``` shell
<!--주석 -->
```



---

# - HTML 구조

``` html
<!DOCTYPE html>
<html>
<!-- 웹 브라우저에 표시하는 제목 head-->
<head>
    <title>Hello HTML5</title>    

</head>
<!-- 사용자에게 실제로 보이는 부분을 작성하는 곳 body-->    
<body>
    
</body>    
       
</html>
```



# - HTML 기본 태그

##  01. 글자 태그

####   1) 제목과 본문 글자 태그

|  h   |     heading     |  제목  |
| :--: | :-------------: | :----: |
|  p   |    paragraph    |  단락  |
|  br  |      break      | 줄바꿈 |
|  hr  | horizontal rule | 수평줄 |

####   2) 앵커 태그

| 태그 |  영어  |      설명       |
| :--: | :----: | :-------------: |
|  a   | anchor | 하이퍼링크 생성 |

``` html
<a href= "https://naver.com">네이버</a>
<!-- 네이버 = 출력글자
     href= hyperlink reference-->
```

####  3) 글자모양 태그

- 글자모양 태그 안에 제목, 목록 태그 넣기는 불가

| 태그  |    영어     |     설명      |
| :---: | :---------: | :-----------: |
|   b   |    bold     |   굵은글자    |
|   i   |   italic    | 기울어진 글자 |
| small |             |   작은글자    |
|  sub  |  subscript  |   아래첨자    |
|  sup  | superscript |    위첨자     |
|  ins  |   insert    |   밑줄글자    |
|  del  |   delete    |    취소선     |

####  

## 02. 목록 태그

| 태그 |      영어      |         설명          |
| :--: | :------------: | :-------------------: |
|  ul  | unordered list | 순서가 없는 목록 생성 |
|  ol  |  ordered list  | 순서가 있는 목록 생성 |
|  li  |   list item    |    목록 요소 생성     |



##  03. 테이블 태그

> <thead> 태그는 HTML 테이블에서 헤더 콘텐츠들을 하나의 그룹으로 묶을 때 사용, <table>요소의 자식 요소로 반드시 하나 이상의 <tr>을 포함하고 있어야 한다.

| 태그  |     영어      |         설명          |
| :---: | :-----------: | :-------------------: |
| table |               | 순서가 없는 목록 생성 |
|  tr   |   table row   |     표에 행 삽입      |
|  th   | table heading |    열 제목 셀 생성    |
|  td   |  table data   |   표의 일반 셀 생성   |
| table |    border     | 표의 테두리 두께 지정 |
| th,td |    colspan    |    셀의 너비 지정     |
| th,td |    rowspan    |    셀의 높이 지정     |

##  04. 미디어 태그

|     img태그     |   src    |                  이미지의 경로지정                  |
| :-------------: | :------: | :-------------------------------------------------: |
|                 |   alt    |          이미지가 없을 때 나오는 글자 지정          |
|                 |  width   |                 이미지의 너비 지정                  |
|                 |  height  |                 이미지의 높이 지정                  |
| audio video태그 |   src    |                                                     |
|                 | preload  | 음악 비디오를 준비중일 때 데이터 모두 불러올지 여부 |
|                 | autoplay |           음악 비디오 자동 재생 여부 지정           |
|                 |   loop   |             음악 비디오 반복 여부 지정              |
|                 | controls |        음악 비디오 재생 도구 출력 여부 지정         |

- `<audio> `태그

```html
<body>
 <audio controls="controls">
     <!-- 타입 속성 미입력 시 재생 가능한 파일인 지 확인하는 작업이 필요하므로 입력할 것-->
    <source src="~" type="audio/mp3">
    <source src="~" type="audio/ogg">
    </audio>
</body>    
```

- `<video>`태그

``` html
<body>
   <video controls="controls">
    <source src="~" type="video/mp4">
    <source src="~" type="video/webm">  
    </video>     
</body>
```

``` html
<body>
    <!-- poster 이후 주소url 에서 자동생성한 이미지를 동영상 불러오는 동안 사용자에게 보여줄 수 있는 기능. 주소 다음 너비x높이 입력하면 해당 크기의 이미지 제공 -->
    <video controls= "controls" poster="http://palcehold.it/640x360">
        <source src= "~" type= "video/mp4">
        <source src= "~" type= "vidoo/webm">
    </video>    
</body>
```



----

---

# - HTML5 입력 양식 태그와 구조화 태그

##  1. 입력 양식 태그

``` html
<body>
    <form>
        <input type= "text" name= "search">
        <input type= "submit"
    </form>
</body>
```

- form 태그는 method 속성의 방식으로 action 속성 장소에 데이터를 전달
- 제출 버튼을 누르면 화면을 한 번 새로고침

``` html
<form action="전송위치" method="전송방식">
    
</form> 
```

- <GET 방식>

>  주소에 데이터를 입력해서 전달

``` html
<body>
    <form method= "get">
        <input type="text" name="search ">
        <input type="submit">
    </form>
</body>
```

- <POST 방식>

> 주소가 변경되지 않고 비밀스럽게 데이터전달 > 데이터를 별도로 전송하기 때문에 데이터 용량에 제한이 없다.

``` html
<body>
    <form method="post">
        <input type ="text" name= "search"
        <input type= "submit">       
    </form>
</body>
```

----

---

- ### `<label>` 태그

> label 태그는 input 태그를 설명할 때 사용
>
> lable 태그의 for 속성에 input 태그의 id 속성을 입력해서 label 태그가 어떤 input 태그를 나타내는지 알려준다.

``` html
<form>
    <label for="name" type= "text"></label>
    <input id="name" type= "text">
</form>
```

- ### `<select> `태그

> select 태그는 목록으로 보여주는 항목 중 하나 또는 여러 개를 선택할 때 사용하는 입력 양식 요소
>
> 기본적으로 하나만 선택 가능	

####   1) 한 항목만 선택가능

``` html
<body>
    <select>
         <option>삼겹살</option>
         <option>샤브샤브</option>
         <option>탕수육</option>
         <option>보쌈</option>
    </select>
</body>
```

####   2) 여러 항목 선택가능

``` html
<body>
    <select multiple = "multiple">
         <option>삼겹살</option>
         <option>샤브샤브</option>
         <option>탕수육</option>
         <option>보쌈</option>
    </select>
</body>
```

####   3) 선택 옵션 묶기

``` html
<body>
    <select>
        <optgroup label ="한식">
            <option>꽃등심</option>
            <option>떡갈비</option>
            <option>육회비빔밥</option>
        </optgroup>
        <optgroup label = "중식">
            <option>자장면</option>
            <option>짬뽕</option>    
            <option>팔보채</option>  
        </optgroup>
    </select>
</body>
```

####   4) 연관있는 입력양식 그룹으로 묶기

``` html
<body>
    <fieldset>
        <legend>입력양식</legend>
        <table>
          <tr>
              <td><label for="name">이름</label></td>
              <td><input id="name" type="text"></td>
         </tr>    
         <tr>
              <td><label for="mail">이메일</label></td>
              <td><input id="mail" type="email"></td>
         </tr>       
        </table>
        <input type ="submit">
    </fieldset>
</body>
```



#### +

> Textarea 태그 
>
> <!--  서버 다룰 때 알아야 할 내용임 -->
>
> <textarea>Textarea태그
> Textarea태그</textarea>

![](C:\Users\win\Desktop\멀티캠퍼스\HTML TEXTAREA.PNG)

## 2. HTML5 문서구조화

####  1) 공간 분할 태그

| 태그 | 설명                     |
| ---- | ------------------------ |
| div  | 블록형식으로 공간분할    |
| span | 인라인 형식으로 공간분할 |

- 블록형식은 각 태그가 한 행을 모두 차지

  ``` html
  <body>
      <div>div 태그 -block 형식</div>
      <div>div 태그 -block 형식</div>
      <div>div 태그 -block 형식</div>
  </body>
  ```

- 인라인 형식은 자신의 글자 크기만큼 영역 차지

  ``` html
  <body>
      <span>span 태그 - inline 형식</span>
      <span>span 태그 - inline 형식</span>
      <span>span 태그 - inline 형식</span>
  </body>
  ```

  

  | 블록형식 태그 | 인라인형식 태그 |
  | ------------- | --------------- |
  | div 태그      | span 태그       |
  | h1~h6 태그    | a 태그          |
  | p 태그        | input 태그      |
  | 목록 태그     | 글자형식 태그   |
  | 테이블 태그   | 입력양식 태그   |

  

####  2)시맨틱 태그

- 특정 태그에 의미를 부여해 웹 페이지를 만들기 시작했는 데, 이를 시멘틱 웹이라고 한다.
- 컴퓨터 프로그램이 코드를 읽고, 의미를 인식할 수 있는 지능형 웹 = 시멘틱 웹

##### <HTML5  기본 시맨틱 테그>

| 태그    | 설명                              |
| ------- | --------------------------------- |
| header  | 머리말(페이지제목, 페이지소개)    |
| nav     | 하이퍼링크들을 모아 둔 내비게이션 |
| aside   | 본문 흐름에 벗어나는 노트나 팁    |
| section | 문서의 장이나 절에 해당하는 내용  |
| article | 본문과 독립적인 콘텐츠 영역       |
| footer  | 꼬리말 (저자나 저작권 정보)       |

 

``` html
<body>
	<header>
		<h1>HTML5 기본</h1>
	</header>
	<nav>
		<ul>
			<li><a href="#">메뉴 -1</a></li>
			<li><a href="#">메뉴 -2</a></li>
			<li><a href="#">메뉴 -3</a></li>
		</ul>
	</nav>
	<section>
		<article>
			<h1>Lorem ipsum dolor sit amet</h1>
			<p>Lorem ipsum dolor sit amet, consectetur adipiscing
				elit.Cascading Style Sheets (CSS) is a style sheet language used for
				describing the presentation of a document written in a markup
				language.[1] Although most often used to set the visual style of web
				pages and user interfaces written in HTML and XHTML, the language
				can be applied to any XML document, including plain XML, SVG and
				XUL, and is applicable to rendering in speech, or on other media.
				Along with HTML and JavaScript, CSS is a cornerstone technology used
				by most websites to create visually engaging webpages, user
				interfaces for web applications, and user interfaces for many mobile
				applications.</p>
		</article>
		<article>
			<h1>Lorem ipsum dolor sit amet</h1>
			<p>Lorem ipsum dolor sit amet, consectetur adipiscing
				elit.Cascading Style Sheets (CSS) is a style sheet language used for
				describing the presentation of a document written in a markup
				language.[1] Although most often used to set the visual style of web
				pages and user interfaces written in HTML and XHTML, the language
				can be applied to any XML document, including plain XML, SVG and
				XUL, and is applicable to rendering in speech, or on other media.
				Along with HTML and JavaScript, CSS is a cornerstone technology used
				by most websites to create visually engaging webpages, user
				interfaces for web applications, and user interfaces for many mobile
				applications.</p>
		</article>
	</section>
	<footer>
		<address>광주광역시 서구 농성동</address>
	</footer>
</body>
```

![](C:\Users\win\Desktop\멀티캠퍼스\HTML SEMENTIC.PNG)
