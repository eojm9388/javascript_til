# 데이터 타입

## 숫자 타입

자바스크립트는 하나의 숫자 타입만 존재한다.

자바스크립트의 숫자 타입은 정수만을 위한 타입이 없고 모든 수를 실수로 처리한다. 이는 정수로 표시된다 해도 사실은 실수라는 것을 의미한다. 따라서 정수로 표시되는 수끼리 나누더라도 실수가 나올 수 있다.

```javascript
console.log(1 === 1.0); // true
```

숫자 타입은 추가적으로 세 가지 특별한 값도 표현할 수 있다.

- `Infinity` : 양의 무한대
- `-Infinity`: 음의 무한대
- `NaN`: 산술 연산 불가

```javascript
console.log(10 / 0); // Infinity
console.log(10 / -0); // -Infinity
console.log(1 * 'String'); // NaN
```

자바스크립트는 대소문자를 구별하므로 `NaN`을 NAN, Nan, nan과 같이 표현하면 에러가 발생하므로 주의하기 바란다. 자바스크립트 엔진은 NAN, Nan, nan을 값이 아닌 식별자로 해석한다.

## 문자열 타입

문자열 타입은 텍스트 데이터를 나타내는 데 사용한다.

문자열은 작은따옴표(`' '`), 큰따옴표(`" "`) 또는 백틱(` `` `)으로 텍스트를 감싼다. 자바스크립트에서 가장 일반적인 표현법은 작은따옴표를 사용하는 것이다.

```javascript
var string;
string = '문자열';
string = '문자열';
string = `문자열`;
```

만약 문자열을 따옴표로 감싸지 않으면 자바스크립트 엔진은 키워드나 식별자 같은 토큰으로 인식한다.

```javascript
// 따옴표로 감싸지 않은 hello를 식별자로 인식한다.
var string = hello; // ReferenceError
```

## 템플릿 리터럴

템플릿 리터럴은 멀티라인 문자열, 표현식 삽입, 태그드 템플릿 등 편리한 문자열 처리 기능을 제공한다.

템플릿 리터럴은 일반 문자열과 비슷해 보이지만 백틱(` `` `)을 사용한다.

### 1. 멀티라인 문자열

일반 문자열 내에서는 줄바꿈이 허용되지 않는다.

```javascript
var str = 'hello
world';
// SyntaxError
```

따라서 일반 문자열 내에서 줄바꿈 등의 공백을 표현하려면 백슬래시(`\`)로 시작하는 `이스케이프 시퀀스`를 사용해야 한다.

일반 문자열과 달리 템플릿 리터럴 내에서는 이스케이프 시퀀스를 사용하지 않고도 줄바꿈이 허용되며, 모든 공백도 있는 그대로 적용된다.

```javascript
var template = `<ul>
  <a href="#">Home</a>
</ul>`;

console.log(template);
/*
<ul>
  <a href="#">Home</a>
</ul>
*/
```

### 2. 표현식 삽입

템플릿 리터럴 내에서는 표현식 삽입을 통해 간단히 문자열을 삽입할 수 있다.

```javascript
var first = 'Jimin';
var last = 'Eo';

console.log(`My name is ${first} ${last}.`); // My name is Jimin Eo
```

표현식을 삽입하려면 `${ }`으로 표현식을 감싼다. 이때 표현식의 평가 결과가 문자열이 아니라도 문자열로 타입이 강제 변환되어 삽입된다.

> 표현식 삽입은 반드시 템플릿 리터럴 내에서 사용해야 한다. 템플릿 리터럴이 아닌 일반 문자열에서의 표현식 삽입은 문자열로 취급된다.

## 불리언 타입

불리언 타입의 값은 논리적 참, 거짓을 나타내는 `true`와 `false`뿐이다.

```javascript
var foo = true;
console.log(foo); // true

var foo = false;
console.log(foo); // false
```

## undefined 타입

`var`키워드로 선언한 변수는 암묵적으로 `undefined`로 초기화 된다.

`undefined`는 개발자가 의도적으로 할당하기 위한 값이 아니라 자바스크립트 엔진이 변수를 초기화할 때 사용하는 값이다.

## null 타입

프로그래밍 언어에서 `null`은 변수에 값이 없다는 것을 의도적으로 명시할 때 사용한다.

변수에 `null`을 할당하는 것은 이전에 참조하던 값을 더 이상 참조하지 않겠다는 의미이다.

## 데이터 타입의 필요성

#### 1. 데이터 타입에 의한 메모리 공간의 확보와 참조

- 데이터 타입에 따라 값을 저장하기 위한 메모리 공간의 크기가 다르다.
- 값의 데이터 타입에 따라 정해진 크기의 메모리 공간을 확보한다.

#### 2. 데이터 타입에 의한 값의 해석

- 컴퓨터는 2진수로 데이터를 처리한다.
- 메모리에 저장된 값은 데이터 타입에 따라 다르게 해석될 수 있다.
- 이진수 `0100 0001`을 숫자로 나타내면 `65`이지만 문자열로 해석하면 `A`이다.

## 동적 타이핑

정적 타입 언어는 변수를 선언할 때 데이터 타입을 사전에 선언해야 한다.

자바스크립트는 정적 타입 언어와는 다르게 변수를 선언할 때 타입을 선언하지 않는다. 다만 `var, let, const`같은 키워드를 사용해 변수를 선언할 뿐이다.

어떠한 데이터 타입도 변수에 할당할 수 있다.

```javascript
var foo;
console.log(typeof foo); // undefined

foo = 3;
console.log(typeof foo); // number

foo = 'Hello';
console.log(typeof foo); // string

foo = true;
console.log(typeof foo); // boolean

foo = null;
console.log(typeof foo); // object

foo = Symbol();
console.log(typeof foo); // symbol

foo = {};
console.log(typeof foo); // object

foo = [];
console.log(typeof foo); // object

foo = function () {};
console.log(typeof foo); // function
```

> 자바스크립트의 변수는 선언이 아닌 할당에 의해 타입이 결정 된다. 그리고 재할당에 의해 변수의 타입은 언제든지 동적으로 변할 수 있다.
