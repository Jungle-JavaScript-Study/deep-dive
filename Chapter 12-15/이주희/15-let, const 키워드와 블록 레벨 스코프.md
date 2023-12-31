## 1. 함수 레벨 스코프 & 블록 레벨 스코프
- 함수 외부에서 var 변수는 코드 블록 내에서 선언해도 모두 전역 변수가 된다.
- let 변수는 모든 코드 블록을 지역 스코프로 인정하는 블록 레벨 스코프를 따른다.

<br/>

## 2. 변수 호이스팅
- let 변수는 변수 호이스팅이 **발생하지 않는 것처럼** 동작한다.
- var 변수는 런타임 이전에 암묵적으로 선언과 초기화가 진행된다.
  - 따라서 변수 선언문 이전에 변수에 접근해도 스코프에 변수가 존재하기 때문에 에러가 발생하지 않고 undefined를 반환한다.
- let 변수는 선언 단계와 초기화 단계가 분리되어 진행된다.
  - 런타임 이전에 암묵적으로 선언 단계가 먼저 실행되지만, 초기화 단계는 변수 선언문에 도달했을 때 실행된다.
  - 초기화 단계가 실행되기 이전에 변수에 접근하려고 하면 ReferenceError가 발생한다.
  - 스코프의 시작 지점부터 초기화 시작 지점까지 변수를 참조할 수 없으며, 이 구간을 일시적 사각지대(Temporal Dead Zone, TDZ)이라고 한다.

### 2-1. let 변수의 변수 호이스팅
```javascript
let foo = 1;

{
  console.log(foo); // ReferenceError: Cannot access 'foo' before initialization
  let foo = 2;
}
```
- let 변수가 호이스팅이 발생하지 않는다면 전역변수 foo의 값을 출력하겠지만,
- let 변수도 여전히 호이스팅이 발생하기 때문에 참조 에러 ReferenceError가 발생한다.
- JS는 let, const를 포함해서 모든 선언(let, const, var, function, function*, class 등)을 호이스팅한다.
  - 단, ES6에서 도입된 let, const, class를 사용한 선언문은 호이스팅이 발생하지 않는 것처럼 동작하는 것이다.

<br/>

## 3. 전역 객체와 let
- var 키워드로 선언한 전역 변수와 전역 함수, 그리고 선언하지 않은 변수에 값을 할당한 암묵적 전역은 전역 객체 window의 프로퍼티가 된다.
- let 키워드로 선언한 전역 변수는 전역 객체의 프로퍼티가 아니다.
  - let 전역 변수는 보이지 않는 개념적인 블록(전역 렉시컬 환경의 선언적 환경 레코드, 23장에 나옴) 내에 존재하게 된다.
