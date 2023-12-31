<aside>
💡 **데이터 타입 (data type)**
값의 종류

</aside>

-   자바스크립트의 모든 값은 데이터 타입이 존재
    | 구분      | 데이터 타입 | 설명                                                |
    | --------- | ----------- | --------------------------------------------------- |
    | 원시 타입 | number      | 숫자, 정수와 실수 구분 없이 하나의 숫자 타입만 존재 |
    |           | string      | 문자열                                              |
    |           | boolean     | 논리적 참과 거짓 (true / false)                     |
    |           | undefined   | var 키워드로 선언된 변수에 암묵적으로 할당되는 값   |
    |           | null        | 값이 없다는 것을 의도적으로 명시할 때 사용하는 값   |
    |           | symbol      | ES6에서 추가된 7번째 타입                           |
    | 객체 타입 |             | 객체, 함수, 배열 등                                 |
-   데이터 타입별 목적과 용도
    -   number : 산술 연산
    -   string : 텍스트를 화면에 출력하기 위해
    ⇒ 타입마다 메모리 공간의 크기도 다르고, 저장되는 2진수도 다르며, 읽어 들여 해석하는 방식도 다름

<aside>
💡 **원시 타입**
컴퓨터 과학에서 프로그래밍 언어가 제공하는 자료형

</aside>

## 6.1 숫자 타입

-   자바스크립트는 하나의 숫자 타입만 존재
-   배정밀도 64비트 부동소수점 형식의 2진수
    -   모든 수를 실수로 처리하며, 정수만 표현하기 위한 데이터 타입이 별도로 존재하지 않음
    -   자바스크립트는 2/8/16진수를 표현하기 위한 데이터 타입을 제공하지 않아, 10진수로 해석
-   추가적으로 세 가지 특별한 값
    1. `Infinity` : 양의 무한대
    2. `-Infinity` : 음의 무한대
    3. `NaN` : 산술 연산 불가

## 6.2 문자열 타입

-   텍스트 데이터를 나타내는 데 사용
-   0개 이상의 16비트 유니코드 문자(UTF-8)의 집합
-   `작은따옴표(’’)`, `큰따옴표(””)`, ` 백틱(``) `으로 표현
    ⇒ 키워드나 식별자 같은 토큰과 구분하기 위해서
-   자바스크립트의 문자열은 원시 타입이며, 변경 불가능한 값
    -   따라서, 문자열이 한번 생성되면 그 문자열을 변경할 수 없음

## 6.3 템플릿 리터럴

-   편리한 문자열 처리 기능 제공
    -   멀티라인 문자열 `multi-line-string`
    -   표현식 삽입 `expression interpolation`
    -   태그드 템플릿 `tagged template`
-   런타임에 일반 문자열로 변환되어 처리
-   백틱(``)을 사용해 표현

### 6.3.1 멀티라인 문자열

-   일반 문자열에서는 줄바꿈이 허용되지 않아, 이스케이프 시퀀스 사용
      <aside>
      💡 **이스케이프 시퀀스 (escape sequence)**
      
      | 이스케이프 시퀀스 | 의미 | 이스케이프 시퀀스 | 의미 |
      | --- | --- | --- | --- |
      | \0 | Null | \t | 탭 (수평) |
      | \b | 백스페이스 | \v | 탭 (수직) |
      | \f | 폼 피드 : 프린터로 출력할 경우 
      다음 페이지의 시작 지점으로 이동 | \uXXXX | 유니코드 |
      | \n | 개행 : 다음 행으로 이동 | \’ | 작은따옴표 |
      | \r | 개행 : 커서를 처음으로 이동 | \” | 큰따옴표 |
      |  |  | \\ | 백슬래시 |
      </aside>
      
      > ***라인 피드와 캐리지 리턴***
      **개행** : 텍스트의 한 줄이 끝남을 표시하는 문자 또는 문자열
      **라인 피드(\n)** : 커서를 정지한 상태에서 종이를 한 줄 올리는 것
      **캐리지 리턴(\r)** : 종이를 움직이지 않고 커서를 맨 앞줄로 이동
      - 윈도우 : CR+LF
      - 유닉스 : LF
      - mac : CR (~ver.9) / LF (ver.10~)
      >
-   템플릿 리터럴 내에서는 이스케이프 시퀀스 없이 줄바꿈 가능하며, 모든 공백도 있는 그대로 적용

### 6.3.2 표현식 삽입

-   문자열은 `+연산자`를 사용해 연결할 수 있음
    -   피연산자 중 하나 이상이 문자열인 경우 문자열 연결 연산자로 동작 (그 외의 경우는 덧셈 연산자)
-   표현식 삽입을 통해 `+연산자` 없이 쉽게 문자열 조합 가능
    -   표현식을 삽입하려면 `${표현식}`으로 사용
        -   문자열이 아니더라도 문자열로 강제 변환되어 삽입됨
    -   반드시 템플릿 리터럴 안에서만 사용
    ```jsx
    var name = "jiwoo";
    var age = 23;

    console.log(`My name is ${name}, ${age}`);
    ```

## 6.4 불리언 타입

-   논리적 참, 거짓을 나타내는 `true` / `false`
-   조건에 의해 프로그램의 흐름을 제어하는 조건문에서 자주 사용

## 6.5 undefined 타입

-   변수를 선언한 이후 값을 할당하지 않은 변수를 참조하면 undefined 반환
-   개발자가 의도적으로 사용한게 아니라, 자바스크립트 엔진이 변수를 초기화할 때 사용하는 값
    -   즉, undefined == 초기화되지 않은 변수

> **_NULL_**
> 변수에 값이 없다는 것을 명시하고 싶을 때

<aside>
💡 **선언과 정의**
- 정의 : 변수에 값을 할당하여 변수의 실체를 명확히 하는 것
- 자바스크립트는 선언과 정의에 대한 경계가 모호하나,  일반적으로 변수는 선언하고 함수는 정의

</aside>

## 6.6 null 타입

-   변수에 값이 없다는 것을 의도적으로 명시할 때 사용 (의도적 부재 intentional absence)
-   변수에 null을 할당하는 것은 변수가 이전에 참조하던 값을 더 이상 참조하지 않겠다는 의미
    ⇒ 참조를 명시적으로 제거
    ⇒ 이후 자바스크립트 엔진이 가비지 콜렉션 수행하여 사라짐
-   함수가 유효한 값을 반환할 수 없는 경우 명시적으로 null을 반환하기도

## 6.7 심벌 타입

-   ES6에서 추가된 7번째 타입
-   변경 불가능한 원시 타입의 값 (심벌 값은 다른 값과 중복되지 않는 유일무이한 값)
    -   이름이 충돌할 위험이 없는 객체의 유일한 프로퍼티 키를 만들기 위해 사용
-   symbol 함수를 호출해 생성
    -   이때 생성된 심벌 값은 외부에 노출되지 않으며, 다른 값과 중복되지 않는 유일무이한 값

```jsx
// 심벌 값 생성
var key = Symbol("key");

// 객체 생성
var obj = {};

// 심벌을 프로퍼티 키로 사용
obj[key] = "value";
```

## 6.8 객체 타입

-   자바스크립트는 객체 기반의 언어이며, 자바스크립트를 이루고 있는 거의 모든 것이 객체

## 6.9 데이터 타입의 필요성

### 6.9.1 데이터 타입에 의한 메모리 공간의 확보와 참조

-   값은 메모리에 저장하고 참조할 수 있어야 함
-   메모리에 값을 저장하려면 먼저 확보해야 할 메모리 공간의 크기를 결정
-   자바스크립트 엔진은 데이터 타입, 즉 값의 종류에 따라 정해진 크기의 메모리 공간을 확보
    ⇒ 변수에 할당되는 값의 데이터 타입에 따라 확보해야 할 메모리 공간의 크기가 결정됨
    ![스크린샷 2023-09-24 오후 3.49.52.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/f15bdfe8-e824-4d79-9d88-8bf1244f8c56/fa2dcf11-69f0-4ddd-a52a-7e74a3e0d242/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-09-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_3.49.52.png)
-   숫자 타입의 값을 생성할 때 : 배정밀도 64비트 부동소수점 형식
      <aside>
      💡 **배정밀도 64비트 부동소수점 형식**
      8바이트로 숫자를 표현 == 숫자 값의 크기는 8바이트
      
      </aside>


> **_값을 참조하는 과정_**

1. 한번에 읽어야 할 메모리 셀의 개수(바이트 수)를 알아야 함
2. score 변수라면, 숫자 타입의 값이 할당되어 있어, 엔진은 숫자 타입으로 인식
3. 숫자 타입은 8바이트 단위로 저장되므로 8바이트 단위로 메모리 공간의 저장된 값 읽음
    >

<aside>
💡 **심벌 테이블**
: 컴파일러 또는 인터프리터는 심벌 테이블이라고 불리는 자료 구조를 통해 식별자를 키로 바인딩된 값의 메모리 주소, 데이터 타입, 스코프 등을 관리

</aside>

### 6.9.2 데이터 타입에 의한 값의 해석

-   모든 값은 데이터 타입을 가지며, 메모리에 2진수로(비트의 나열) 저장
    -   데이터 타입에 따라 다르게 해석될 수 있음
-   데이터 타입이 필요한 이유
    1. 값을 저장할 때 확보해야 하는 메모리 공간의 크기를 결정하기 위해
    2. 값을 참조할 때 한 번에 읽어 들여야 할 메모리 공간의 크기를 결정하기 위해
    3. 메모리에서 읽어 들인 2진수를 어떻게 해석할지 결정하기 위해

## 6.10 동적 타이핑

### 6.10.1 동적 타입 언어와 정적 타입 언어

-   **정적 타입 언어(static/string type)**
    -   변수를 선언할 때 변수에 할당할 수 있는 값의 종류를(데이터 타입) 사전에 선언
        ⇒ 명시적 타입 선언 (explicit type declaration)
    -   변수의 타입을 변경할 수 없으며, 데이터 타입에 맞는 값만 할당
    -   컴파일 시점에 타입 체크 수행 (통과하지 못하면 에러 발생)
    -   ex. C, C++, 자바, 코틀린, 고, 하스켈, 러스트, 스칼라 등
-   **동적 타입 언어(dynamic/weak type)**
    -   자바스크립트 기준, var / let / const 키워드를 통해 변수를 선언
        -   typeof 연산자로 피연산자의 데이터 타입을 문자열로 확인 가능
    -   어떠한 데이터 타입의 값이라도 자유롭게 할당 가능
    -   값을 할당하는 시점에 변수의 타입이 동적으로 결정되고, 변수의 타입을 언제든지 변경 가능
    -   type inference : 변수는 선언이 아닌 할당에 의해 타입이 결정되는 타입 추론
    -   dynamic typing : 재할당에 의해 변수의 타입은 언제든지 동적으로 변할 수 있는 동적 타이핑
    -   ex. 자바스크립트, 파이썬, PHP, 루비, 리스프, 펄 등

### 6.10.2 동적 타입 언어와 변수

-   동적 타입 언어는 변수에 어떤 값이라도 할당할 수 있어 자유롭지만, 그만큼 구조적 단점 존재
    1. 변수 값 추적 어려움
    2. 값의 변경으로 타입도 변경되기 쉬움
    3. 값을 확인하기 전에는 타입을 확신하기 어려움
    4. 개발자의 의도와는 상관없이 자바스크립트 엔진에 의해 암묵적으로 타입이 변환될수도
    ⇒ 유연성은 높지만 신뢰성은 떨어짐
-   변수를 사용할 때 주의할 점
    1. 변수는 꼭 필요한 경우에 한해 제한적으로 사용
    2. 스코프는 최대한 좁게 만들어 변수의 부작용을 억제
    3. 전역 변수는 최대한 사용하지 않기

        ⇒ 프로그램의 복잡성을 증가시키고, 처리 흐름을 추적하기 어렵고, 오류의 원인을 특정하기 어려움

    4. 변수보단 상수를 사용해 값의 변경을 억제 (const 키워드)
    5. 변수 이름은 변수의 목적이나 의미를 파악할 수 있도록 네이밍
