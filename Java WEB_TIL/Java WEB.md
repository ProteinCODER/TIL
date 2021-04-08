# 1. 정적 웹 프로그래밍

- #### 1) 클라이언트 2) 웹서버 3) 관리자

- 사용자에게 화면 디자인 같은 고정된 정보만 제공

- 정보 수정 시 관리자가 직접 HTML 소스를 수정하여 사용자에게 정보 제공



# 2. 동적 웹 프로그래밍 

- #### 1) 클라이언트 2) 웹서버 3) 웹 어플리케이션 서버  4) 데이터베이스

- 정적 웹 프로그래밍에서 관리자가 하던 역할을 웹 어플리케이션 서버`(WAS)`가 수행한다.

- 초기 : CGI(Common Gate Interface) 공용 게이트 인터페이스 방식

- 프로세스 방식으로 진행, 서버의 부하가 심하다

- 이 부분을 개선하여 나온 것이 JSP, ASP, PHP 같은 동적 웹 프로그래밍 기술이다.

##   JSP 프로그램 (JAVA 스레드에 관해 추가 공부 필요하겠다)

> 기존 프로세스 방식이 아닌 스레드(thread) 방식으로 실행하기 때문에 CGI 방식보다는 효율적으로 기능을 수행

- 각각의 요청에 대한 기능을 메모리에 따로따로 로드하지 않아도 된다.

- 클라이언트의 요구를 처리하는 기능은 최초 한 번만 메모리에 로드된다.
- 클라이언트가 동일한 요구를 하면 기존에 사용한 기능을 재사용한다.



톰캣 컨테이너= 웹 어플리케이션 서버의 일종

이클립스= JSP 개발 도구



# 3. 웹 어플리케이션

> 기존의 정적인 웹 어플리케이션의 기능을 그대로 사용하면서, 서블릿, JSP, 자바 클래스들을 추가하여 사용자에게 동적인 서비스를 제공하는 프로그램
>
> 웹 컨테이너에서 실행되는 JSP, 서블릿, 자바 클래스들을 사용해 정적 웹 프로그래밍 방식의 단점을 보완하여, 서비스를 제공하는 서버 프로그램



| 구성요소 | 기능                                                         |
| -------- | ------------------------------------------------------------ |
| webShop  | 루트 디렉토리, 다른 웹 애플리케이션 이름과 중복허용하지 않음. JSP HTML 파일 저장되는 곳 |
| WEB-INF  | 웹 어플리케이션 관련 정보 저장되는 곳, 외부에서 접근 불가    |
| classes  | 웹 어플리케이션이 수행하는 서블릿과 다른 일반 클래스들이 위치하는 곳 |
| lib      | 여러 라이브러리 압축 파일(.jar)이 저장되는 곳                |
| web.xml  | 배치지시자로서 일종의 환경 설정 파일. 웹 어플리케이션에 대한 여러가지 설정을 할 때 사용 |





###  +추상 클래스

---

> 추상(abstract): 실체 간 공통되는 특성을 추출한 것. 구체적인 실체라기 보다는 실체들의 공통되는 특성을 가지고 있는 것
>
> 객체를 직접 생성할 수 있는 클래스를 실체 클래스라고 한다면, 이 클래스들의 `공통적인 특성`을 추출해서 선언한 클래스를 `추상클래스`라고 한다.

-  추상클래스 = 부모 / 실체클래스= 자식

- ##### 추상클래스는 new 연산자를 사용해서 인스턴스를 생성시키지 못한다.

- 왜냐하면, 추상클래스는 실체클래스의 공통되는 필드와 메소드를 추출해서 만들었기 때문이다.

  ``` java
  class Bear extends Animal {'''} 
      // 추상클래스는 실체클래스를 만들기 위해 부모 클래스로만 사용된다. 
      //때문에, extends 뒤에만 올 수 있다.
  ```



##### - 추상 클래스 용도

1) 실체 클래스들의 공통된 필드와 메소드의 이름을 통일할 목적

- 동일한 데이터와 기능임에도 불구하고, 이름이 다르다보니, 객체마다 사용법이 달라질 수있는데 이를 방지하는 목적
- ex) Phone이라는 추상클래스에 owner 필드와 turnOn( ) 메소드 선언해서, 상속받는 실체클래스의 필드와 메소드 통일가능

2) 실체 클래스를 작성할 때 시간을 절약

- 공통적인 필드와 메소드는 추상클래스인 Phone에 모두 선언해두고, 실체 클래스마다 다른 점만 실체클래스에 선언하게 되면, 실체 클래스를 작성하는데 시간을 절약할 수 있다.

> 코더가 작성해야할 클래스가 다수이고, 이 클래스들이 동일한 필드와 메소드를 가져야 할 경우, 설계자는 이 내용들을 추려내어 추상클래스로 설계 규격을 만드는 것이 좋다.
>
> EX) 타이어 규격 = 추상 클래스 /  규격을 바탕으로 만든 금호타이어, 한국타이어 = 실체 클래스



##### - 추상 클래스 선언

``` java
public abstract class 클래스 {
    //필드
    //생성자
    //메소드
}
```

- abstract를 붙이게 되면 new 연산자를 사용해서 객체를 만들지 못하고, 상속을 통한 자식 클래스만 만들 수 있다.

  ``` java
  //<Phone.java>
  public abstract class Phone {
      public String owner; 
      public Phone(String owner) {
          this.owner=owner;
      }
      public void turnOn() {
          System.out.pirntln("전원을 켭니다");
      }
      public void turnOff() {
          System.out.println("전원을 끕니다");
      }
  }
  ```

- 추상클래스는 자식객체가 생성될 때 super(```)를 호출해서 추상 클래스 객체를 생성하므로, 추상 클래스도 생성자가 반드시 있어야한다.

  ``` java
  //Smartphone.class
  public class Smartphone extends Phone {
      public Smartphone(String owner) {   //생성자
          super(owner);
      }
      public void internetSearch() {
          System.out.println("인터넷 검색을 합니다.");
      }
  }
  ```

##### - 추상 메소드와 오버라이딩

- Animal.java

  ``` java
  public abstract class Animal { 
      public String kind;
      public void breath() {
          System.out.pirntln("숨을 쉽니다");
      }
      public abstract void sound();         //추상 메소드
  }
  ```

- Dog.java

  ``` java
  public class Dog extends Animal {} {
      public Dog() {
          this.kind="포유류";
      }
      @Overrride            //추상 메소드 재정의
      public void sound() {
      System.out.println("멍멍");
      }
  }	animalExample.java
  ```

- AnimalExample.java

  ``` java
  public class AnimalExample {
      public static void main(String[] args) {
          Dog dog =new Dog();
          dog.sound() ;
          System.out.println("---");
          
          Animal animal= null; //변수의 자동 타입 변환
          animal= new dog();  //자동 타입 변환
          animal.Sound();     // 재정의된 메소드 호출
          
          animalSound(new dog());    //new dog이 animal로 자동 타입 변환되어
          public static void animalSound(Animal animal)   // 재정의된 sound() 메소드가 호출
              
      }
  }
  ```

  - ##### sound 메소드 호출 세가지 방법

  - 1. Dog 변수로 호출
    2. Animal 변수로 타입 변환해서 sound() 메소드 호출 (자식타입은 부모타입으로 자동 타입변환. 메소드가 재정의 돼있을 경우, 재정의된 자식 메소드가 호출되는 상속의 특징이 적용)
    3. 부모타입의 매개변수에 자식 객체를 대입해서 `메소드의 다형성`을 적용

    > 메소드의 다형성
    >
    > ##### `"객체가 한 개 이상의 자료형 타입을 갖게되는 특성을 다형성(폴리모피즘)이라고 한다."`
    >
    > ##### - 자동 타입 변환은 필드 값을 대입할 때에도 발생하지만, 주로 메소드를 호출할 때 많이 발생한다. 메소드를 호출할 때에는 매개변수의 타입과 동일한 매개값을 지정하는 것이 정석이지만, 매개값을 다양화하기 위해 매개변수에 자식타입 객체를 지정할 수도 있다.
    >
    > 다형성은 하나의 타입에 대입되는 객체에 따라서 실행 결과가 다양한 형태로 나오는 성질을 말한다.
    >
    > ``` java
    > public class Vehicle {
    >     public void run() {
    >         System.out.println("차량이 달립니다");
    >     }
    > }
    > ----
    > public class Driver {
    >     void drive(Vehicle vehicle) {
    >         Vehicle.run();
    >     }
    > }
    > -----
    > public class Bus extends Vehicle {
    >     @Override
    >     public void run() {
    >         System.out.println("버스가 달립니다.");
    >     }
    > }
    > ----
    > public class driverExample {
    >     public static void main(String[] args) {
    >         Driver driver= new Driver;
    >         Bus bus= new BUS;
    >         driver.drive(bus);
    >     }
    > }
    > //Vehicle vehicle = bus;  자동 타입변환
    > ```



### + 인터페이스

---

상속은 같은 종류의 하위 클래스를 만드는 기술, 인터페이스는 사용방법이 동일한 클래스를 만드는 기술이라는 개념적 차이가 있지만, 둘 다 다형성을 구현하는 기술이라는 것은 동일하다.

| 물리적세계              | 자바세계                                  |
| ----------------------- | ----------------------------------------- |
| 컴퓨터                  | ZooKeeper(실행용 클래스)                  |
| USB포트                 | Predator(인터페이스)                      |
| 하드디스크,스마트폰 --- | Tiger, Lion, Crocodile --- (lib용 클래스) |

1. ##### 인터페이스 자체에 메소드 생성 BUT, 메소드 내 동작 내용 비워둘 것

   ``` java
   public interface Predator{
       public String getFood();
   }
   ```



2. ##### Tiger에 getFood 메소드 구현

   ``` java
   public class Tiger {
       public String getFood() {
           return "apple";
       }
   }
   ```

   

3. ##### ZooKeeper 실행(predator 인터페이스를 구현한 구현체(tiger)의 getFood()메소드 호출)

   ```java
   public class ZooKeeper {
       public void feed(Predator predator) {
           System.out.println("feed"+predator.getFood)
       }
   }
   ```

> ##### 중요한 점: ZooKeeper 클래스가 동물들의 종류에 의존적인 클래스에서 동물들의 종류와 상관없는 독립적인 클래스가 되었다는 점

####   1. 상수 필드

- 인터페이스는 데이터를 저장할 수 없기 때문에 데이터를 저장할 인스턴스 또는 정적필드를 선언할 수 없다.
- 상수는 public static final로 선언한다. 이를 생략하더라도 자동적으로 컴파일 과정에서 붙게 된다.
- ex) int MAX_VOLUME= 10;  상수는 대문자, 서로 다른 언어로 구성되어 있을 경우 언더바(_)로 연결

####   2.  추상 메소드

- 형태: 리턴타입 메소드명 (매개변수,''') ;
- public abstract 생략해도 컴파일 과정에서 자동으로 붙음.

####   3. 디폴트 메소드

- 형태 : default 리턴타입 메소드명(매개변수,''') {'''}

- 디폴트 메소드는 인터페이스에 선언되지만, 인터페이스에서 바로 사용할 수 없다. 추상 메소드가 아닌 인스턴스 메소드이므로, 구현객체가 있어야 사용할 수 있다.

- 구현 클래스 작성할 때, 디폴트 메소드를 재정의(오버라이딩)해서 자신에게 맞게 수정하면 디폴트 메소드가 호출 될 때 자신을 재정의한 메소드가 호출된다.

- ``` java
  default void setMenu(boolean mute) {
      if(mute) {
          System.out.pirntln("무음 처리합니다.")
      } else {
          System.out.println("무음 해제합니다.")
      }
  }
  ```

####   4. 정적 메소드

- 형태: static 리턴타입 메소드명(매개변수,''') {'''}



####  - 구현 클래스

- ``` java
  public class 구현클래스명 implements 인터페이스명 {}
  ```

- 인터페이스 변수에 구현 객체 대입

  ``` java
  public class RemoteControlExample {
      public static void main(String[] args) {
          RemoteControl rc;  //  인터페이스 변수 선언
         rc= new Televison(); // 구현 객체 대입
         rc= new Audio(); 
      }
  }
  ```

####  - 익명 구현객체

- 소스파일을 만들지 않고도 구현 객체를 만드는 방법

- UI 프로그래밍에서 이벤트 처리 목적, 임시 작업 스레드 만드는 목적으로 많이 활용.

- 람다식은 인터페이스의 익명 구현 객체를 만듬

  ``` java
  인터페이스 변수= new 인터페이스() {
      //인터페이스에 선언된 추상 메소드의 실체 메소드 선언
  };  //끝에 ; 반드시 붙일 것
  ```

  - 중괄호 안에는 모든 추상 메소드들의 실체 메소드를 작성해야 한다.

####  - 다중 인터페이스 구현 클래스

- ``` java
  public class 구현클래스명 implements 인터페이스A, 인터페이스B {
      인터페이스 A에 선언된 추상메소드에 대한 실체메소드 선언
      인터페이스 B에 선언된 추상메소드에 대한 실체메소드 선언    
  }
  ```

- 구현 클래스는 모든 인터페이스의 추상메소드에 대해 실체 메소드를 작성해야 한다. 하나라도 없으면 추상 클래스로 선언해야 한다.



#### - 인터페이스 사용

---

> 인터페이스로 구현 객체를 사용하려면 인터페이스 변수를 선언하고, 구현 객체를 대입해야 한다. 인터페이스 변수는 참조타입이기 때문에 구현 객체가 대입될 경우 구현 객체의 번지를 저장한다.
>
> #### 1. 인터페이스 변수 선언     2. 인터페이스 변수에 구현 객체 대입



- 인터페이스 변수 선언 ex) RemoteControl RC= null;

- 구현 객체 대입 ex) rc= new Televison();  이후, 메소드 실행 rc.tunOn();

- 메소드 호출 시 어떤 구현 객체를 매개값으로 주느냐에 따라, 추상메소드의 실행결과는 다르게 나온다.

- 구현 객체가 인터페이스 타입으로 변환되는 것은 자동타입변환이라고 한다.

- ##### `필드의 다형성`: ex)"한국타이어. 금호타이어 = 구현 클래스  => 모두 타이어 인터페이스로 동일하게 사용할 수 있는 교체 가능한 객체에 해당한다.

  * 객체 생성 후, 초기 값으로 대입한 구현 객체 대신 다른 구현 객체를 대입할 수도 있다. 

  ``` java
  Car mycar= new Car();
      mycar.frontLeftTire= ''';   //기존과 다른 구현 객체 대입
  ```

  ##### 인터페이스 배열로 구현객체 관리

  ``` java
  Tire [] tires= {
      new HanKookTire();
      new HanKookTire();
      new HanKookTire();
      new HanKookTire();\    
  }
  void run() {        // 구현 객체들을 배열로 관리하면 제어문에서 가장 많이 혜택을 본다.
      for(Tire tire: tires) {
          tire.roll();
      }
  }
  ```

  ##### 강제 타입 변환(Casting)

  - 구현 객체가 인터페이스 타입으로 자동변환하면, 인터페이스에 선언된 메소드만 사용가능하다.

  - 하지만, 구현 클래스에 선언된 필드와 메소드를 사용해야 하는 경우도 발생한다. 이 때 강제 타입변환을 해서 다시 구현클래스 타입으로 변환한 다음, 구현 클래스의 필드와 메소드를 사용할 수 있다. 

    ``` java
    구현 클래스 변수 = (구현클래스) 인터페이스 변수 ;
    ---
        public interface vehicle{
         void run();
    }
    ---
        public class bus implemets vehicle {
            @Override
            public void run() {
                System.out.printlnl("버스가 달립니다");
            }
            public void checkFare() {
                System.out.println("승차요금을 체크합니다");
            }
        }
    ---
        public class VehicleExample {
            public static void main(String[] args) {
                Vehicle vehicle= new Bus();
                
                vehicle.run();              // > 버스가 달립니다 
                //vehicle.checkFare();     // (x)
                Bus bus=(bus) vehicle;
                bus.run();                  //> 버스가 달립니다.
                bus.checkFare();            //> 승차요금을 체크합니다.
            }
        }
    ```

  ##### 객체 타입확인 (instanceof)

  ``` java
  public class Driver {
      public void drive(Vehicle vehicle) {
          if(vehicle instanceof Bus) {     //vehicle 매개변수가 참조하는 객체가 Bus인지 조사
              Bus bus=(Bus) vehicle;       // Bus 객체일 경우 안전하게 강제 타입변환
              bus.checkFare();
          }
          vehicle.run();
      }
  }
  ```

#### 

#### - 인터페이스 상속

---

> 인터페이스는 클래스의 상속과는 달리, 다중 상속을 허용한다
>
> 하위 인터페이스로 타입 변환이 되면 상 하위 인터페이스에 선언된 모든 메소드를 사용할 수 있으나, .상위 인터페이스 타입으로 변환이 되면 상위 인터페이스에 선언된 메소드만 사용이 가능하다.

#### 

#### - 디폴트 메소드와 인터페이스 확장

---

> 디폴트 메소드는 인터페이스에서 선언된 인스턴스 메소드이기 때문에, 구현 객체가 있어야 사용할 수 있다.
>
> 인터페이스에서 디폴트 메소드를 허용한 이유는 기존 인터페이스를 확장해서 새로운 기능을 추가하기 위해서이다.
>
> 기존 인터페이스의 이름과 추상 메소드의 변경없이 디폴트 메소드만 추가할 수 있기 때문에 이전에 개발한 구현 클래스를 그대로 사용하면서 새롭게 개발하는 클래스는 디폴트 메소드를 활용할 수있다.

``` java
public void method1() {} //기존 추상메소드
public default void method2() {} // 디폴트 메소드 추가하면서 기존에 사용하던 구현 클래스는 문제없이 사용하면서, 새로운 구현 클래스에서 메소드 기능을 추가하여 사용할 수 있다.
```



#### - 디폴트 메소드가 있는 인터페이스 상속

---

> 부모 인터페이스에 디폴트 메소드가 정의되어 있을 경우, 자식 인터페이스에서 디폴트 메소드를 활용하는 방법 
>
> 1. 디폴트 메소드를 단순히 상속받는다
> 2. 디폴트 메소드를 재정의해서 실행 내용을 변경한다.
> 3. 디폴트 메소드를 추상메소드로 재선언한다.

# 서블릿(Servlet)