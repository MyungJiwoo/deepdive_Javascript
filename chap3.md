## 3.1 자바스크립트 실행 환경

-   모든 브라우저와 Node.js는 자바스크립트 엔진을 내장
    -   브라우저
        -   html, css, javascript를 실행해 웹페이지를 브라우저 화면에 렌더링하는 것이 주된 목적
        -   보안상의 이유로 파일 시스템을 제공하지 않음
    -   Node.js
        -   브라우저 외부에서 js 실행 환경을 제공하는 것이 주된 목적
    ⇒ 둘 다 ECMAScript를 실행할 수 있지만, 그 이외 추가 제공되는 기능은 호환 X

<aside>
💡 **웹 크롤링 (web crawing)**
서버에서 웹사이트의 콘텐츠를 수집하기 위해 웹사이트에서 HTML 문서를 가져온 다음, 이를 가공해서 필요한 데이터만 추출

</aside>

## 3.2 웹 브라우저

-   구글 크롬의 점유율이 65.47%로 가장 크며, 2위는 사파리로 16.97%

### 3.2.1 개발자 도구

-   단축키 : command + option + l
-   개발자 도구에서 제공하는 다양한 기능
    | 패널        | 설명                                             |
    | ----------- | ------------------------------------------------ |
    | Elements    | 렌더링된 뷰 확인                                 |
    | Console     | 에러 확인 및 js 코드에 작성한 console.log() 확인 |
    | Sources     | 디버깅                                           |
    | Network     | 네트워크 요청 정보와 성능 확인                   |
    | Application | 웹 스토리지, 세션, 쿠키 확인 및 관리             |

### 3.2.2 콘솔

-   콘솔창에서 js에 작성한 console.log()를 사용해 원하는 메시지를 확인하거나, 에러 발생시 에러 메시지를 확인할 수 있는 중요한 공간
-   shift + enter로 여러 줄 입력 가능
-   REPL 환경
      <aside>
      💡 **REPL (Read Eval Print Loop)**
      입력 수행 출력 반복 환경
      
      </aside>


### 3.2.3 브라우저에서 자바스크립트 실행

-   브라우저는 HTML 파일을 로드하면 script 태그에 포함된 자바스크립트 코드를 실행하는데, 이때 console.log()가 있다면 실행 결과가 브라우저 콘솔창에 출력

### 3.2.4

-   source 패널에서 디버깅
-   에러가 발생한 위치에 빨간 밑줄이 표시되며, 마우스를 올리면 에러 정보 표시

<aside>
💡 **디버깅**
먼저 에러 메시지를 확인하고 에러가 발생한 원인을 제거하는 것

</aside>

## 3.3 Node.js

-   프로젝트 규모가 커짐에 따라 다양한 프레임워크 또는 라이브러리를 도입하거나, Babel, Webpack, ESLint 등 여러 가지 도구를 사용할 필요가 있음
-   Node.js 와 npm 필요

### 3.3.1 Node.js와 npm 소개

-   Node.js
    -   크롬 V8 자바스크립트 엔진으로 빌드된 자바스크립트 런타임 환경
-   npm (node package manager)
    -   자바스크립트 패키지 매니저
    -   Node.js 사용할 수 있는 모듈들을 패키지화해 모아둔 저장소 역할과 패키지 설치, 관리를 위한 CLI 제공

<aside>
💡 **CLI (Command line interface)**
명령 줄 인터페이스
입력과 출력의 2단계로 이뤄짐

</aside>

[프론트엔드 프레임워크](https://www.notion.so/2409ffdd602044878b5688a88e1264bc?pvs=21)

### 3.3.2 Node.js 설치

<aside>
💡 **LTS (Long Term Support)**
장기적으로 안정된 버전

</aside>

-   설치 확인
    ```bash
    npm -v
    ```

### 3.3.3 Node.js REPL

<aside>
💡 **REPL (Read Eval Print Loop)**
간단한 자바스크립트 코드를 실행해 결과를 확인해 볼 수 있음

</aside>

-   파일 실행
    -   `ctrl + c` 두 번 누르면 Node.js REPL 종료
    ```bash
    node index.js
    // 확장자명 생략 가능
    ```

## 3.4 비주얼 스튜디오 코드

-   vsc와 같은 코드 에디터를 사용하면 코드 자동 완성, 문법 오류 감지, 디버깅, GIT 연동 등 기능 활용 가능

### 3.4.2 내장 터미널

-   터미널 이동 단축키 : `ctrl + ``

### 3.4.3 Code Runner 확장 플러그인

-   단축키를 통해 소스코드를 간단하게 실행할 수 있음
    -   `control + option + N`
-   `ReferenceError: alert is not defined`
    -   브라우저가 알림창을 띄우는 alert 함수는 브라우저에서만 동작하는 클라이언트 사이트 web api
    -   즉, alert 함수는 브라우저에서만 유효
-   ECMAScript 표준 내장 함수
    -   브라우저와 Node.js 환경에서 모두 실행 가능
-   클라이언트 사이트 Web Api
    -   브라우저 환경에서만 실행 가능

### 3.4.4 Live Server 확장 플러그인

-   소스코드를 수정할 때마다 수정 사항을 브라우저에 자동으로 반영
