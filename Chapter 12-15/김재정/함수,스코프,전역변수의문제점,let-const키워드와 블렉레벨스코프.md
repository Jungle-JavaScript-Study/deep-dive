**12.1 함수란?**

함수는 일련의 과정을 문으로 구현하고 코드 블록으로 감싸서 하나의 실행 단위로 정의한 것이다.

함수 내부로 입력을 전달받는 변수를 **매개변수**, 입력을 **인수**, 출력을 **반환값**이라 한다.

함수는 함수 정의를 통해 생성하고 함수 호출을 통해 실행을 시킨다. 아래는 간단한 예시

```jsx
function foo(){
	console.log("Hello World!");
} // 정의

foo(); //호출
```

**12.2 함수를 사용하는 이유**

1. 함수는 몇번이든 호출할 수 있어 코드의 재사용성 측면에서 매우 유용하다.
2. 코드의 중복을 억제, 재사용성을 높여 유지보수의 편의성측면에서 유용하다.
3. 실수가 줄어들어 코드의 신뢰성이 올라간다.
4. 코드의 가독성을 향상 시킨다.

**12.3 함수 리터럴**

함수의 리터럴 구성요소는 다음과 같다.

1. 함수이름
    1. 함수 이름은 식별자이다.
    2. 몸체 내부에서만 참조할 수 있다.
    3. 이름은 생략할 수 있는데 이를 무명함수라 하고 반대의 개념은 기명함수 하고 한다.
2. 매개변수 목록
    1. 0개 이상의 매개변수를 소괄호로 감싸고 쉼표로 구분
    2. 함수 몸체 내에서 변수와 동일하게 취급된다.
3. 함수몸체
    1. 함수가 호출되었을 때, 일괄적으로 실행될 문들을 하나의 실행 단위로 정의한다.

**12.4함수 정의**

함수는 함수 이름으로 호출하는 것이 아니라 함수 객체를 가르키는 식별자로 호출한다.

1. 함수 선언문(Function Declaration):

```jsx

function add(x, y) {
    return x + y;
}
console.log(add(1, 2));  // 출력: 3

```

- 함수 선언문은 함수 이름을 생략할 수 없다.
- 표현식이 아닌 문으로, 변수에 할당할 수 없다.
- 식별자가 없어 암묵적 변환으로 함수명을 식별자로 변환되어 그곳에 함수 객체를 할당하여 사용된다.

1. 함수 표현식(Function Expression):

JS 함수는 값처럼 변수에 할당할 수 있어성질을 갖는 객체 즉, 일급 객체이다.

```jsx

let multiply = function(x, y) {
    return x * y;
}; 
console.log(multiply(2, 3));  // 출력: 6

```

- 리터럴의 이름을 생략할 수 있다.
- 선언문과 다르게 “표현식인 문”으로 변수에 할당이 가능하다.

1. Function 생성자 함수:

```jsx

let divide = new Function('x', 'y', 'return x / y;');
console.log(divide(6, 3));  // 출력: 2

```

1. 화살표 함수(Arrow Function):

```jsx

let subtract = (x, y) => x - y;
console.log(subtract(5, 2));  // 출력: 3

```

**함수 호이스팅?**

함수 선언문이 코드의 선두로 끌어 올려진 것처럼 동작하는 자바스크립트 고유의 특징을 함수 호이스팅이라 한다.

변수 할당문의 값은 할당문이 실행되는 시점, 즉 런타임에 평가되므로 함수 표현식의 함수 리터럴도 할당문이 실행되는 시점에 평사되어 함수 객체가 된다.

따라서, 함수 표현식으로 함수를 정의하면 함수 호이스팅이 발생하는 것이 아니라 변수 호이스팅이 발생한다.

**12.5함수 호출**

일반객체는 호출할 수 없지만 함수는 호출할 수 있다.

- 인수는 함수를 호출할 때 지정하며 개수와 타입에 제한이 없다.
- 자바스크립트는 동적 타입의 언어다. 따라서 자바스크립트 함수는 매개변수의 타입을 사전에 지정할 수 없다.
- 제한은 없지만 최대 갯수 6개를 넘기지 않는것을 지양하고 있다.

**12.참조에 의한 전달과 외부 상태의 변경**

객체 타입의 인수는 참조값이 복사되어 매개변수에 전달되기 때문에 함수 몸체에서 참조값을 통해 객체를 변경할 경우 원본이 훼손된다. 다시 말해 외부 상태, 즉 함수 외부에서 함수 몸체 내부로 전달한 참조값에 의해 원본 객체가 변경되는 부수 효과가 발생한다.

부수 효과가 발생할경우 상태 변화를 추적하기 어려워 짐으로 아래와 같은 해결책을 권장한다.

1. 객체의 의도치 않은 변경을 추적하기 위해 옵저버 패턴으로 객체를 참조하는 모든 이들에게 변경사실을 통지한다.
2. 객체를 불변객체로 만들어 사용한다.
3. 외부 상태를 변경하지 않고 외부상태에 의존하지 않는 함수를 순수함수라고 한다. 순수함수를 통해 부수효과를 최대한 억제 시킨다.

**12.7 다양한 함수의 형태**

- 즉시 실행함수
    
    ```jsx
    (function() {
        var privateVar = "I'm private var";
        console.log(privateVar);  // 출력: I'm private var
    })();
    
    console.log(privateVar);  // ReferenceError: privateVar is not defined
    ```
    
    즉시 실행 함수는 자체 스코프를 생성하고 **`privateVar`** 변수를 그 스코프 안에 캡슐화 합니다. 따라서 **`privateVar`**는 즉시 실행 함수 외부에서 접근할 수 없습니다. 이런 특성 때문에 즉시 실행 함수는 전역 네임스페이스의 오염을 방지하고, 코드를 모듈화하는데 유용합니다.
    
- 재귀함수
    
    스택오버플로우는 함수의 호출 스택이 너무 커져서 메모리를 초과할때 발생한다. 아래와 ㄱㅏㅌ은 상황을 방지할 수 있도록 종료조건을 항상 정의해야한다.
    
    ```jsx
    function recursive() {
        recursive();
    }
    
    recursive(); // RangeError: Maximum call stack size exceeded
    ```
    
- 콜백함수
    - 함수를 매개변수로 받아서 다른 함수에서 사용하는 함수를 '고차 함수'라고 합니다. 이렇게 매개변수로 전달된 함수를 '콜백 함수'라고 합니다.
    간단하게 말하자면, 다른 함수를 '입력'으로 받아서 실행하는 함수가 고차 함수입니다. 그리고 이 고차 함수에게 '입력'으로 들어가는 함수가 콜백 함수입니다.
- 순수함수와 비순수 함수
    - 외부상태에 의존하지 않고 인수가 전달되면 언제나 동일한 값을 반환하는 함수이다.
    - 외부상태에 의존하며 외부상태에 따라 반환값이 달라지는 함수이다. 따라서 부수효과가 발생할 수 있다.

**13.1 스코프란?**

모든 식별자는 자신이 선언된 위치에 의해 다른 코드가 식별자 자신을 참조할 수 있는 유효범위가 결정된다.

이를 스코프라고 한다. 즉, 스코프는 식별자가 유효한 범위를 말한다.

```jsx
var x = "global"
function foo(){
	var x = "local"
	console.log(x); 
}
foo(); //local
console.log(x); //global
```

같은 이름중 어떤 변수를 참조해야할지 결정하는것을 식별자 결정이라고 한다.

스코프는 자바스크립트 엔진이 식별자를 검색할 떄 사용하는 규칙 이라고도 할 수 있다.

**13.2 스코프의 종류**

- 전역
    - 전역변수는 어디서든지 참조할 수 있다.
- 지역
    - 함수 몸체 내부를 말한다.
    - 지역 변수는 자신의 지역 스코프와 하위 지역 스코프에서 유효하다.

**13.3 스코프 체인**

- 스코프가 함수의 중첩에 의해 계층 구조를 갖는다.
    - 변수를 참조할 때 자바스크립트 엔진은 스코프 체인을통해 변수를 참조하는 코드의 스코프에서 시작하여 상위 스코프 방향으로 이동하며 선언된 변수를 검색한다.

**13.4 함수 레벨 스코프**

코드 블록이 아닌 함수에 의해서만 지역 스코프가 생성된다.

이러한 특성을 블록레벨 스코프하고 한다, (var 제외 해당 변수는 함수레벨스코프임)

**13.5 렉시컬 스코프**

- 자바스크립트는 함수를 어디서 정의했는지에 따라 상위 스코프가 결정된다.
- 함수가 호출된 위치는 상위 스코프 결정에 어떠한 영향도 주지 않는다. 즉, 함수의 상위 스코프는 언제나 자신이 정의된 스코프다.

**14.1 변수의 생명 주기**

- 지역변수의 생명주기 : 지역 변수의 생명주기는 함수의 생명주기와 일치한다. 변수는 자신이 등록된 스코프가 소멸될 떄 까지 유효하며 할당된 메모리 공간은 더 이상 그 누구도 참조하지 않을 때, 가비지 콜렉터에 의해 해제되어 가용메모리 풀에 반환된다.
- 전역변수의 생명주기: 전역객체의 생명주기와 일치한다.

**14.2 전역 변수의 문제점**

- 암묵적 결합 : 모든 코드가 전역변수를 참조하고 변경할 수 있음
- 긴 생명주기 : 전역변수는 생명주기가 같으므로 메모리 리소스를 오랜기간 소비한다.
- 스코프 체인 상에서 종점 존재 : 전역 변수의 검색속도가 가장 느림
- 네임스페이스 오염 : 동일한 이름으로 명명된 전역변수를 같은 스코프 내에 존재할 경우 예상치 못한 문제가 발생한다.

**14.3 전역 변수의 사용을 억제하는 방법**

- 즉시 실행 함수 : 변수의 범위를 제한하고 코드를 격리하는데 사용
    
    ```jsx
    (function () {
      var localVariable = 'I am local!';
      console.log(localVariable);
    })();
    
    console.log(localVariable); // undefined - localVariable는 함수 범위 내에서만 존재합니다.
    ```
    
- 네임 스페이스 객체
- 모듈패턴 (private. public을 분리하여 제한 및 정보은닉)

**15.1 var 키워드로 선언한 변수의 문제점**

- 변수 중복 선언 허용
- 함수레벨 스코프
- 변수 호이스팅

**15.2 let 키워드**

- 변수 중복선언 금지
- 블록레벨 스코프
- 변수 호이스팅이 발생하지 않은것처럼 동작
    - 일시적 사각지대 (TDZ)의 단계에 있는 변수를 접근할 시, 참조에러가 발생한다.
- 전역 객체와 let
    - window.x 이런식으로 사용가능하고 암묵적 전역이라 생략도 가능

**15.3 const 키워드**

- 선언과 초기화를 동시에 해야한다.
- 재할당이 금지된다.
- const 키워드로 선언된 변수에 객체를 할당한 경우 값을 변경할 수 있다.

**15.4 var vs let vs const**

- ES6를 사용한다면 var 키워드는 사용하지 말것
- 재할당이 필요한 경우에 한래 let을 사용하고 스코프는 최대한 좁게
- 변경이 발생하지 않고 읽기 전용으로 사용하는 원시값과 객체는 const키워드를 사용한다.
