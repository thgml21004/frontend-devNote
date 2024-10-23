---
description: React
---

# React

## 사이트 참고

(옛날문서는 코드 참고하지 말것!)

* [Ract legacy 공식문서](https://ko.legacy.reactjs.org/) : 옛날 거라서 보면 안 될 줄 알았는데, 최근에 업데이트가 됨
* [React 공식문서](https://ko.react.dev/) : 요즘 React 사용법을 다룬 공식 문서. 이것부터 읽는 걸 권장
* [Thinking in React](https://react.dev/learn/thinking-in-react) : React 작업하는 프로세스 / "상태"를 골라내는게 핵심
* [React 코어 개발자가 쓴 React에 대한 이해를 돕는 글](https://overreacted.io/react-as-a-ui-runtime/) : 필독\


## 렌더링

여러 개의 Root를 만들거나, 여러 번 render해도 된다.

여러 번 render하는 카운터 예제. 변경된 부분만 업데이트하기 때문에 하단 입력 컨트롤에 입력한 값이 그대로 유지된다.

### 참고 사이트

* [createRoot](https://react.dev/reference/react-dom/client/createRoot)
* [강의에서 언급된 예전 문서](https://ko.legacy.reactjs.org/docs/react-dom-client.html#createroot)
* [Updating a root component](https://react.dev/reference/react-dom/client/createRoot#updating-a-root-component)

### 예시1. 여러개의 root 만들기

*   main.tsx

    ```jsx
    import ReactDOM from "react-dom/client";
    import App from "./app";

    function Demo() {
        return (
            <p>Demo</p>
        )
    }

    function main() {
        const element = document.getElementById("root");
        const elementDemo = document.getElementById("demo");

        if (!element || !elementDemo) {
            return;
        }

        const root = ReactDOM.createRoot(element);
        const rootDemo = ReactDOM.createRoot(elementDemo);

        root.render(<App name='하하하' />);
        rootDemo.render(<Demo />)

    }

    main();
    ```
*   index.html

    ```jsx
    <!doctype html>
    <html lang="ko">
        <head>
            <meta charset="utf-8" />
            <title>react demo</title>
        </head>
        <body>
            <div id="root"></div>
            <div id="demo"></div>
            <script type="module" src="/src/main.tsx"></script>
        </body>
    </html>
    ```
*   app.tsx

    ```jsx
    export default function App({ name = 'psh' }: {
        name?: string
    }) {
        return (
            <p>Hellow, {name}</p>
        )
    }
    ```
* 결과\
  ![](<../.gitbook/assets/스크린샷 2024-10-23 오후 12.02.53.png>)

### 예시2. 1초마다 count

*   main.tsx

    ```jsx
    import ReactDOM from "react-dom/client";
    import App from "./app";

    function Demo({ count }: {
        count: number
    }) {
        return (
            <p>Demo : {count}</p>
        )
    }

    function main() {
        const element = document.getElementById("root");
        const elementDemo = document.getElementById("demo");

        if (!element || !elementDemo) {
            return;
        }

        const root = ReactDOM.createRoot(element);
        const rootDemo = ReactDOM.createRoot(elementDemo);

        root.render(<App name='하하하' />);

        let count = 0;
        
        // 처음 진입 시 count 시작이 0 부터 보여주려고 한번 언급
        rootDemo.render(<Demo count={count} />)

        setInterval(() => {
            count += 1;
            rootDemo.render(<Demo count={count} />)
        }, 1000);

    }

    main();
    ```
* 결과\
  1초마다 count 됨\
  ![](<../.gitbook/assets/스크린샷 2024-10-23 오후 12.06.48.png>)

## 리렌더링

### 사이트 참고

* [React는 컴포넌트를 언제 다시 리렌더링 할까요?](https://megaptera.notion.site/React-c5911858618c47d2bd716718721bff6d?pvs=4)
* &#x20;[왜 리액트에서 리렌더링이 발생하는가.](https://megaptera.notion.site/b2100b92619841cbaf3c5cc69cc3168b?pvs=4)
* [React 렌더링 동작에 대한 (거의) 완벽한 가이드](https://megaptera.notion.site/React-2b0bebf44f70424cb8ed338e59f4e431?pvs=4)



### 번외

* [면접 때 종종 나오는 (쓸모 없는) 질문인 “React는 프레임워크인가요, 라이브러리인가요?”에 대한 React 개발자의 답변](https://megaptera.notion.site/React-React-2ecaa9ba1a3e42f79e607da1b1d74e24?pvs=4)
* [제어의 역전](https://martinfowler.com/bliki/InversionOfControl.html)



### 예시1. 클릭해서 count

*   app.tsx : onClick 안에서 실행

    ```jsx
    import { useState } from "react";

    export default function App({ name = 'psh' }: {
        name?: string
    }) {
        const [count, setCount] = useState(0);

        return (
            <div>
                <p>Hellow, {name}</p>
                <p>Count: {count}</p>
                <button type="button" onClick={() => setCount(count + 1)}>클릭!</button>
            </div>
        )
    }
    ```
*   app.tsx : 함수 이벤트

    ```jsx
    import { useState } from "react";

    export default function App({ name = 'psh' }: {
        name?: string
    }) {
        const [count, setCount] = useState(0);

        const handleClick = () => {
            setCount(count + 1);
        };

        return (
            <div>
                <p>Hellow, {name}</p>
                <p>Count: {count}</p>
                <button type="button" onClick={handleClick}>클릭!</button>
            </div>
        )
    }
    ```
* 결과\
  ![](<../.gitbook/assets/스크린샷 2024-10-23 오후 12.27.50.png>)
