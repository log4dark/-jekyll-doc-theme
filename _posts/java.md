# Java
Drop in Java :love_you_gesture: 

**객체지향 프로그래밍**이란? 
+ 클래스
+ 객체
+ 메시지

특징은?
+ 캡슐화
+ 추상화
+ 다형성
+ 상속

그리고, 목차... 링크 하자~~~

## Contents
> + 01 데이터 타입 (Data Type)
> + 02 연산자
> + 03 제어문
> + 04 클래스 (Class)
> + 05 상속
> + 06 인터페이스 (Interface)
> + 07 중첩 클래스와 중첩 인터페이스 (Nested Class and Nested Interface)
> + 08 예외 처리 (Exception)
> + 09 제너릭 (Generic)
> + 10 자바 API (Library)
>   + java.lang
>   + java.util
>   + java.time
> + 11 스레드 (Thread)
> + 12 자바 I/O 입출력
> + 13 자바 네트워킹
> + 14 람다식(Lambda)
> + 15 스트림과 병렬 처리 

## 00 Start...
API Document link: <https://docs.oracle.com/javase/8/docs/api/>

### 자바란?
- 객체지향 언어
- Garbage Collector
- JVM(Java Virtual Machine) - One source multi-use
- 함수적 스타일 코딩 지원 -> 람다식(Lambda Expression)
 
## 01 데이터 타입 (Data Type)
### 기본 타입(Primitive Type)
#### 정수 타입
- byte: 1byte - 바이너리 데이터 처리할 때 사용 (파일, 네트워크)
- char: 2byte, 0~2<sup>16-1</sup> (유니코드: \u0000~\uFFFF)
- short: 2byte
- int: 4byte
- long: 8byte
 
#### 실수 타입
- float: 4byte
- double: 8byte
 
### 참조 타입(Reference Type)
배열, Enum, 클래스, 인터페이스 타입으로 객체(Object)의 주소값을 저장하는 타입 - 변수는 스택영역, 객체는 힙 영역  

#### String 타입
...
```java
// 문자열 리터럴이 동일하면 같은 객체를 공유
String name1 = "penny"; 
String name2 = "penny";
name1 == name2; // true (주소 비교)

// name3과 name4는 서로 다른 객체
String name3 = new String("penny");
String name4 = new String("penny");
name3 == name4; // false

// String 값 비교는 equals 메소드 사용. 
name3.equals(name4); // true
```

#### 배열 타입
배열 선언
```java
int[] array; // 타입[] 변수
int array[]; // 타입 변수[]
```

배열 선언과 값 할당
```java
String[] name1 = {"dark", "penny", "jisung");
String[] name2 = null;
name2 = new String[] {"dark", "penny", "jisung");
// 배열 객체의 주소 출력
System.out.printf("name=%x\n", System.identityHashCode(name));
```

커맨드 라인 입력
```java
// $ java TcpServer 127.0.0.1 20000 
public String void main(String[] args) {
	args.length; // 2
    args[0]; // 127.0.0.1
    args[1]; // 20000 
    ...
}
```

다차원 배열
```java
int[][] scores = new int[2][3];
scores.length; // 2
scores[0].length; // 3
scores[1].length; // 3
```

#### Enum 타입
Enum 선언
```java
// BloodType.java
public enum BloodType { // 파일명과 Enum명이 같아야 함
    A, // 요넘 하나가 객체임
    B,
    AB,
    O
}
```

Enum 객체의 메소드
- name(): 열거 객체의 문자열 리턴
- ordinal(): 열거 객체의 순번(0부터 시작)을 리턴
- valueOf(): 주어진 문자열의 열거 객체를 리턴
- compareTo(): 열거 객체를 비교해서 순번 '차이'를 리턴
- values(): 모든 열거 객체들을 배열로 리턴  
 
```java
BloodType bt1 = Bloodtype.AB;
String name = bt1.name(); // "AB"
int ordinal = bt1.ordinal(); // 2
bloodType = bt1.valueOf("O"); // O

BloodType bt2 = BloodType.A;
bt1.compareTo(bt2); // -2
bt2.compareTo(bt1); // 2

BloodType[] btArr = BloodType.values();
for(BloodType bt3 : btArr) {
	System.out.println(bt3); // A, B, AB, O
}
```  

C/C++ style Enum[^1]
```java
public enum ErrorCode {
    SUCCESS(0), // SUCCESS 객체를 생성, 생성자 구현 후 int 0 으로 설정
    ERROR(1),

    UNDER_CONSTRUCTION(9000);
    
    private final int errorCode;
    ErrorCode(int errorCode) { this.errorCode = errorCode; }
    public int value() { return errorCode; }
}
ErrorCode.UNDER_CONSTRUCTION.value(); // 9000
```

## 연산자
### 연산자(Operator) 종류
- 산술: +, -, *, /, %
- 부호: +, -  // 음수와 양수의 부호
- 대입: =, +=, -=, *=, /=, %=, &=, ^=, |=, <<=, >>=, >>>=
- 증감: ++, --
- 비교: ==, !=, >, <, >=, <=, instanceof
- 논리: !, &, |, &&, ||
- 조건: (조건식)?A:B
- 비트: ~, &, |, ^
- 쉬프트: >>, <<, >>>
 
### 연산자 우선순위
1. 증감(++, --), 부호(+, -), 비트(~), 논리(!)
2. 산술(*, /, %)
3. 산술(+, -)
4. 쉬프트(<<, >>, >>>)
5. 비교(<, >, <=, >=, instanceof)
6. 비교(==, !=)
7. 논리(&)
8. 논리(^)
9. 논리(|)
10. 논리(&&)
11. 논리(||)
12. 조건(?:)
13. 대입(=, +=, -=, *=, /=, %=, &=, ^=, |=, <<=, >>=, >>>=)


## 제어문
### 조건문
- if
- switch
 
### 반복문
- for
- while
- do-while
 
### 기타
- break
- continue

**Java 5 for loop syntax**  
(1)배열에서 가져올 값이 있는지 평가, 있으면 (2)->(3)->(1) 이고, 없으면 `for`문 종료
```java
for ( (2)타입 변수 : (1)배열 ) {
	(3)실행문;
}

int[]scores = {95, 90, 87, 89, 97};
for (int scores : scores) {
	// processing...
}
```  

## 04 클래스 (Class)
### 객체지향 프로그래밍
객체간의 상호작용, 메소드 호출(메시지 전달), 객체간의 관계.  

#### 객체란?
물리적으로 존재하거나 추상적으로 존재하며 자신만의 속성을 가지고 식별되는 개체이다.  
객체는 속성과 동작으로 구성되어 있고, 자바에서는 각각을 필드(**field**)와 메소드(**method**)라고 한다.  
그러면, 클래스는? 객체를 생성/만들기 위한 템플릿(Template)이다.

**Instance vs. Object**[^2]  
예를 들어서 그릇에 사과 5개가 있고, 각각의 사과는 사과 타입의 객체이고, 둥글고, 크고등의 특징을 가지고 있다.   
위의 내용을 프로그래밍 관점에서 보면,  
Apple 클래스에 변수로 shape:둥글고, size:크다 등을 가져야 하고,   
그릇에 5개의 사과를 표현하기 위해서는 5개의 사과를 만들어야(**인스턴스화**) 한다.   
`Apple apple1, Apple apple2, Apple apple3 etc...`. 

즉, 클래스로 부터 객체를 만드는 과정을 인스턴스화라고 하고, 클래스로 부터 만들어진 객체를 해당 클래스의 인스턴스(instance)라고 한다.

#### 클래스간의 관계
- 영속적인 관계가 아닐 경우 (멤버가 아님)
  - dependency: *uses a* - 메소드의 파라미터로 넘어오는 객체일 경우
- 영속적인 관계일 경우 (멤버)
  - association: *uses a* - cssociation은 클래스간의 관계가 논리적으로 전체(집합)와 부분의 관계일 경우, aggregation과 composition으로 나눌 수 있다.
    - aggregation: *has a* (...는...를 가짐)
    - composition: *owns a*
- 영속적인 관계일 경우 (상속)
  - inheritance: *is a*

```
// 객체간의 관계
                         machine
                            ^
                            | 상속 관계 (inheritance)
person --사용(dependency)--> car
                            ^
                            | 집합 관계 (association)
                +-----------|------------+
                |           |            |
              engine       tire        handle
```

### 클래스 선언, 객체 생성과 클래스 변수
```java
// 클래스 선언
public class Car {
  ...
}

// 'new' 연산자로 car 객체를 생성
Car car = new Car();
```

### 클래스의 구성 멤버
```java
public class ClassName {
  // 필드 - 데이터 저장
  int fieldName;
  
  // 생성자 - 객체 생성 시, 초기화
  ClassName() { ... }
  
  // 메소드 - 객체의 동작
  void methodName() { ... }
}
```
필드를 클래스 멤버 변수로 부르기도 함.  
필드 선언과 동시에 초기화 가능하고 생략 시, 필드 초기값은 정수/실수 티입은 '0', 논리 타입은 'false', 참조 타입은 'null' 이다.

### 생성자
객체의 생성 시, 초기화 역할 

#### 다른 생성자 호출 (this())
```java
클래스( [매개변수선언, ...] ) {
  this( 매개변수, ..., 값, ... ); // 클래스의 다른 생성자 호출
}

Car(String model) {
  this(model, 250);
}

Car(String model, int maxSpeed) {
  this.model = model;
  this.maxSpeed = maxSpeed;
}
```

### 메소드
객체의 동작 역할  

#### 메소드 선언 시, 매개 변수의 수를 모를 경우
```java
// 매개 변수를 배열 타입으로 선언
int sum1(int[] values) { ... }

int[] values = {1, 2, 3}
int result = sum1(values);
int result = sum1(new int[] {1, 2, 3, 4, 5});

// 매개 변수를 "..."를 사용해서 선언
// - 메소드 호출 시, 배열을 생성 하지 않고, 값만 나열하면 자동으로 배열 생성 됨.
int sum2(int ... values) { }

int result = sum2(1, 2, 3);
int result = sum2(1, 2, 3, 4, 5);
int result = sum2(new int [] {1, 2, 3, 4}); // 배열을 직접 사용 해도 됨
```

### 접근 제한자
...

### 정적 멤버와 static
...

### 패키지
패키지는 클래스를 체계적으로 관리하기 위한 디렉토리 형태의 체계  
- "패키지명+클래스명" 형태로 패키지는 클래스를 유일하게 만드는 역할
- 즉, 클래스 이름이 같아도 패키지 이름이 다르면, 다른 클래스로 인식

#### 패키지 선언
```java
package 상위패키지.하위패키지;
public class ClassName { ... }
```

### 어노테이션(Annotation)
...  


## 05 상속
### Keywoard:
+ 상위 클래스/부모 클래스, 하위 클래스/자식 클래스
+ 코드 중복을 줄이기 위해?
+ `extends`
+ 다중 상속 지원하지 않음

### 클래스 상속
```java
class 자식클래스 extends 부모클래스 {
}

class SportsCar extends Car {
  public SportsCar() {
    super(); // 자식 생성자 호출 시, 부모 생성자 호출 됨.
  }
}
```

### 메소드 재정의(Overriding)
부모 클래스의 특정 메소드를 상황에 따라 자식 클래스에서 **재정의**, 즉 부모 클래스의 메소드를 가림~ 
규칙:
- 부모의 메소드와 동일한 시그너처(리턴 타입, 메소드 이름, 매개변수 리스트)를 가져야 한다.
- 접근 제한을 더 강하게 오버라이딩할 수 없다.
- 새로운 예외를 throws할 수 없다.

@Override 어노테이션 설정 시, 컴파일러가 규칙 체크하여 개발자 실수를 줄여줌.

#### 부모 메소드 호출(super)
자식 클래스에서 오버라이딩된 부모 클래스의 메소드 호출해야 할 때, `super.부모메소드()`로 사용.  

### final 클래스와 final 메소드
`final` 키워드는 클래스, 메소드, 필드에서 사용할 수 있고, 최종상태의 의미를 가짐
+ `final` 클래스는 자식 클래스에서 상속할 수 없는 클래스임
  + `public final class String { ... }`
+ `final` 메소드는 자식 클래스에서 오버라이딩 할수 없음
  + `public final 리턴타입 메소드명() { ... }`
+ `final` 필드는 상수 정의 
  + `public final int success = 0`

### 타입 변환과 다형성
다형성이란 동일한 타입을 사용하지만 다양한 결과가 나오는 성질로써 상속관계에서...
부모 타입에 모든 자식 객체를 대입할 수 있고, 바로 위의 부모가 아니더라도 상속 계층에서 상위 타입이라면 가능하다.

#### 자동 타입 변환  
`부모클래스 변수 = 자식클래스타입;`

#### 필드의 다형성 
부모 타입으로 (자동)형 변환되면, 부모 클래스에 선언된 필드와 메소드만 접근이 가능하다.  
한가지 예외는 자식 클래스에서 메소드가 오버라이딩 되었다면, 자식 클래스의 메소드가 호출 된다.
```java
public class Car {
  Tire tire1 = new KoreaTire(); // 다형성 예
  Tire tire2 = new JapanTire();
}
```

#### 매개 변수의 다형성
```java
public class Car {
  public void run() {} // 차량이 달립니다.
}

public class Bus extends Car {
  public void run() {} // 버스가 달립니다.
}

public class Taxi extends Car {
  public void run() {} // 택시가 달립니다.
}

public class Driver {
  public void drive(Car car) {
    car.run();
  }
}

// main
Taxi taxi = new Taxi()
Driver driver = new Driver(taxi); // Car car = taxi;
driver.run(); // 택시가 달립니다. (자식 객체에서 재정의한 run 호출)
```  

#### 강제 타입 변환(Casting)
자식 객체가 부모 객체의 타입으로 자동 타입 변환 후, 다시 자식 타입으로 변환할 때 강제 타입 변환을 사용할 수 있다.  
어떤 경우에 사용할까? 자식 객체의 필드와 메소드 사용을 하고 싶을 때, 강제 타입 변환 함.
```java
자식 클래스 변수 = (자식 클래스) 부모 클래스 타입;
```

#### 객체 타입 확인(instance of)
강제 타입 변환은 자식 타입이 부모 타입으로 변환된 상태에서만 다시 자식 타입으로 변환 가능하다.
```java
Taxi taxi = (Taxi) car; // car의 타입이 Car인지 Taxi인지 어떻게 알수 있을까?
```

어떤 객체가 어떤 클래스의 인스턴스인지 확인하기 위해서 `instance of` 연산자 사용  
```java
boolean result = 좌항(객체) instanceof 우항(타입)

if (car instanceof Taxi) {
  Taxi taxi = (Taxi) car;
}
```

### 추상 클래스
객체를 직접 생성할 수 있는 클래스를 구현 클래스라고 하면, 해당 클래스의 **공통적인 특성**을 추출하여 선언한 클래스를 추상(abstract) 클래스라고 함.
+ 공통적인 특성은 필드와 메소드
+ 추상 클래스는 `new`연산자를 통해서 객체를 생성할 수 없음

#### 왜? 추상 클래스가 필요할까?
+ 구현 클래스들의 공통된 필드와 메소드 이름의 통일 // user or owner -> user로 통일
+ 구현 클래스 작성 시, 시간절약 - 상속이니... 당연.
+ 추상 클래스는 객체를 생성할 수 없으니... 구현 클래스의 공통된 (설계)**규격***을 정하는 역할  

#### 추상 클래스 선언
클래스 선언 시 `abstract` 키워드 사용
```java
public abstract class Car {
  // 필드
  // 생성자
  // 메소드
}
```

#### 추상 메소드와 오버라이딩
추상 클래스에서 메소드 이름은 통일 시켰는데, 행동이 각 구현 클래스마다 다를 경우, 추상 메소드 사용.  
추상 메소드는 선언부만 있고 실행 내용은 없어서, 자식 클래스에서 반드시 구현을 해야함.  
즉, 추상 메소드는 **구현강제**의 목적.
```java
public abstract class Animal {
  public sbstract void sound(); // {} 없음.
}

public class Dog extends Aniaml {
  @Override
  public void sound() { // 추상 메소드 재정의
    // 멍멍...
  }
}

public class Cat extends Aniaml {
  @Override
  public void sound() { // 추상 메소드 재정의
    // 야옹...
  }
}
```


## 06 인터페이스 (Interface)
역할은? 객체의 사용 방법을 정의, 객체의 사용 설명서
(dark) 상속은 기능의 확장이고, 인터페이스는 기능의 규격화로 볼수 있다.

### 인터페이스 선언
```java
public interface 인터페이스명 {
  // 상수
  [public static final] 타입 상수명 = 10;
  
  // 추상 메소드
  // - 구현 클래스에서 구현 해야 함
  [public abstract] 리턴타입 메소드명(매개변수, ...);
  
  // 디폴트 메소드
  // - 인스턴스 메소드로 구현 객체가 있어야 사용 가능. 
  // - 구현 클래스에서 재정의(Overriding) 가능
  [public] default 리턴타입 메소드명(매개변수, ...) { ... } // 구현가능
  
  // 정적 메소드
  // - 인터페이스로 호출 가능
  [public] static 리턴타입 메소드명(매개변수, ...) { ... } // 구현가능
}
```
[] 부분 생략 시, 컴파일러가 생성 함.

### 인터페이스 구현
#### 구현 클래스
```java
public class 구현클래스명 implements 인터페이스명 {
  // 인터페이스에 선언된 추상 메소드를 구현
}

// TODO: 예시 작성 하자~~~

// 만약 구현 클래스에서 인터페이스의 추상 메소드를 미 구현 시, 추상 클래스로 설정 해야 됨.
public abstract class 구현클래스명 implements 인터페이스명 {
  // 일부만 구현...
}
```

#### 익명 구현 객체
...  


#### 다중 인터페이스 구현 클래스
...  


### 인터페이스 사용
...  

### 타입 변환과 다형성
...  

### 인터페이스 상속
...  

### 디폴트 메소드와 인터페이스 확장
...   


## 07 중첩 클래스와 중첩 인터페이스 (Nested Class and Nested Interface)
중첩 클래스란?  

```java
class ClassName {
  class NestedClassName {}
}
```
+ 클래스안의 클래스 

왜? 사용하니...
+ 두 클래스만 관계가 있을 때, 클래스간 접근이 쉽다.
+ 외부에 불필요한 관계를 숨긴다.?

중첩 클래스 종류는?
+ 멈버 클래스
  + 인스턴스 멤버 클래스: `Class B`
  + 정적 멤버 클래스: `static Calss B`
+ 로컬 클래스: 메소드안에 클래스 정의

### 중첩 클래스와 중첩 인터페이스
... 

### 익명 객체
익명(anonymous) 객체는 이름이 없는객체로써 단독으로 생성할 수 없고
클래스를 생성하거나 인터페이스를 구현해야 한다.  
익명 객체는 **필드**의 초기값이나 **로컬 변수**의 초기값, **메소드 파라미터**로 주로 대입된다.  

그리고, 익명 객체를 로컬 변수로 사용 시, (즉 메소드 내에서 익명 객체 생성) 익명 객체 내부에서 
메소드의 파라미터 값이나 로컬 변수 사용할 경우, 이 변수들은 `final` 특성을 가진다. (즉, 읽기는 가능하나 쓰기는 안됨)

#### 익명 자식 객체 (상속)
```java
부모클래스 [필드|변수] = new 부모클래스(파라미터, ...) {
  // 필드
  // 메소드
}
```
자식 클래스를 재사용하지 않고, 단지 초기값 설정 용도로 사용한다.

#### 익명 구현 객체 (인터페이스)
```java
인터페이스 [필드|변수] = new 인터페이스() {
    // 인터페이스에 선언된 추상 메소드 구현
    // 필드
    // 메소드    
}
```
*example: <https://github.com/log4dark/going_merry/tree/master/No07-Nested-Class-and-Nested-Interface/No07-anonymous-object>*

## 08 예외 처리 (Exception)
...  


## 09 스레드 (Thread)
### 스레드 생성과 실행
#### Runnable 인터페이스의 구현 객체를 통한 스레드 생성과 실행

```java
// (1) Runnable 인터페이스 구현하여 객체 생성
class Task implements Runnable {
    public void run() {
      // 스레드가 실행할 코드
    }
}
Runnable task = new Task();
Thread thread = new Thread(task);

// (2) 또는 익명 구현 객체 생성
Thread thread = new Thread(new Runnable() {
    public void run() {
        // ....
    }
});

thread.start(); // run() 메소드 실행
```
*Runnable 인터페이스의 구현 객체를 만들고, Thread의 생성자로 전달 후, 
Thread 객체에서 `start()` 메소드 호출하면 `run()` 메소드가 실행 된다.*  
```java
Thread thread = new Thread(() -> {
    // 스레드가 실행할 코드
});
```
Runnable 인터페이스는 run() 메소드 하나만 정의되어 있기 때문에 함수적 인터페이스이다. 
그래서 람다 표현식 사용이 가능하다.

#### Thread 클래스 상속을 통한 스레드 생성과 실행
```java
// (1) Thread 클래스 상속하여 객체 생성
public class Task extends Thread() {
    public void run() {
        // ...
    }
}
Thread thread = new Task();

// (2) 또는 익명 (하위) 객체 생성
Thread thread = new Thread(new Thread() {
    public void run() {
        // ...
    }
});

thread.start(); // run() 메소드 실행 
```
*example: <https://github.com/log4dark/going_merry/tree/master/No09-Thread/No09-thread-create>*

#### 스레드의 이름
```java
thread.setName("스레드 이름");
thread.getName();
```
setName()과 getName()은 Thead 객체의 참조가 필요하다. 
스레드 객체의 참조가 없을 때, 정적 메소드 currentThread()로 현재 스레드의 참조를 얻을 수 있다.
```java
Thread thread = Thread.currentThred();
```

#### 스레드 Priority 설정
```java
thread.setPriority(우선순위);

// Constant 
thread.setPriority(Thread.MAX_PRIORITY); // 10
thread.setPriority(Thread.NORM_PRIORITY); // 5 
thread.setPriority(Thread.MIN_PRIORITY); // 5 
```
우선순위는 1 ~ 10이고, 10이 가장 높다.  

### 임계 영역(Critical Section) 설정 방법
자바에서 임계 영역 설정을 위해서 동기화(synchronized) 메소드와 동기화 블록을 제공한다.
```java
// 동기화 메소드 설정
public synchronized void increment() {
    // 임계 영역 - 단 하나의 스레드만 실행
}

// 동기화 블록 설정
public void increment() {
    // 여러 스레드 실행 가능
    synchronized(공유객체) { // 공유 객체가 객체 자신이면 this을 넣을수 있다.
        // 임계 영역 - 단 하나의 스레드만 실행 
    }
    // 여러 스레드 실행 가능
}
```
메소드 선언에 `synchronized` 키워드 설정 시, 메소드 전체가 임계 영역이 되고, 
일부 내용만 임계 영역으로 만들고 싶으면 동기화(synchronized) 블록을 만들되면 돤다.


### ref
+ https://codechacha.com/ko/java-atomic-types/

## 10 제너릭 (Generic)
제네릭(Generic) 은 클래스, 인터페이스, 메서드등의 **타입**을 **파라미터로** 사용할 수 있게 해주는 역할을 한다.
...  


## 11 자바 API (library)

## java.lang  
### Class 클래스  
클래스와 인터페이스의 메타 데이터인 클래스 이름, 생성자 정보, 필드 정보, 메소드 정보등을 관리 한다. 

#### Class 객체 얻기 (getClass(), forName())
Class 객체를 얻기 위해서 Object 클래스가 가지고 있는 `getClass()` 메소드를 이용 한다.
```java
Class clazz = obj.getClass();
```  

`getClass()` 메소드는 해당 클래스로 객체가 생성되었을 때 사용할 수 있는데, 
객체를 생성하기 전에는 정적 메소드인 `forName()`을 이용해야 한다.  
```java
try {
    Class clazz = Class.forName(String className);
} catch (ClassNotFoundExcepton e) {
}
```  

#### 리플렉션 (getDeclaredConstructors(), getDeclaredFields(), getDeclaredMethods())
리플렉션(Reflection)이란? 객체를 통해서 클래스의 생성자, 필드, 메소드 정보를 분석하는 기법이다.  
Class 객체는 리플렉션을 위해 getDeclaredConstructors(), getDeclaredFields(), getDeclaredMethods()를 제공한다.  
```java
Constructor[] constructors = clazz.getDeclaredConstructors();
Field[] fields = clazz.getDeclaredFields();
Method[] methods = clazz.getDeclaredMethods();
```
그리고 Constructor, Field, Method 클래스는 java.lang.reflect 패키지에 포함되어 있다.  

#### 동적 객체 생성 (newInstance()) 
컴파일 타임이 아닌, 런타입 시에 클래스를 선택해야 하는 경우, Class 객체를 이용하여 동적으로 선택된 클래스의 객체를 생성할 수 있다.  
```java
try {
    Class clazz = Class.forName("Class Name");
    Object obj = clazz.newInstance();
} catch (ClassnotFoundException e) {
} catch (InstantiationException e) { // 클래스가 추상 클래스이거나 인터페이스 경우 발생
} catch (IllegalAccessException e) { // 클래스나 생성자가 접근 제한자로 인해 접근할 수 없을 경우 발생
} 
```

`newInstance()` 메소드의 리턴 타입은 Object 이므로 이것을 원래 클래스 타입으로 강제 타입 변환 해야만 사용할 수 있는데, 
클래스 타입을 모를 경우, 인퍼에시를 통해서 해결을 할 수 있다.

예를 들어서 특정 메시지 수신 시, 아래와 같이 인터페이스 및 구현 클래스를 정의하고 동적 객체 생성 후, 강제 타입 변환해서 사용할 수 있다.
```java
// 인터페이스와 구현 클래스
public interface Message() {
}
public class CreateMessage() implements Message {
}
public class DeleteMessage() implements Message {
}

// 동적 객체 생성
public void receive(String messageName) {
  // ... 
  Class clazz = Class.forName(messageName);
  Message message = (Message) clazz.newInstance(); // CreateMessage 또는 DeleteMessage 객체 생성
}
```

## java.util (컬렉션 프레임워크) 
자료구조를 구현, 주요 인터페이스는 List, Set, Map 이고, 각 인터페이스를 구현한 구현 클래스가 존재   
  
**Collection**: 컬렉션의 최상위 인터페이스
+ **List**: 순서 유지 하고, 중복 저장 가능
  + ArrayList: 일반 배열 형태이고 추가/삭제 시, 원소를 밀고 당기고 함
  + Vector: 일반 배열 형태 & <U>Thread Safe</U>
  + LinkedList: 일반 리스트 형태, Node/Link
+ **Set**: 순서 유지 하지 않고, 중복 저장 안 됨
  + HashSet
  + TreeSet: Tree 구조의 Set, *검색 시 시간복잡도 Log(N) 이겠네...*
+ **Map**: Key/Value 형태, Key는 중복 저장 안 됨
  + HashMap
  + Hashtable: HashMap과 동일한 내부 구조 & <U>Thread Safe</U>
  + Properties: Key=Value 형태의 프로퍼티(*.properties) 파일 읽을 때 사용
  + TreeMap: Tree 구조의 Map

### List 컬렉션
순서 유지 하고, 중복 저장 가능
+ **객체 추가**
  + `boolean add(E e)`: 맨 끝에 추가
  + `void add(int index, E e)`: 해당 인덱스에 객체 추가, 해당 인덱스에 객체 존재 시 밀어버림
  + `set(int index, E e)`: 덮어씀
+ **객체 검색**
  + `boolean contains(Object o)` : 저장되어 있는지 여부
  + `E get(int index)`
  + `boolean isEmpty()`
  + `int size()`
+ **객체 삭제**
  + `void clear()` : 저장되어 있는 모든 객체를 삭제
  + `E remove(int index)`
  + `boolean remove(Object o)`  

#### ArrayList
일반 배열 형태, default로 10개 저장 공간, 초기 생성 시 설정 가능
```java
List<String> list = new ArrayList<>();
List<String> list = new ArrayList<>(30); // 30개 저장 공간 생성

```  
`Arrays.asList()` 사용하여 고정된 객체를 통해서 List 생성 가능
````java
List<T> list = Arrays.asList(T... a);

// Interger 타입 파라미터를 순차적으로 설정
List<Integer> list1 = Arrays.asList(1, 2, 3);

// String[] 배열을 파라미터로 설정
String[] str = {"dark", "penny", "ji"};
List<String> lists2 = Arrays.asList(str);
````  

#### Vector
ArrayList와 동일한 내부구조, 동기화된(synchronized) 메소드로 구성되어 있어 **Thread Safe**

#### LinkedList
일반 리스트 형태, 노드를 가지고 Doubly Linked List 형태 인듯  

### Set 컬렉션 
순서 유지 하지 않고, 중복 저장 안 됨, 수학의 집합과 유사    
+ **객체 추가**
  + `boolean add(E e)`: 중복 저장 시 false 리턴 
+ **객체 검색**
  + `boolean contains(Object o)` : 저장되어 있는지 여부
  + `boolean isEmpty()`
  + `Iterator<E> iterator()` : 저장된 객체를 한 번씩 가져오는 반복자 리턴
  + `int size()`
+ **객체 삭제**
  + `void clear()` : 저장되어 있는 모든 객체를 삭제
  + `boolean remove(Object o)`  

반복자는 Iterator 인터페이스를 구현한 객체, `iterator()` 메소드를 호출하여 얻을 수 있고, 
아래의 메소드가 정의 되어 있음
+ `boolean hasNex()` : 가져올 객체가 있으면 true, 없으면 false
+ `E next()` : 하나의 객체를 가져옴
+ `void remove()` 

```java
Set<String> set = ...;
Iterator<String> iterator = set.iterator();  
while(iterator.hasNext) {
    String str = iterator.next();
    if (str.equals("dark")) {
        iterator.remove();
    }
}

// for loop
for (String str : set) {
}
```  

#### HashSet
```java
Set<E> set = new HashSet<>();
```  
HashSet은 *(Set 이니까)* 동일한 객체를 중복 저장하지 않고, 동일한 객체 판단 로직은 아래와 같음
```java
if ((hashCode() 리턴값 같음) && (equals() 리턴값 true)) {
    // 동등 객체로 저장하지 않음
} else {
    // 서로 다른 객체로 저장
}
```  

### Map 컬렉션  
Key / Value 로 구성, Key 는 중복 저장 안되고, 동일 Key로 저장 시 덮어씀   

+ **객체 추가**
  + `V put(K key, V value)`
+ **객체 검색**
  + `boolean containsKey(Object key)` : 키의 존재 여부
  + `boolean containsValue(Object value)` : 값의 존재 여부
  + `Set<Map.Entry<K,V>> entrySet()` : 키와 값의 쌍으로 구성된 <U>모든</U> Map.Entry 객체를 Set 으로 담아서 리턴
  + `V get(Ojbect key)`
  + `boolean isEmpty()`
  + `Set<K> keySet()` : <U>모든</U> 키를 Set 객체에 담아서 리턴
  + `int size()`
  + `Collection<V> values()` : 저장된 <U>모든</U> 값을 Collection 에 담아 리턴
+ **객체 삭제**
  + `void clear()` : 저장되어 있는 모든 Map.Entry(Key와 Value)를 삭제 
  + `V remove(Object key)`

저장된 모든 Key와 Value 출력하는/얻는 방법
```java
Map<String, String> map = new HashMap<>();

// keySet() 이용
Set<String> keys = map.keySet();
for (String key : keys) {
    System.out.printf("keySet: key(%s) value(%s)\n", key, map.get(key));
}

// entrySet() 이용
Set<Map.Entry<String,String>> entrySet = map.entrySet();
for (Map.Entry<String,String> mapEntry : entrySet) {
    System.out.printf("entrySet: key(%s) value(%s)\n",mapEntry.getKey(), mapEntry.getValue());
}
```  

#### HashMap
HashMap의 키로 사용할 (사용자 정의) **객체**는 `hashCode()`와 `equals()` 메소드를 재정의 해서 동등 객체가 될 조건을 정해야 함.
동등 객체의 조건은 `hashCode()` 리턴값이 같고, `equals()` 리턴값이 `true`일 때 이다.  
```java
Map<K,V> map = new HashMap<>();
``` 
키와 값의 타입은 기본타입(byte, short, int, float, double, boolean, char)은 사용할 수 없고, 
클래스 및 인터페이스 타입만 가능  
```java
Map<String,Integer> map = new HashMap<>();
```  
사용자 정의 객체인 `Student`를 Key로 하고 점수를 저장하는 HashMap 사용 시, 
학번과 이름이 동일한 `Student` 객체를 동일한 키로 간주하기 위해서 `hashCode()`와 `equals()`를 재정의 해야 한다.  
```java
public class Student {
    public int sno;
    public String name;

    public Student(int sno, String name) {
        this.sno = sno;
        this.name = name;
    }

    public boolean equals(Object obj) { // 학번과 이름이 같다면 true 리턴
        if (obj instanceof Student) {
            Student student = (Student) obj;
            return (sno == student.sno) && (name.equals(student.name));
        } else {
            return false;
        }
    }

    public int hashCode() { // 학번과 이름이 같다면 동일한 값을 리턴
        return sno + name.hashCode();
    }
}
```  

#### Hashtable
HashMap과 동일한 내부 구조를 가지고, Thread Safe 함  
```java
Map<K, V> map = new Hashtable<>();
```  

#### Properties
Properties는 Hashtable의 하위 클래스이고, 프로퍼티(*.properties) 파일을 읽을 때 주로 사용.  
프로퍼티 파일은 Key=Value 형태의 텍스트 파일로 ISO 8859-1 문자셋으로 저장되고, 한글은 유니코드(Unicode)로 변환되어 저장 됨.
```java
// 디렉토리 경로 (/w IntelliJ)
/src/main
        /java/com.log4dark.going_merry/MyApp.java
        /resources/application.properties
/target/classes
        /com/log4dark/going_merry/MyApp.class
        application.properties
        
// application.properties
tcp.ip=127.0.0.1
tcp.port=9100
tcp.timeout-sec=3
        
// 프로퍼티 파일 읽기
Properties properties = new Properties(); // 프로퍼티 객체 생성
try {
    // application.properties loading...
    properties.load(new FileReader(ClassLoader.getSystemResource("application.properties").getPath()));
} catch (Exception e) {
    System.out.printf("e: %s\n", e.toString());
}

String ip = properties.getProperty("tcp.ip");
String port = properties.getProperty("tcp.port");
String timeoutSec = properties.getProperty("tcp.timeout-sec");
```  

### LIFO와 FIFO 컬렉션
LIFO(Last In First Out) 구조인 스택(Stack)과 FIFO(First in First Out) 구조인 큐(Queue) 제공 

#### Stack
Stack <U>클래스</U>의 주요 메소드
+ E push(E item)
+ E peek(): 스택의 맨 위 객체를 가져오고, 객체를 스택에서 제거하지 않음
+ E pop(): 스택의 맨 위 객체를 가져오고, 객체를 스택에서 제거
+ boolean isEmpty()

```java
Stack<E> stack = new Stack<>();
```

#### Queue
Queue <U>인터페이스</U> 주요 메소드
+ boolean offer(E e): 주어진 객체를 enqueue
+ E peek(): 객체를 하나 가져오고, 객체를 큐에서 제거하지는 않음
+ E poll(): 객체를 하나 가져오고, 객체를 큐에서 제거
+ boolean isEmpty()

```java
Queue<E> queue = new LinkedList<>();
```  

### 컬렉션 동기화 (Thread Safe)
Vector와 Hashtable은 Thread Safe 하지만, ArrayList, HashSet, HashMap은 멀티스레드에 안전하지 않음.  
해당 컬렉션을 `Collections`의 `synchronizedXXX()` 메소드를 사용하여 동기화 가능 
+ List<T> synchronizedList(List<T> list)
+ Set<T> synchronizedSet(Set<T> set)
+ Map<K,V> synchronizedMap(Map<K,V> map)

```java
Map<K,V> map = Collections.synchronizedMap(new HashMap<K,V>());
```
But...  
동기화된(synchronized) 컬렉션은 10개 요소가 있을 때, 1개를 처리할 경우 (10개) 전체를 lock을 한다.   
java.util.concurrent 패키지의 `ConcurrentHashMap`과 `ConcurrentLinkedQueue`는 처리하는 요소만 lock을 부분적으로 수행.  
*즉, java.util.concurrent 패키지의 컬렉션들이 성능이 좋겠지~~~*  
```java
Map<K,V> map = new ConcurrentHashMap<K,V>();
Queue<E> queue = new ConcurrentLinkedQueue<E>();
```

## java.time  
...  

## 12 I/O 입출력
...  


## 13 자바 네트워킹
...


## Reference 
> + ...   

[^1]: https://docs.oracle.com/javase/tutorial/java/javaOO/enum.html
[^2]: https://stackoverflow.com/questions/2885385/what-is-the-difference-between-an-instance-and-an-object