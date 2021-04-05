# <자바 스크립트>

##  1. 자바스크립트 기본용어

- ### 식별자

- 자바스크립트에서 변수나 함수 등에 이름을 붙일 때 사용하는 단어

- | 구분                     | 단독으로 사용 | 다른 식별자와 함께사용 |
  | ------------------------ | ------------- | ---------------------- |
  | 식별자 뒤에 괄호 없음 X  | 변수          | 속성                   |
  | 식별자 뒤에 괄호 있음 () | 함수          | 메소드                 |

  ``` javascript
  alert("Hello World"); // 함수 
  Math.abs(-273) ; // 메소드
  Maht.PI ; // 속성
  ```

- ### #자바스크립트 출력

  ### alert("메시지")



## 2. 자료형과 변수

###  1) 자료형

 1) 숫자

 2) 문자열

 3) 불 bool(참과 거짓)

- 문자열은 국어사전의 앞 쪽에 위치할수록 값이 작다.

  | 연산자 | 설명                               |
  | ------ | ---------------------------------- |
  | !      | 논리부정(참이면 거짓, 거짓이면 참) |
  | &&     | 논리곱(둘다 참이어야 함)           |
  | \|\|   | 논리합(둘 중 하나만 참이어도 참)   |

  

###  2) 변수

- #### JavaScript에서 변수는 `var`로 시작한다.

- 값을 저장할 때 사용하는 식별자

  ``` javascript
  var pi =3.14159265;
  ```



## 3. 조건문과 반복문

- #### if 조건문

  ``` html
  <script>
   var date= new Date() ;          // 변수 선언
   var hours =date.getHours() ;   //요소 추출   
   
   if(hours <12) {
       alert('오전입니다')
   }
      if(12<=hours) {
          alert('오후입니다')
      }
  </script>
  ```

- #### if else 조건문

  ``` html
  <script>
   var date= new Date() ;         
   var hours =date.getHours() ;  
   
   if(hours <12) {
       alert('오전입니다')
   } else {
          alert('오후입니다')
      }
  </script>
  ```

  - 두 가지로 분명하게 나뉘는 상황에서 편리하게 사용할 수 있는 if else 조건문 사용

- #### 중첩 조건문

  ``` html
  <script>
   var date = new Date();
   var hours= date.getHours();
      
      if(hours <5) {
          alert('잠잘 시간이야')
      } else {
          if(hours <7) {
              alert('수업 준비')
          } else {
              if(hours <10) {
                  alert('1교시 수업')
              } else {
                  
              }
          }
      }
  </script>
      
  ```

- #### if else if 조건문

  ``` html
  <script>
   var date = new Date();
   var month =date.getMonth()+1;
   
   if( 3<=month&&month<=5) {
       alert('봄입니다')
   } else if {
       if(6 <=month&&month<=8) {
           alert('여름입니다')
       } else if {
           if(9<=month&&month<=11) {
               alert('가을입니다')
           } else if {
               alert('겨울입니다')
           }
       }
   }  
  </script>
  ```

- #### 반복문

  ``` html
  <script>
   for(var i=0;i<1000;i++) {
       alert('출력')
   }
  </script>
  ```

  - 배열

  - 변수 여러 개를 한꺼번에 다룰 수 있는 자료형

    ``` html
    <script>
     var array=[`가`,`나`,'''];
     
                array[0]='a';    // 배열의 0번째 요소 `a`로 변경
                
                alert(array);
        //alert(array.length);  > 배열의 길이 출력
    </script>
    ```

- #### while 반복문

  ``` html
  <script>
   var i= 0;    //변수 선언
   var array = ['가','나','다'];   // 배열 선언
      while(i< array.length) {
          alert(i+'번 째 출력:'+array[i]);
          i++;
      }
  </script>
  ```

- #### for 반복문

  ``` html
  <script>
   var array=['가','나','다'];
      
      for(i=0;i<array.length;i++) {
          alert(i+'번 째 출력: '+array[i]);
      }
  </script>
  ```

####  <FOR문과 WHILE문>

- 정해진 횟수만큼 반복해야 할 때 = FOR문
- 이외 = WHILE문

####   - 1~100까지의 합

``` html
<script>
 var output= 0;
    for(var i=0;i<=100;i++) {
        output +=i;
        alert(output);
    }
</script>
```



## 4. 함수

###  1) 선언과 호출, 실행 우선순위

---

| 방법       | 표현                |
| ---------- | ------------------- |
| 익명함수   | function () {}      |
| 선언적함수 | function 함수 () {} |

- #### 익명함수 선언

  ``` html
  <script>
   var 함수 = function() {
       alert('함수_01');
       alert('함수_02');
   };
      alert(typeof (함수)+':'+함수)
  </script>
  ```

  - 두 문장을 포함하는 함수를 생성하고 출력

- ####  선언적 함수 선언

  ``` html
  <script>
   function 함수 () {
    alert('함수_01');
      alert('함수_02');
   };
      alert(typeof (함수)+':'+함수);
  </script>
  ```
  
  - 익명 함수를 선언적 함수로 바꾼 것: 실행 결과 함수에 이름이 붙어 있음.

####     함수 ();  // 함수를 호출한다(실행)

###   실행 우선순위

- 가장 마지막에 입력된 값이 저장되고, 실행 시 마지막 입력된 값이 출력된다

  ``` html
  <script>
   var 함수= function() {alert('함수_A')};
   var 함수= function() {alert('함수_B')};
      함수 ();   // 함수 실행
  </script>
  ```

  - 선언적 함수와 익명 함수 함께 사용할 때 실행 순서가 다른데, 자바스크립트는 모든 코드를 읽기 전 선언 함수를 먼저 읽는다.

  - 따라서 선언적 함수가 익명 함수 뒤에 있지만 먼저 읽기 때문에,  코드 실행 시, 나중에 읽은 익명 함수를 실행한다.

    #### 선언함수`_`fucntion 함수()를 먼저 읽기 때문에 출력 시, 익명함수`_`var 함수= function () 이  출력된다.

    

###   2)  매개 변수와 반환값

---

####     매개변수

- 함수의 괄호 안에 집어넣어 함수 쪽에 추가적인 정보를 전달하는 것을 매개변수라고 한다.

####     반환값

- 함수를 실행한 결과를 반환값(리턴값)이라고 한다.

  ``` javascript
  var minutes= date.getMinutes ();
  ---
  function 함수이름 (매개변수,매개변수,매개변수) {
  //함수코드
  //함수코드
  //함수코드
  return 반환 값;
  }
  ```

#####   <예제>

``` html
<script>
 function f(x) {
     return (2*x)+1 ;
 }
    alert(f(3));
</script>
```



### 3) 콜백 함수

---

> 매개 변수로 전달되는 함수를 콜백 함수라고 한다.

``` html
<script>
 function CallTenTimes(callback) {
     for(var i=0;i<10;i++) {
         callback() ;
     }
 } 
    var callback= function() {   // 변수 선언              callTenTimes(function() { alert('함수호출')}); 가능
        alert('함수 호출')    // '함수호출'이 열 번 출력된다.
    }
    callTenTimes(Callback);   //함수 호출    
</script>
```

- 콜백 함수는 익명함수로 사용할 때가 많다. 매개변수에 익명함수를 곧바로 입력할 수 있다.



## 5. 객체

> 객체는 자료형 어러 개를 한 번에 저장한다
>
> 배열은 `인덱스`를 기반으로 자료를 저장하지만, 객체는 `키`를 기반으로 자료를 저장한다.



- ##### 객체 뒤 대괄호를 사용해 키를 입력하면 객체 속성에 접근 가능

``` html
product['제품명'] :'망고' 
식별자 생성 규칙에 어긋나는 문자를 키로 사용할 경우, 반드시 대괄호로 감싸야 객체 요소에 접근 가능

<script>
 var object = {
     'with space' :273,
     'with ~!@#$%()_+':52
 };
    alert(object['with space']);
    alert(object['with ~!@#$%()_+']);
</script>
```

- ##### `for in 반복문` = for(var 키 in 객체) {문장}   = 객체 요소 하나씩 살펴보기 가능

  ``` html
  <script>
   var product = {
       제품명: '망고',
       유형: '당절임'
   };
      for(var i in product) {
          alert(i+':'+product[i]);
      }
  </script>
  ```



####   속성과 메소드

---

> 배열에 있는 값 하나하나를 요소라고 하며, 객체에 있는 값 하나하나를 속성이라고 한다.
>
> ##### 객체 속성 중 자료형이 함수인 속성을 특별히 `메소드`라고 한다.
>
> ##### 객체에 있는 속성을 메소드에서 사용하고 싶을 때 자신이 가진 속성임을 분명하게 표시해야 한다. (this 키워드 사용)   
>
> ``` html
> <script>
>  var person = {
>      name: '장재영'
>      eat: function(food) {
>          alert(this.name+'이'+food+'을/를 먹습니다.')     //객체에 있는 속성 메소드에서 사용 this.
>      }
>  };
> person.eat('밥') ;    //메소드 호출
> </script>
> ```

#### JavaScript에선 반드시 this를 써야한다 . 안쓰면 오류 나옴