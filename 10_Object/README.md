# 10장 객체 리터럴

<br>
<br>

## 10.1 객체란?

```
자바스크립트를 구성하는 거의 "모든 것" (원시 값을 제외한 나머지 값, 함수 배열, 정규 표현식 등)으로 다양한 타입의 값을 하나의 단위로 구성한 복합적인 자료구조
```

```js
// 객체는 프로퍼티와 메서드로 구성된 집합

var counter = {
  num: 0, // 프로퍼티 : 객체의 상태를 나타내는 값(data)
  increase: function () {
    this.num++; // 메서드 : 프로퍼티(상태 데이터)를 참조하고 조작할 수 있는 동작(behavior)
  },
};
```

📄 함수로 객체를 생성하기도 하며 함수 자체가 객체이기도 하다.

<br>
<br>

## 10.2 객체 리터럴에 의한 객체 생성

C++, 자바 같은 클래스 기반 객체 지향 언어는 **클래스를 사전에 정의**, 필요 시점에 new 연산자와 함께 **생성자를 호출하여 인스턴스를 생성**하는 방식으로 객체 생성

> 📄 instance : 클래스에 의해 생성되어 메모리에 저장된 실체 (객체지향 프로그래밍에서 객체는 클래스와 인스턴스를 포함한 개념)

자바스크립트는 프로토타입 기반 객체 지향 언어로서 클래스 기반 객체지향 언어와는 달리 다양한 객체 생성 방법 지원

- 객체 리터럴 (보편적)

  JS의 유연&강력함을 대표하는 객체 생성 방식

- Object 생성자 함수
- 생성자 함수
- Object.create 메서드
- 클래스 (ES6)

<br>
<br>

## 10.3 프로퍼티

**객체는 프로퍼티의 집합, 프로퍼티는 키와 값으로 구성**

- **프로퍼티 키** : 빈 문자열을 포함하는 모든 문자열 또는 심벌 값 (식별자 역할)

- **프로퍼티 값** : 자바스크립트에서 사용할 수 있는 모든 값

```js
// 네이밍 규칙 준수하는 프로퍼티 키 사용할 것을 권장
var person = {
  firstName: "Ung-mo",
  "last-name": "Lee", // 번거로움
};
console.log(person); // {firstName : "Ung-mo", last-name : "Lee"}
```

이미 존재하는 프로퍼티 키 선언 → 에러 발생하지 않고, 나중에 선언한 프로퍼티가 덮어씀

<br>
<br>

## 10.4 메서드

자바스크립트 함수는 일급 객체이다. 따라서 함수는 값으로 취급 → 프로퍼티 값으로 사용할 수 있다.

프로퍼티 값이 함수일 경우 일반함수와 구분하기 위해 **_메서드_** 라고 부름

<br>
<br>

## 10.5 프로퍼티 접근

```js
var person = {
  name: "Lee",
};

// 마침표 표기법에 의한 프로퍼티 접근
console.log(person.name); // Lee

// 대괄호 표기법에 의한 프로퍼티 접근
// 프로퍼티 키는 반드시 따옴표로 감싼 문자열이어야함
console.log(person["name"]); // Lee
```

<br>
<br>

## 10.6 프로퍼티 값 갱신

이미 존재하는 프로퍼티에 값을 할당하면 프로퍼티 값이 갱신됨

<br>
<br>

## 10.7 프로퍼티 동적 생성

존재하지 않는 프로퍼티에 값 할당 → 프로퍼티가 동적으로 생성되어 추가, 값이 할당 됨

<br>
<br>

## 10.8 프로퍼티 삭제

delete 연산자는 객체의 프로퍼티 삭제

<br>
<br>

## ES6에서 추가된 객체 리터럴의 확장 기능

<br>

### 10.9.1 프로퍼티 축약 표현

```js
//ES5
var x = 1,
  y = 2;

var obj = {
  x: x,
  y: y,
};

//ES6 - 변수를 프로퍼티 값으로 사용 → 변수이름 프로퍼티 키가 동일한 이름일 때 프로퍼티 키 생략 가능
var x = 1,
  y = 2;

var obj = { x, y };
```

<br>

### 10.9.2 계산된 프로퍼티 이름

ES5) 계산된 프로퍼티 이름으로 프로퍼티 키를 동적 생산할때는 객체 리터럴 외부에서 대괄호 표기법 사용

```js
// ES6에서는 객체 리터럴 내부에서도 계산된 프로퍼티 이름으로 프로퍼티 키를 동적 생성 가능

const prefix = "prop";
let i = 0;

// 객체 리터럴 내부에서 계산된 프로퍼티 이름으로 프로퍼티 키 동적 생성
const obj = {
  [`${prefix}-${++i}`]: i,
  [`${prefix}-${++i}`]: i,
  [`${prefix}-${++i}`]: i,
};

console.log(obj); // {prop-1: 1, prop-2: 2, prop-3: 3}
```

<br>

### 10.9.3 메서드 축약 표현

ES5에서 메서드 정의 - 프로퍼티 값으로 함수 할당

ES6에서 메서드 정의 - function 키워드 생략한 축약 표현

ES6의 메서드 축약 표현으로 정의한 메서드는 프로퍼티에 할당한 함수와 다르게 동작 (26.2 "메서드"에서 자세히)

<br>