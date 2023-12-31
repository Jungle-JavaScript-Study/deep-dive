## Ch 16~18, 20

**Q1. 데이터 프로퍼티의 프로퍼티 어트리뷰트 4개**

- 정답
    
    데이터 프로퍼티는 키와 값으로 구성된 일반적인 프로퍼티로,
    
    - 프로퍼티 값에 접근하면 반환되는 값인 `[[Value]]`
    - 값의 변경 가능 여부를 나타내는 `[[Writable]]`,
    - 열거 가능 여부를 나타내는 `[[Enumerable]]`,
    - 재정의 가능 여부를 나타내는 `[[Configurable]]`이 있습니다.
- 내 대답
    - [[Value]], [[Writable]], [[Enumerable]], [[Configurable]] .

**Q2. 프로퍼티가 생성될 때 데이터 프로퍼티의 각 프로퍼티 어트리뷰트는 어떤 값으로 초기화되나요?**

- 정답
    
    `[[Value]]`의 값은 프로퍼티 값으로 초기화되며 나머지는 true로 초기화됩니다.
    
- 내 대답
    
    value : 프로퍼티의 초기값
    
    writable, enumerable, configurable : true
    

**Q3. 접근자 프로퍼티의 프로퍼티 어트리뷰트 4개**

- 정답
    
    접근자 프로퍼티는 다른 데이터 프로퍼티의 값을 읽거나 저장할 때 사용하는 접근자 함수로 구성된 프로퍼티로,
    
    - 접근자 프로퍼티를 통해 프로퍼티 값을 읽을 때 호출되는 접근자 함수인 `[[Get]]`
    - 접근자 프로퍼티를 통해 프로퍼티 값을 저장할 때 호출되는 접근자 함수인 `[[Set]]`
    - 열거 가능 여부를 나타내는 `[[Enumerable]]`,
    - 재정의 가능 여부를 나타내는 `[[Configurable]]`이 있습니다.
- 내 대답
    
    get, set, enumerable, configurable
    

**Q4. JavaScript에서 객체의 변경을 방지하는 메서드에는 어떤 게 있나요?**

- 정답
    - 프로퍼티의 추가를 금지하는 `Object.preventExtensions`
    - 객체를 밀봉해 읽기와 쓰기만 가능하게 하는 `Object.seal`
    - 객체를 동결해 읽기만 가능하게 하는 `Object.freeze` 메서드가 있습니다.
- 내 대답
    
    Object.preventExtension
    
    Object.seal
    
    Object.freeze
    

**Q4-1. 위 메서드를 사용해 변경을 방지한 객체의 중첩 객체는 변경이 가능한가요?**

- 정답
    
    ㅇㅇ 위 메서드들은 중첩 객체까지는 영향을 주지 못하기 때문에 중첩 객체는 변경이 가능합니다.
    
    객체의 중첩 객체까지 변경이 불가능하게 하려면 객체를 값으로 갖는 모든 프로퍼티에 대해 재귀적으로 변경을 방지하는 메서드를 호출해야 합니다.
    
- 내 대답
    
    변경이 가능하다.
    불가능하게 하려면 객체의 프로퍼티를 순회하면서 중첩 객체 전부를 freeze 해줘야한다. (deep freeze)
    

**Q5. 생성자 함수는 어떤 함수인가요?**

- 정답
    
    new 연산자와 함께 호출하여 객체(인스턴스)를 생성하는 함수입니다.
    
- 내 대답
    
    new 연산자와 함께 호출해 객체를 생성하는 함수
    

**Q6. 생성자 함수에 의해 생성된 객체를 부르는 용어는 무엇인가요?**

- 정답
    
    인스턴스
    
- 내 대답
    
    ~~constructor 함수~~
    
    인스턴스
    

**Q7. 객체를 생성할 때, 객체 리터럴을 사용하지 않고 생성자 함수로 생성하는 것이 더 유리한 상황은 언제인가요?**

- 정답
    
    프로퍼티 구조가 동일한 객체 여러 개를 생성할 때는 생성자 함수를 사용하는 것이 더 간편합니다.
    
- 내 대답
    
    한 번에 여러 객체를 생성할 때, 같은 프로퍼티를 갖는 객체를 생성할 때
    

**Q8. 생성자 함수를 정의하는 방법을 설명해주세요.**

- 정답
    
    일반 함수와 동일한 방법으로 정의하고 new 연산자와 함께 호출합니다.
    
- 내 대답
    
    Object 생성자 함수를 사용할 수도 있고, 
    new 연산자를 사용할 수도 있다.
    

**Q9. 생성자 함수를 new 연산자 없이 호출하면 어떻게 동작하나요?**

- 정답
    
    일반 함수로 동작합니다.
    
- 내 대답
    
    일반 객체로 동작함.
    

**Q9-1. JavaScript의 빌트인 생성자 함수인 String, Number, Boolean 생성자 함수를 new 연산자 없이 호출하면 어떻게 동작하나요?**

- 정답
    
    객체가 아닌 문자열, 숫자, 불리언 값을 반환합니다.
    
- 내 대답
    
    타입 변환이 일어난다.
    문자열, 숫자타입, 불리언값으로 변한다.
    

**Q10. 생성자 함수로서 호출할 수 있는 함수와 그럴 수 없는 함수는 어떻게 구분되나요?**

- 정답
    
    함수 정의 방식에 따라 구분됩니다.
    
    함수 선언문, 함수 표현식, 클래스는 생성자 함수로서 호출될 수 있는 constructor이고,
    
    ES6의 메서드 축약 표현으로 작성된 메서드, 화살표 함수는 non-constructor입니다.
    
- 내 대답
    
    [[Construct]] 가 true이면 생성자함수로서 호출가능
    false 이면 생성자함수로서 호출불가능
    

**Q11. 생성자 함수 내부의 this에 값이 최초로 바인딩 되는 시점은 언제이고, 어떤 값이 바인딩 되나요?**

- 정답
    
    생성자 함수 몸체의 코드가 실행되는 런타임 이전에 암묵적으로 생성된 빈 객체가 this에 바인딩됩니다.
    
- 내 대답
    
    런타임 이전에 암묵적으로 바인딩 되고, 생성될 함수 객체의 인스턴스의 빈 객체
    

**Q12. 생성자 함수 내부의 this는 무엇을 가리키나요?**

- 정답
    
    생성자 함수가 생성할 인스턴스를 가리킵니다.
    
- 내 대답
    
    생성자 함수가 호출될 인스턴스
    

**Q12-1. 생성자 함수를 new 연산자 없이 호출했을 때 함수 내부의 this는 무엇을 가리키나요?**

- 정답
    
    전역 객체 window를 가리킵니다.
    
- 내 대답
    
    전역 객체 (window, global)
    

**Q13. 생성자 함수가 생성자 함수로서 호출되었는지 확인하는 방법을 설명해주세요.**

- 정답
    
    함수 내부에서 new.target을 사용해서 확인할 수 있습니다.
    
    생성자 함수로서 호출되면 new.target은 함수 자신을 가리키고,
    
    일반 함수로서 호출되면 undefined입니다.
    
- 내 대답
    
    함수 내부에서 new.target이 함수 객체를 가리키면 생성자함수
    일반 함수이면 new.target === undefined 
    

**Q14. 일급 객체가 되는 조건 4개**

- 정답
    - 무명의 리터럴로 생성 가능
    - 변수나 자료구조(객체, 배열 등)에 저장 가능
    - 함수의 매개변수에 전달 가능
    - 함수의 반환값으로 사용 가능
- 내 대답
    1. 무명의 리터럴로 생성할 수 있다.
    2. 변수나 자료구조(객체, 배열 등)에 저장할 수 있다.
    3. 함수의 매개변수에 전달할 수 있다.
    4. 함수의 반환값으로 사용할 수 있다.

**Q14-1. 일급 객체는 어떤 객체를 의미하나요?**

- 정답
    
    일급 객체란 다른 객체들에게 적용 가능한 연산을 모두 지원하는 객체를 말합니다.
    
- 내 대답
    
    위 조건 4개가 모두 만족하는 객체.
    

**Q15. 함수 호출 시 매개변수의 개수보다 인수를 초과하여 전달한 경우 초과된 인수를 어떻게 확인할 수 있나요?**

- 정답
    
    함수 내부에서 지역 변수처럼 사용할 수 있는 arguments 객체를 통해 확인할 수 있습니다.
    
    모든 인수는 암묵적으로 arguments 객체의 프로퍼티로 보관됩니다.
    
- 내 대답
    
    함수 객체의 arguments 프로퍼티에는 인수가 모두 저장된다.
    

**Q15-1. 위 질문의 답이 되는 기능의 활용 방안을 설명해주세요.**

- 정답
    
    arguments 객체는
    
    매개변수 개수를 확정할 수 없는 가변 인자 함수를 구현할 때 활용할 수 있습니다.
    
- 내 대답
    
    가변 인자 함수에서 유용하다.
    

**Q16. arguments 객체의 length 프로퍼티와 함수 객체의 length 프로퍼티는 각각 무엇의 개수를 가리키나요?**

- 정답
    
    arguments 객체의 length 프로퍼티는 인자의 개수를,
    
    함수 객체의 length 프로퍼티는 매개변수의 개수를 가리킵니다.
    
- 내 대답
    
    arguments 객체의 length 프로퍼티는 함수로 들어온 인자의 개수이고,
    함수 객체의 length 프로퍼티는 매개변수의 개수이다.
    

**Q17. prototype 프로퍼티가 없는 함수는 어떤 함수인가요?**

- 정답
    
    non-constructor 함수에는 prototype 프로퍼티가 없습니다.
    
- 내 대답
    
    non-constructor 함수
    

**Q17-1. prototype 프로퍼티는 무엇을 가리키나요?**

- 정답
    
    생성자 함수가 생성할 인스턴스의 프로토타입 객체를 가리킵니다.
    
- 내 대답
    
    prototype 프로퍼티는 함수가 객체를 생성하는 생성자 함수로 호출될 때 
    생성자 함수가 생성할 인스턴스의 프로토타입 객체를 가리킨다.
    

**Q18. JavaScript에서 strict mode를 적용하는 방법을 설명해주세요.**

- 정답
    
    전역의 선두 또는 함수 몸체의 선두에 `'use strict';`를 추가합니다.
    
- 내 대답
    
    전역의 선두나 함수 몸체의 선두에 ‘use strict’를 선언한다.
    

**Q18-1. strict mode가 발생시키는 에러 4개**

- 정답
    - 선언하지 않은 변수(암묵적 전역)을 참조하면 ReferenceError가 발생합니다.
    - delete 연산자로 변수, 함수, 매개변수를 삭제하면 SyntaxError가 발생합니다.
    - 중복된 매개변수 이름을 사용하면 SyntaxError가 발생합니다.
    - with문을 사용하면 SyntaxError가 발생합니다.
- 내 대답
    
    암묵적 전역
    변수, 함수, 매개변수의 삭제
    
    매개변수 이름의 중복
    with문의 사용
    

**Q18-2. strict mode 적용에 의한 변화 2개**

- 정답
    - 함수를 일반 함수로서 호출했을 때 this에 바인딩 되는 값이 전역 객체가 아닌 undefined가 바인딩됩니다.
    - 매개변수로 전달 받은 인수를 재할당하여 변경해도 arguments 객체에는 반영되지 않습니다.
- 내 대답
    
    일반함수의 this
    
    arguments 객체
    

**Q19. 프로젝트에서 사용한 라이브러리 혹은 프레임워크에서 strict mode를 설정하는 방법을 설명해주세요.
(React or Next.js 중 사용한 것 기준으로 설명해주세요.)**

- 정답
    
    **React**
    
    React에서 제공하는 StrictMode 태그를 사용하여 감싼 영역에 strict mode가 적용됩니다.
    
    https://react.dev/reference/react/StrictMode
    
    **Next.js**
    
    Next.js 13.4부터는 기본적으로 Strict Mode가 활성화됩니다.
    
    next.config.js에서 reactStrictMode의 값을 변경해 설정할 수 있습니다.
    
    https://nextjs.org/docs/app/api-reference/next-config-js/reactStrictMode
    
- 내 대답
    
    React Dom 위아래 <strict mode> </strict mode> 로 감싼다.
    

**Q19-1. react에서 strict mode를 사용하면 (개발 환경에서) 어떤 동작이 활성화되나요?**

- 정답
    - 컴포넌트가 추가로 한 번 더 렌더링되어 불순한 렌더링에 의해 발생하는 버그를 찾는 데 도움을 줍니다.
    - useEffect가 추가로 한 번 더 실행되어 Effect 정리가 누락되어 발생하는 버그를 찾는 데 도움을 줍니다.
    - deprecated 된 API를 사용하고 있지는 않은 지 확인합니다. https://react.dev/reference/react/StrictMode
- 내 대답
    
    파일 실행이 두 번 된다.
