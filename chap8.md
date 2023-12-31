<aside>
💡 **제어문**
: 조건에 따라 코드 블록을 실행(조건문)하거나, 반복 실행(반복문)할 때 사용
- 위에서 아래 방향으로 순차적 실행하나, 제어문으로 실행 흐름을 인위적으로 제어 가능

</aside>

-   가독성을 해친다는 단점이 있으나, 다른 함수형 프로그래밍 기법으로 보완 가능

## 8.1 블록문

<aside>
💡 **블록문**
: 0개 이상의 문을 중괄호로 묶은 것으로, 코드 블록 또는 블록이라 부름

</aside>

-   자바스크립트는 블록문을 하나의 실행 단위로 취급
-   단독으로 사용할 수도 있으나, 일반적으로 제어문이나 함수를 정의할 때 사용하는 것이 일반적
-   블록문 끝에는 세미콜론을 붙이지 않음

## 8.2 조건문

<aside>
💡 **조건문**
주어진 조건식의 평가 결과에 따라 코드 블록(블록문)의 실행을 결정

</aside>

<aside>
💡 **조건식**
boolean 값으로 평가될 수 있는 표현식

</aside>

### 8.2.1 if … else문

-   주어진 조건식(참/거짓)의 평과 결과에 따라 실행할 코드 블록을 결정
-   만약 조건식이 boolean이 아닌 다른 값으로 평가되면, 자바스크립트 엔진이 암묵적으로 강제 변환

```jsx
if (조건식) {
    // 조건식이 ture
} else {
    // 조건식이 false
}
```

```jsx
if(조건식 1) {
	// 조건식 1이 ture
}
else if (조건식 2) {
	// 조건식 2가 true
	// else if는 여러 번 사용 가능
}
else {
	// 조건식 1과 조건식 2가 모두 false
}
```

-   `if{}`와 `else{}`는 한 번만 사용 가능하나, `else if{}`는 여러 번 사용 가능
-   코드 블록 내의 문이 하나라면 중괄호 생략 가능

> **_if…else문을 삼항 조건 연산자로 바꿔 쓰기_**
> `var kind = num ? (num > 0 ? ‘양수’ : ‘음수’) : ‘영’;`

-   삼항 조건 연산자는 값으로 평가되는 표현식을 만듦
-   단순히 값을 결정해 변수에 할당할 때에는 삼항 조건 연산자가 좋고, 조건과 실행 코드가 많다면 비효율적
    >

### 8.2.2 switch문

-   주어진 표현식을 평가하여 그 값과 일치하는 표현식을 갖는 case 문으로 실행 흐름을 옮김
-   case문은 상황을 의미하는 표현식을 지정하고, 콜론으로 마침
    -   표현식은 문자열이나 숫자인 경우가 많음
        > **_if…else문_**
        > 논리적 참, 거짓으로 실행할 코드 블록을 결정
        **_switch문_**
        논리적 참, 거짓보다는 다양한 상황에 따라 실행할 코드 블록 결정
        그러나 가독성이 떨어져, if…else문을 사용하는 것을 권장
        >
-   모든 case문과 일치하지 않는다면 `default문`으로 이동 (선택 사항으로 생략 가능)

```jsx
switch (표현식) {
	case 표현식1 :
		~~
		break;
	case 표현식2 :
		~~
		break;
	default:
		~~
}
```

-   case문 안에 `break;`를 쓰는 이유
      <aside>
      💡 **폴스루(fall through)** 방지
      : 모든 문이 끝날 때까지 이후의 모든 문을 실행하는 것
      - break문이 코드 블록에서 탈출하는 역할 (default는 어차피 끝나서 break 필요 없음)
      - 의도적으로 break를 걸지 않고, 여러 case를 조합해 사용 가능
      
      </aside>


## 8.3 반복문

-   조건식의 평가 결과가 참인 경우 코드 블록을 실행 (조건식이 거짓일 때까지 반복)

> **_반복문을 대체할 수 있는 다양한 기능_**

-   배열 순회 → `forEach()`
-   객체의 프로퍼티를 열거 → `for … in`
-   이터러블 순회 → `for … of`
    >

### 8.3.1 for문

```jsx
for (변수 선언문 또는 할당문 ; 조건식 ; 증감식) {
	조건식이 참인 경우 반복할 코드
}
```

-   실행 과정
    ![스크린샷 2023-09-24 오후 5.25.41.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/f15bdfe8-e824-4d79-9d88-8bf1244f8c56/9a27c216-8753-47c5-a14a-e837fb833293/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-09-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_5.25.41.png)
-   변수 선언문, 조건식, 증감식은 모두 옵션
    -   그러나 하나의 식이라도 빠뜨린다면 무한 루프 발생 (코드를 무한히 반복 실행하는 문)
        -   break문으로 탈출 가능
-   중첩 for문
    ```jsx
    for (변수 선언문 또는 할당문 ; 조건식 ; 증감식) {
    	for (변수 선언문 또는 할당문 ; 조건식 ; 증감식) {
    		조건식이 참인 경우 반복할 코드
    	}
    }
    ```

### 8.3.2 while문

-   주어진 조건식의 평가 결과가 참이면 코드 블록을 계속해서 반복 실행
-   조건문의 평과 결과가 거짓이 되면 코드 블록을 실행하지 않고 종료
    -   조건식의 평과 결과가 boolean이 아니라면, 강제 변환하여 참과 거짓을 구별

> **_for문_**
> 반복 횟수가 명확할 때

**_while문_**
반복 횟수가 불명확할 때

>

```jsx
while (조건식) {
	반복할 코드
}
```

```jsx
while (true) {
	반복할 코드
	break;
}
```

### 8.3.3 do … while문

-   코드 블록을 먼저 실행하고 조건식 평가
    ⇒ 코드 블록을 무조건 한 번 이상은 실행

```jsx
do {
	반복 실행할 코드
} while (조건식);
```

## 8.4 break문

-   레이블 문, 반복문 또는 switch 문의 코드 블록을 탈출
    -   이 외의 코드 블록에서 사용하면 `SyntaxError` 발생

<aside>
💡 **레이블 문(label statement)**
: 식별자가 붙은 문
`foo : console.log(’foo’);`

-   프로그램의 실행 순서를 제어하는 데 사용 (case, default문도 레이블 문의 일종)
-   레이블 문, 중첩 for문, 조건문 등을 탈출하려면 break문에 레이블 식별자 사용
    `break foo;`
-   남용하면 프로그램의 흐름이 복잡해져서 권장하지 않음
</aside>

> **_문자열에서 특정 문자의 인덱스 검색_**

1. `for 반복문` 사용
2. `string.indexOf()`
    >

## 8.5 continue문

-   반복문의 코드 블록 실행을 현 지점에서 중단하고 반복문의 증감식으로 실행 흐름을 이동시킴
-   반복문을 탈출하지는 않음
-   조건문 내에서 실행할 코드가 길다면 continue문을 사용하는 것이 가독성에 좋음

> **_문자열에서 특정 문자의 개수 세기_**

1. `for 반복문` 사용
2. `string.match(정규식).length`
    >
