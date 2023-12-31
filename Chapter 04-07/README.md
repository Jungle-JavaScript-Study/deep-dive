Q1. `var`, `let`, `const의` 차이가 무엇인가?

<details>
<summary>정답</summary>

-   `var`: 함수 스코프를 가짐, 재선언&재할당 가능, 호이스팅에 영향을 받음<br>
-   `let`: 블록 스코프를 가짐, 재선언 불가, 재할당 가능<br>
-   `const` 블록 스코프를 가짐, 반드시 선언과 동시에 초기화를 해야 함, 재선언&재할당 불가능<br>
</details>
<details>
<summary>꼬리 질문</summary> 
&nbsp;&nbsp;Q1-1. 호이스팅에 관해 설명하시오
<details>
<summary>정답</summary>

> "인터프리터가 변수와 함수의 메모리 공간을 선언 전에 미리 할당하는 것" —— by [mdn](https://developer.mozilla.org/ko/docs/Glossary/Hoisting).

-   JavaScript가 컴파일 과정에서 모든 스코프를 탐색하며 변수에 대한 선언과 초기화를 분리하여 선언에 대한 메모리부터 할당하는 것 (선언만 코드의 최상단으로 옮기는 것과 비슷한 효과)<br>
-   호이스팅의 대상은 선언만, 초기화는 호이스팅되지 않음.
-   호이스팅 시 `var`는 `undefined`로 초기화, `let`/`const`는 초기화하지 않음

    -   따라서 var과 함수는 선언 전 사용 가능, `let`/`const`/`class`는 불가능<br>
    -   `let`/`const`에서 호이스팅된 부분과 실제 선언부 사이에서, 변수가 존재는 하지만 초기화되지 않은 부분을 TDZ(Temporal Dead Zone) 라고 함(이 때 변수 사용하면 `ReferenceError` 발생)
    -   `var`만 호이스팅의 대상인 것처럼 보일 수 있으나 `let`/`const`도 호이스팅 대상임
    </details>
    &nbsp;&nbsp;Q1-2. `var`를 사용함으로써 일어날 수 있는 문제에 대해 설명하시오
      <details>
      <summary>정답</summary>

    -   함수 스코프를 가지고 있기 때문에 의도치 않은 전역적 동작이 발생할 수 있다(스코프 관리가 어렵다)
    -   호이스팅으로 인해 변수 선언이 스코프 상단으로 옮겨지기 때문에 의도치 않은 동작이 발생할 수 있다
    -   재선언과 재할당이 가능하기 때문에 개발자가 의도하지 않은 변수의 재할당이 발생할 수 있다
      </details>
    </details>
    <br>
    Q2. 할당, 선언, 초기화, 참조에 대해 순서와 실행 시점을 포함하여 설명하시오
    <details>
    <summary>정답</summary>

-   선언: 메모리 공간을 할당받고 변수 이름과 메모리 주소를 연결하는 것, 자바스크립트 엔진이 런타임 이전에 소스코드를 평가할 때 실행됨(=호이스팅)
-   초기화(정의): 값을 저장할 메모리 공간을 할당받고 암묵적으로 `undefined`를 할당하는 것, 자바스크립트에서는 변수를 선언할 때 선언 단계화 초기화 단계가 같이 일어남
    -   정확히는 자바스크립트에서 변수의 선언 = 선언 단계(변수 이름을 등록해 자바스크립트 엔진에 변수의 존재를 알리는 것) + 초기화 단계, 자바스크립트에서는 변수를 선언하면 암묵적으로 정의가 이루어지기 때문에 구분이 모호함
-   할당: 만들어진 변수에 값을 대입하는 것, 런타임에 실행됨
-   참조: 런타임에 코드가 한 줄씩 실행되면서 변수나 함수에 접근하는 것, 런타임 시점
</details>
<details>
<summary>꼬리 질문</summary> 
&nbsp;&nbsp;Q2-1. 변수에 값을 재할당할 때 일어나는 일을 설명하시오
<details>
<summary>정답</summary>

&nbsp;&nbsp;&nbsp;&nbsp;새로운 메모리 공간을 할당받고 변수가 참조하던 메모리 주소값을 업데이트한다. 이전 메모리 주소에 있던 값은 참조하는 변수가 없으면 가비지콜렉터에 의해 메모리에서 해제된다.<br>
&nbsp;&nbsp;&nbsp;&nbsp;※`var`로 선언한 변수는 선언과 동시에 초기화되기 때문에 처음 할당하는 것도 사실 재할당이다

</details>
</details>
<br>

Q3. 자바스크립트에서의 최소 단위를 `statement`와 `token`의 관점에서 설명하시오

<details>
<summary>정답</summary>

-   `statement`: 자바스크립트에서 실행 가능한 최소 코드 단위. 보통 세미콜론(;)으로 끝나고 실행될 때 어떤 작업을 수행함
    ex. 변수 선언, 할당, 조건문, 반복문
-   `token`: 소스 코드에서 의미를 가지는 최소 단위. 자바스크립트 엔진은 코드를 분석할 때 토큰 단위로 분리하고, 이를 기반으로 파싱하여 문법적인 구조를 이해함
ex. 키워드, 식별자, 연산자
</details>
<br>

Q4. `undefined`와 `null`에 대해 설명하시오

<details>
<summary>정답</summary>

-   `undefined`: 타입이자 값. 자바스크립트 엔진이 변수를 초기화할 때 사용하는 값으로, 개발자가 할당하는 것은 지양
-   `null`: 타입이자 값. 변수에 값이 없다는 것을 의도적으로 명시할 때(이전에 참조하던 값을 더 이상 참조하지 않겠다는 뜻 -> 가비지콜렉션에 영향)나 함수가 유효한 값을 반환할 수 없는 경우 반환됨
</details>
<br>

Q5. 데이터에 타입이 필요한 이유는 무엇인가?

<details>
<summary>정답</summary>

-   값을 저장할 때 할당받을 메모리 공간의 크기 결정
-   값을 참조할 때 한 번에 읽어들여야 할 메모리 공간의 크기 판단
-   메모리에서 읽은 2진수를 어떻게 해석할지 결정
</details>

<summary>꼬리질문</summary> 
자바스크립트와 타입스크립트의 차의점
- 타입 체크: JavaScript는 동적 타입 언어이며, TypeScript는 정적 타입 언어입니다.
- 객체 지향 프로그래밍: TypeScript는 JavaScript보다 강력한 객체 지향 프로그래밍 기능을 제공합니다.
- 사용 도메인: JavaScript는 클라이언트 사이드 스크립팅에 주로 사용되는 반면, TypeScript는 대규모 애플리케이션 개발에 더 적합합니다.
- 도구 지원: TypeScript는 JavaScript보다 향상된 도구 지원을 제공합니다.
</details>

<br>
Q7. c언어와 자바스크립트에서의 데이터 타입에서의 차이점을 설명하시오

<details>
<summary>정답</summary> 
  
- C언어: 정적 타입 언어로, 명시적 타입 선언(변수 선언할 때 타입 함께 선언) 필요. 변수의 타입은 컴파일 시간에 타입 체크가 발생하면서 결정되고 실행 시간에는 변경되지 않음
- 자바스크립트: 동적 타입 언어. 값을 할당하는 시점에 타입이 동적으로 결정되고 실행 중에 변수의 타입을 동적으로 변경할 수 있음. 선언이 아닌 할당에 의해 타입이 결정되는 타입 추론이 발생.
</details>
<details>
<summary>꼬리 질문</summary> 
  Q7-1. 자바스크립트의 동적 타입 언어로서의 단점을 이야기하시오.

<details>
<summary>정답</summary> 
  
  - 값을 확인하기 전에는 타입을 확신할 수 없음
  - 개발자의 의도랑 상관없이 암묵적으로 타입이 변환될 수 있어 코드가 잘못 동작할 수 있음 -> 신뢰성이 설어짐
  - 실행 시간에 타입이 결정되기 때문에 코드의 복잡성이 증가할 수 있음
</details>
</details>
<details>
<summary>꼬리 질문</summary> 
  Q7-2. 자바스크립트와 타입스크립트의 차의점과 장단점을 아는만큼 설명해주세요

<details>
<summary>정답</summary> 
  
- JavaScript:
동적 타입 언어: JavaScript는 동적 타입 언어로, 변수의 타입을 선언하지 않고도 자유롭게 값을 할당할 수 있습니다. 이는 개발자에게 유연성을 제공하지만, 타입 오류가 발생할 수 있는 가능성도 있습니다.
브라우저에서 실행: JavaScript는 웹 브라우저 환경에서 동작하도록 설계되었습니다. 클라이언트 측 웹 개발에 주로 사용되며, 웹 페이지의 동적인 기능을 구현할 수 있습니다.
쉬운 학습 곡선: JavaScript는 배우기 쉽고 사용하기 간단한 문법을 갖고 있어 입문자에게 접근하기 쉽습니다.

-   TypeScript:
    정적 타입 언어: TypeScript는 정적 타입 언어로, 변수의 타입을 명시적으로 선언하고 컴파일 시간에 타입 검사를 수행합니다. 이를 통해 타입 관련 오류를 사전에 탐지할 수 있어 코드의 안정성과 유지 보수성을 향상시킵니다.
    타입 주석과 타입 추론: TypeScript는 변수와 함수의 매개변수, 반환 값 등에 대해 타입 주석을 명시적으로 추가할 수 있습니다. 또한, 타입 추론 기능을 통해 타입을 자동으로 추론하여 생략할 수 있는 경우도 있습니다.
    ES6+ 지원: TypeScript는 ECMAScript (ES) 표준에 기반하고 있으며, 최신 JavaScript 기능을 지원합니다. 이로 인해 강력한 객체지향 프로그래밍 패턴, 모듈화, 화살표 함수 등을 활용할 수 있습니다.
    대규모 프로젝트에 적합: TypeScript는 대규모 프로젝트에서 특히 유용합니다. 정적 타입 검사와 타입 주석을 통해 코드의 가독성과 유지 보수성을 높일 수 있으며, 풍부한 개발 환경과 도구 지원을 받을 수 있습니다.
    장단점을 요약하면 다음과 같습니다:

-   JavaScript의 장점:
    쉽게 학습하고 사용할 수 있는 문법과 개발 생태계
    브라우저에서 직접 실행되는 클라이언트 측 웹 개발에 적합
    JavaScript의 단점:

-   동적 타입 언어로 인한 타입 관련 오류 가능성
    대규모 프로젝트에서 코드의 안정성과 유지 보수성 부족
    TypeScript의 장점:

-   정적 타입 언어로 인한 코드의 안정성과 타입 관련 오류 사전 탐지
    ECMAScript 표준과 최신 JavaScript 기능 지원
    대규모 프로젝트에서 가독성과 유지 보수성 향상
    TypeScript의 단점:

-   학습 곡선이 존재하며 JavaScript에 비해 상대적으로 복잡한 문법
    컴파일 시간이 추가로 소요될 수 있음
    따라서 JavaScript는 빠른 프로토타이핑과 작은 규모의 프로젝트에 적합하며, TypeScript는 대규모 프로젝트 및 팀 협업에 더 적합한 선택입니다. 선택은 개발하는 프로젝트의 요구사항과 개발자의 선호도에 따라 달라질 수 있습니다.

</details>
</details>
<br>
<br>

Q8. 자바스크립트에서 2진수, 8진수, 10진수, 실수, 정수 변수를 표현하는 방법을 설명하시오.

<details>
<summary>정답</summary>

자바스크립트에서 모든 숫자는 64비트 부동소수점 형식으로 표현됨

-   2진수: `0b1010`
-   8진수: `0o10`
-   10진수(정수): `42`
-   실수: `3.14`
</details>
<br>
Q9. 암묵적 타입 변환에 대해 설명하시오

<details>
<summary>정답</summary> 
타입 강제 변환이라고도 함. 개발자의 의도와 관계없이 표현식을 평가하는 도중 자바스크립트 엔진에 의해 암묵적으로 타입이 변환되는 것. 
</details>

Q9-1. 암묵적 타입 변환이 일어나는 예시를 2가지 설명하시오.

<details>
<summary>정답</summary>

1. `!`이나 삼항 연산자 조건식은 불리언으로 변환해서 연산
2. 숫자 타입이 아닌 값에 `+` 연산하면 숫자로 변환해서 연산 수행
3. 문자열과 숫자에 대해 `+` 연산하면 문자열로 변환해서 연산
4. 비교연산자는 비교할 때 피연산자의 타입을 일치시키기 위해 암묵적 타입 변환
 </details>
 <br>
 Q10. 다음의 연산 결과와 그 이유에 대해 설명하시오

```javascript
1 + true; //1
+null; //2
NaN === NaN; //3
0 === -0; //4
Object.is(0, -0); //5
typeof null; //6
typeof NaN; //7
typeof foo; //8
```

<details>
<summary>정답</summary>

```javascript
1 + true; // 2 (+ 연산자의 암묵적 타입 변환)
+null; // 0 (위와 동일, null은 숫자 0으로 변환됨)
NaN === NaN; // false (NaN은 자신과 일치하지 않는 유일한 값)
0 === -0; // true
Object.is(0, -0); // false (Object.is 메서드는 0과 -0을 구별함)
typeof null; // "object" (자바스크립트의 첫번째 버그)
typeof NaN; // "number" (NaN은 숫자 데이터 타입!)
typeof foo; // "undefined" (foo라는 변수가 선언되지 않았으므로 "undefined"를 반환합니다.)
```

</details>

<details>
<summary>꼬리 질문</summary> 
  Q10-1. 위의 3번을 올바르게 평가하는 두가지 방법에 대해 설명하시오
<details>
<summary>정답</summary>

-   `Number.isNan(NaN)`, `isNan(NaN)`
-   `Object.is(NaN, NaN)`
</details>
</details>

<br>

Q11. 개발자 도구 콘솔창에 `var foo = 10`을 입력한 결과와 그 이유를 설명하시오

<details>
<summary>정답</summary>

<img width="142" alt="image" src="https://github.com/Jungle-JavaScript-Study/JavaScript/assets/70076564/f394faa1-edca-42a1-a489-ff38d6b54e97">

-   `var foo = 10`은 선언문이자 할당문
-   선언문 = 표현식이 아닌 문<br>
    할당문 = 표현식인 문<br>
    선언문+할당문 = 표현식이 아닌 문<br>
    위 문은 변수에 값을 할당하는 사이드이펙트가 있을 뿐, 어떠한 값이 평가되지는 않는다. 따라서 완료값이 돼서 `undefined`가 찍힘<br>
    +) return 뒤에 넣을 수 있으면 표현식인 문, 없으면 표현식이 아닌 문<br>
    참고자료) [Why does console.log say undefined, and then the correct value?](https://stackoverflow.com/questions/24342748/why-does-console-log-say-undefined-and-then-the-correct-value)
    <br>[console.log만 찍어도 undefined 나오는 이유](https://velog.io/@ingdol2/JS-console.log%EB%A7%8C-%EC%B0%8D%EC%96%B4%EB%8F%84-undefined-%EB%82%98%EC%98%A4%EB%8A%94-%EC%9D%B4%EC%9C%A0)
    </details>
    <details>
    <summary>꼬리 질문</summary> 
    &nbsp;&nbsp;Q11-1. 완료값이란 무엇인가?
    <details>
    <summary>정답</summary>

    크롬 개발자 도구에서 표현식이 아닌 문을 실행하면 언제나 `undefined`를 출력하는데, 이걸 완료값이라고 함. 표현식인 문을 실행하면 언제나 평가된 값을 반환.
    </details>
    </details>
    <br>

Q12. `==`와 `===`의 차이점에 대해 설명하시오.

<details>
<summary>정답</summary>

-   `==`: 피연산자들을 암묵적 타입 변환으로 타입을 일치시킨 뒤 값을 비교, 사용 지양
-   `===`: 피연산자의 타입과 값이 모두 같을 경우에만 `true`
</details>
