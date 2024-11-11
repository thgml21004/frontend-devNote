---
description: Node.js
---

# 개발환경세팅

## Node 세팅

* 경로 : [https://nodejs.org/en/download/package-manager](https://nodejs.org/en/download/package-manager)
* LTS 버전 : 짝수(22.xx.xx) / 안정적 O
* 현재 버전 : 홀수(21.xx.xx) / 최신 버전 / 안정적 X
* 버전 별 정리 : [https://nodejs.org/en/blog/all](https://nodejs.org/en/blog/all)
*   node 설치\
    \=> 맥북에 노드 최신버전 (22) 설치되어 있었음으로 버전 다운그레이드 함\
    \=> 20 LTS 다운그레이드

    ```
    // NVM 설치 여부 확인
    nvm --version

    // 설치 안되어 있으면 NVM 설치
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash

    // 환경 변수 새로고침 (작업한 Mac OS의 기본 쉘이 zsh)
    source ~/.zshrc

    // Node 버전 확인 및 설치 가능 버전
    nvm ls-remote

    // 특정 버전 설치(20버전 설치함)
    nvm install 20

    // Node 버전 확인
    node -v
    ```

## TypeScript 세팅

### 프로젝트 폴더 생성

```
// 폴더 생성
mkdir my-app

// 코딩 프로그램 열기

// 파일 생성 
touch test.txt

// 파일 삭제
rm test.txt
```

### npm 패키지 설치&#x20;

\=> package.json 파일 생성 됨

```
// 설치 내용 확인 하면서 설치 가능
npm init

// 물어보는 내용 다 yes로 하여 빠르게 설치 가능
npm init -y
```

*   package.json\
    npm run test / npm test => test안의 메시지 출력 됨

    ```
    {
      "name": "my-app", // 프로젝트 폴더명
      "version": "1.0.0", // 버전 관리
      "description": "", // 프로젝트 설명
      "main": "index.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "keywords": [],
      "author": "", // 프로젝트 작성자
      "license": "ISC"
    }
    ```

### .gitignore 파일 생성 (필수)

\=> .gitignore 파일 한번에 넣기 [사이트](https://www.toptal.com/developers/gitignore) > node 검색해서 다 붙여 넣어도 됨\
\=> 필수로 넣어야 되는 것

```
/node_modules/
/dist/
.parcel-cache
```

### TypeScript 설정

```
// 개발환경에서 도구로 설치할것은 -D
// package.json에서 보면 devDependencies 선언 됨
npm i -D typescript

// 타입스크립트 컴파일러 초기화
// npx : 설치하지 않아도 실행 가능
// tsconfig.json 파일 생성 됨
npx tsc --init
```

*   tsconfig.json\
    \=> jsx 주석 풀기

    ```
    "jsx": "react-jsx",
    ```



### ESLint 설정

```
// ESLint 설치
npm i -D eslint

// 설정 초기화
// eslint.config.mjs 파일 생성 됨
npx eslint --init
```

* 설치 시 선택한 답\
  ![](<../.gitbook/assets/스크린샷 2024-10-22 오후 4.55.34.png>)

### .eslintignore 파일 생성 (필수)

\=> 필수로 넣어야 되는 것\
\=> .gitignore 넣은 것과 똑같이 넣어 됨

```
/node_modules/
/dist/
.parcel-cache
```

### 리액트 설치

```
// 리액트 설치
npm i react react-dom

// types 도구 설치
npm i -D @types/react @types/react-dom
```

### 테스팅 도구 설치 (jest / swc)

```
// 테스팅 도구 설치
npm i -D jest @types/jest @swc/core @swc/jest \
    jest-environment-jsdom \
    @testing-library/react @testing-library/jest-dom@5.16.4
```

*   jest.config.js 파일 생성 (_빌드하기 위해?_)\
    \=> 내용 전체 복붙 : [경로](https://github.com/megaptera-kr/textbook/blob/main/usestore-ts-example/jest.config.js)\
    \=> './jest.setup', 삭제 > 안쓰기 때문에\
    \=> eslint 고치는 명령어

    ```
    // eslint 검사
    npx eslint .

    // eslint 고치기
    npx eslint --fix .
    ```

### Parcel 설치

\=> 웹서버를 띄울 수 있다.

```
npm i -D parcel
```

기본 설치 완료

***

### 추가 세팅

* package.json 파일 명령어 수정\
  \=> [경로](https://github.com/megaptera-kr/textbook/blob/main/usestore-ts-example/package.json) > "scripts" 명령어 부분 복붙\
  \=> "main": "index.js" > "source": "index.html"로 변경
* index.html 파일 생성
* src/main.tsx 파일 생성

***

## 화면 작성

### 예시 1. 기본

*   index.html

    ```html
    <!doctype html>
    <html lang="ko">
        <head>
            <meta charset="utf-8" />
            <title>react demo</title>
        </head>
        <body>
            <div id="root"></div>
            <script type="module" src="/src/main.tsx"></script>
        </body>
    </html>
    ```
*   src/main.tsx

    ```typescript
    import ReactDOM from "react-dom/client";

    const element = document.getElementById("root");

    if (element) {
        const root = ReactDOM.createRoot(element);

        root.render(<p>Hello!</p>)
    }
    ```
* 결과 화면\
  ![](<../.gitbook/assets/스크린샷 2024-10-22 오후 5.35.50 (1).png>)

### 예시2. 입력값 출력

*   src/main.tsx

    ```typescript
    import ReactDOM from "react-dom/client";

    function App() {
        return (
            <p>Hellow, wolrd!</p>
        )
    }

    const element = document.getElementById("root");

    if (element) {
        const root = ReactDOM.createRoot(element);

        root.render(<App />)
    }
    ```
*   결과 화면\
    ![](<../.gitbook/assets/스크린샷 2024-10-22 오후 5.44.32.png>)

