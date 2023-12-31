### CH. 4 변수

- 변수란 ? 왜 필요한가 ?
    - 애플리케이션은 데이터를 다룬다. 아무리 복잡한 애플리케이션이라 해도 데이터를 입력(input)받아 처리하고 그 결과를 출력(output)하는 것이 전부다.
    
    ```jsx
    10 + 20
    ```
    
    - 자바스크립트 엔진이 위 자바스크립트 코드를 계산(평가,evaluation)하려면 먼저 10, 20, + 라는 기호(리터럴,literal과 연산자operator)의 의미를 알고 있어야 하며, 10 + 20 이라는 식(표현식,expression)의 의미도 해석(파싱,parsing)할 수 있어야 한다.
    - 메모리(memory)는 데이터를 저장할 수 있는 메모리 셀(memory cell)의 집합체다. 메모리 셀 하나의 크기는 1바이트(8비트)이며, 컴퓨터는 1바이트 단위로 데이터를 저장(write)하거나 읽어(read)들인다.
    - 셀은 고유의 메모리 주소(memory address)를 갖는다.
    - 메모리 주소를 통해 값에 직접 접근하는 것은 치명적 오류를 발생시킬 가능성이 높은 매우 위험한 일이다. ⇒ 따라서 **자바스크립트는 개발자의 직접적인 메모리 제어를 허용하지 않는다.**
    - **변수는 하나의 값을 저장하기 위해 확보한 메모리 공간 자체** or **그 메모리 공간을 식별하기 위해 붙인 이름을 말한다. ⇒ 값의 위치를 가리키는 상징적인 이름이다.** - 변수는 **하나**의 값을 저장하기 위한 메커니즘이다. 여러 개의 값을 저장하려면 여러 개의 변수를 사용해야 한다. (단, 배열이나 객체 같은 자료구조를 사용하면 관련이 있는 여러 개의 값을 그룹화해서 하나의 값처럼 사용할 수 있다.)
    - 메모리 공간에 저장된 값을 식별할 수 있는 고유한 이름을 **********변수 이름**********이라고 한다.
    변수에 저장된 값을 ****************변수 값****************이라고 한다.
    - 변수에 값을 저장하는 것을 **할당(assignment, 대입, 저장)**이라 하고, 변수에 저장된 값을 읽어 들이는 것을 ******참조(reference)******라고 한다.
- 식별자 (변수 이름)
    - **********************************************************************************************************************************************식별자는 어떤 값을 구별해서 식별할 수 있는 고유한 이름을 말한다.**********************************************************************************************************************************************
    - 식별자는 ******************************************************************************************값이 아니라 메모리 주소******************************************************************************************를 기억하고 있다. 즉, 식별자는 메모리 주소에 붙인 이름
    - 메모리 상에 존재하는 어떤 값을 식별할 수 있는 이름은 모두 식별자라고 한다. (ex> 변수, 함수, 클래스 등의 이름 모두)
    - 변수, 함수, 클래스 등의 이름과 같은 식별자는 네이밍 규칙을 준수해야 하며, ****************선언(declaration)****************에 의해 자바스크립트 엔진에 식별자의 존재를 알린다.
- 변수 선언
    - 변수 선언(variable declaration)이란 변수를 생성하는 것 - 값을 저장하기 위한 메모리 공간을 확보(allocate)하고 변수 이름과 확보된 메모리 공간의 주소를 연결(name binding)해서 값을 저장할 수 있게 준비하는 것 - 변수 선언에 의해 확보된 메모리 공간은 확보가 해제(release)되기 전까지 보호된다.
    - **********************************************************************************************************************************************************************************************************변수를 사용하려면 반드시 선언이 필요하다. 변수를 선언할 때는 var, let, const 키워드를 사용한다.**
    - 변수 선언에 의해 확보된 메모리공간에는 자바스크립트 엔진에 의해 undefined라는 값이 암묵적으로 할당되어 초기화된다.
    - +) 변수 이름을 비롯한 모든 식별자는 실행 컨텍스트에 등록된다.
    - 일반적으로, 초기화(initialization)란 변수가 선언된 이후 최초로 값을 할당하는 것.
    → var 키워드로 선언한 변수는 undefined로 암묵적인 초기화가 자동 수행된다.
    +) 만약, 초기화 단계를 거치지 않으면 확보된 메모리 공간에는 이전에 다른 애플리케이션이 사용했던 값이 남아 있을 수 있다.
    → 자바스크립트의 var 키워드는 암묵적으로 초기화를 수행하므로 이러한 위험으로부터 안전하다.
    - 만약 선언하지 않은 식별자에 접근하면 ****************************ReferenceError****************************(참조 에러)가 발생한다.
- 변수 선언의 실행 시점과 변수 호이스팅
    - **************************************************************************************************************************************************************************************************************************************************************변수 선언이 소스코드가 한 줄씩 순차적으로 실행되는 시점, 즉 런타임(runtime)이 아니라 그 이전 단계에서 실행된다.**************************************************************************************************************************************************************************************************************************************************************
    - 자바스크립트 엔진은 소스코드를 한 줄씩 순차적으로 실행하기에 앞서 먼저 소스코드의 평가 과정을 거치면서 소스코드를 실행하기 위한 준비를 한다.
    → 소스코드의 평가 과정이 끝나면 비로소 변수 선언을 포함한 모든 선언문을 제외하고 소스코드를 한 줄씩 순차적으로 실행한다.
    - ******************************************************************************************************************************************************************************************************************************************************************************변수 선언문이 코드의 선두로 끌어 올려진 것처럼 동작하는 자바스크립트 고유의 특징을 변수 호이스팅(variable hoisting)******************************************************************************************************************************************************************************************************************************************************************************이라 한다.
    변수 선언뿐 아니라 var, let, const, function, function*, class 키워드를 사용해서 선언하는 모든 식별자(변수, 함수, 클래스 등)는 호이스팅된다.
- 값의 할당
    - ********************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************변수 선언은 소스코드가 순차적으로 실행되는 시점인 런타임 이전에 먼저 실행되지만 값의 할당은 소스코드가 순차적으로 실행되는 시점인 런타임에 실행된다.********************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************
    - 그림처럼 변수에 값을 할당할 때는 이전 값 undefined 가 저장되어 있던 메모리 공간을 지우고 그 메모리 공간에 할당 값 80을 새롭게 저장하는 것이 아니라 **새로운 메모리 공간을 확보**하고 **그곳에 할당 값 80을 저장**한다는 점에 유의하자.
        
        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0651e4f9-b59d-461c-b876-92879381e9ec/Untitled.png)
        
- 값의 재할당
    - 재할당은 변수에 저장된 값을 다른 값으로 변경한다
    → var 키워드로 선언한 변수는 선언과 동시에 undefined로 초기화되기 때문에 엄밀히 말하자면 변수에 처음으로 값을 할당하는 것도 사실은 재할당이다.
    - ********************************값을 재할당할 수 없어서 변수에 저장된 값을 변경할 수 없다면 변수가 아니라 상수(constant)라 한다.********************************
    - 값을 재할당할 때, 어떤 식별자와도 연결되어 있지 않게 되는 불필요한 값들은 가비지 콜렉터에 의해 메모리에서 자동 해제된다. ( 단, 메모리에서 언제 해제될지는 예측할 수 없다. )
    - +) 언매니지드 언어(unmanaged language)와 매니지드 언어(managed language)
        - 프로그래밍 언어는 메모리 관리 방식에 따라 언매니지드 언어와 매니지드 언어로 분류할 수 있다.
        - C 언어 같은 언매니지드 언어는 개발자가 명시적으로 메모리를 할당하고 해제하기 위해 malloc()과 free() 같은 저수준 메모리 제어 기능을 제공한다.
        - 자바스크립트 같은 매니지드 언어는 메모리의 할당 및 해제를 위한 메모리 관리 기능을 언어 차원에서 담당하고 개발자의 직접적인 메모리 제어를 허용하지 않는다. 즉, 개발자가 명시적으로 메모리를 할당하고 해제할 수 없다.
        - 장단점
            - 언매니지드언어는 개발자의 역량에 따라 최적의 성능을 확보할 수 있지만 그 반대의 경우 치명적 오류를 생산할 가능성도 있다.
            - 매니지드 언어는 개발자의 역량에 의존하는 부분이 상대적으로 작아져 어느 정도 일정한 생산성을 확보할 수 있다는 장점이 있지만 성능 면에서 어느 정도의 손실은 감수할 수 밖에 없다.
- 식별자 네이밍 규칙