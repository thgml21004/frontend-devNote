# 학습 키워드

*   Express 란

    * Node.js를 사용하여 **쉽게 서버를 구성**할 수 있게 만든 클래스와 라이브러리의 집합체
    *   설치

        <pre><code>npm i express
        <strong>npm i -D @types/express
        </strong></code></pre>
    *   express 서버 예제

        ```jsx
        import express from 'express';

        const port = 3000;

        const app = express();

        app.get('/', (req, res) => {
          res.send('Hello, world!');
        });

        app.listen(port, () => {
          console.log(`Server running at http://localhost:${port}`);
        });
        ```


* URL 구조
* REST API
  * 클라이언트와 서버 간의 두 컴퓨터 시스템이 인터넷을 통해 정보를 안전하게 교환하기 위해 사용하는 인터페이스
* HTTP Method(CRUD)
  * GET(조회)
    * 데이터를 읽거나(Read) 검색(Retrieve)할 때에 사용
    * GET요청이 성공적으로 이루어진다면 XML이나 JSON과 함께 200 (Ok) HTTP 응답 코드를 리턴
    * 에러가 발생하면 주로 404 (Not found) 에러나 400 (Bad request) 에러가 발생
  * POST(등록)
    * 새로운 리소스를 생성(create)할 때 사용
    * 하위 리소스(부모 리소스의 하위 리소스)들을 생성하는데 사용
    * 데이터 조회에 성공한다면 Body 값에 저장한 데이터 값을 저장하여 성공 응답을 보냄
  * PUT(수정)
    * 리소스를 생성 / 업데이트하기 위해 서버로 데이터를 보내는 데 사용
    * URL을 통해서 어떠한 데이터를 수정할지 파라메터를 받는다. 그리고 수정할 데이터 값을 Body 값을 통해서 받음
  * DELETE(삭제)
    * 지정된 리소스를 삭제
    * URL을 통해서 어떠한 데이터를 삭제할지 파라메터를 받음
* Fetch API 란
  * 외부와 프로그램을 연결할 수 있는 창구 같은 것
  * Request와 Response 객체, 그리고 기타 네트워크 요청에 관련된 것들을 사용
  *   기본 리소스 요청

      ```jsx
      async function logJSONData() {
        const response = await fetch("http://example.com/movies.json");
        const jsonData = await response.json();
        console.log(jsonData);
      }
      ```
* Promise
  * 서버에서 받아온 데이터를 화면에 표시하기 위해 사용
  *   예시?

      ```jsx
      // Promise
      fetch('http://localhost:3000/products'); 

      // Response
      fetch('http://localhost:3000/products'); 
      ```
* ReadableStream
  * 바이트 데이터를 읽을수 있는 스트림을 제공
  *   예시?

      ```jsx
      // response.body는 ReadableStream
      const response = await fetch('http://localhost:3000/products'); 
      ```
* Unicode
  * 전 세계의 모든 문자를 표현할 수 있도록 설계된 문자 인코딩 표준
  * 문자셋을 처리할 수 있는 기능을 제공
  * 문자열을 **UTF-8** 인코딩 형식으로 처리
* CORS 란
  * 교차 출처 리소스 공유
  * 브라우저가 자신의 출처가 아닌 다른 어떤 출처(도메인, 포트)로부터 자원을 로딩하는 것을 허용하도록 서버가 허가 해주는 HTTP
  *   설치

      <pre><code>npm i cors
      <strong>npm i -D @types/cors
      </strong></code></pre>
  *   미들웨어 사용

      ```
      import express from 'express';
      import cors from 'cors';

      const app = express();

      app.use(cors());
      ```
* React Hook 이란
  * 리액트 클래스형 컴포넌트에서 이용하던 코드를 작성할 필요없이 함수형 컴포넌트에서 다양한 기능을 사용할 수 있게 만들어준 라이브러리
  * 기존 Class 바탕의 코드를 작성할 필요 없이 상태 값과 여러 React의 기능을 사용
* useState
  * 상태를 관리하는 훅
  * 초기값을 설정할 수 있으며, 초기값은 첫 렌더링 때 한번 사용
  *   예시

      ```jsx
      import React, { useState } from 'react';

      function Example() {
        // "count"라는 새 상태 변수를 선언합니다
        const [count, setCount] = useState(0);

        return (
          <div>
            <p>You clicked {count} times</p>
            // 버튼을 클릭할 때마다 기존의 state 기본값인 0에 1이 더해진다.
            <button onClick={() => setCount(count + 1)}>
              Click me
            </button>
          </div>
        );
      }
      ```
* useEffect
  * &#x20;외부 시스템과 컴포넌트를 동기화 하는 훅
  * 렌더링 때마다 실행되므로, 의존성 배열을 통해 언제 이펙트를 실행할지 지정
  *   마운트될 때 한번만 실행

      ```jsx
      // 빈 배열([])
      useEffect(() => {
        console.log('Component mounted!');
      }, []);
      ```
  *   의존성 배열에 특정 값 지정

      ```jsx
      // count 값이 변경될 때만 실행
      useEffect(() => {
        console.log(`Count has changed to ${count}`);
      }, [count])
      ```

      ```jsx
      // count 값이 변경될 때만 실행
      useEffect(() => {
        console.log(`Count has changed to ${count}`);
      }, [count])
      ```
  *   의존성 배열이 없는 경우

      ```jsx
      // 매 렌더링마다 실행
      useEffect(() => {
       console.log('Component rendered or updated!'); 
      });
      ```
* useContext
  * 컴포넌트에서 context를 읽고 구독할  수 있는 훅
  *   예시

      ```jsx
      const value = useContext(SomeContext)
      ```
* useRef
  * 특정 DOM에 접근하여 DOM 조작을 가능하게 하는 훅
  * 렌더링에 필요하지 않은 값을 참조할 수 있는 훅
  *   예시

      ```jsx
      const ref = useRef(initialValue)
      ```
* useLayoutEffect
  * 브라우저가 화면을 다시 그리기 전에 실행되는 훅
  *   예시

      ```
      useLayoutEffect(setup, dependencies?)
      ```
* React StrictMode 란
  * 애플리케이션 내의 잠재적인 문제를 알아내기 위한 도구
  * 자손들에 대한 부가적인 검사와 경고 활성화
  * 개발 모드에서만 활성화되기 때문에, 프로덕션 빌드에는 영향을 끼치지 않음
* Hook의 규칙
  1. 최상위(at the Top Level)에서만 Hook을 호출
  2. #### 오직 React 함수 내에서 Hook을 호출 <a href="#only-call-hooks-from-react-functions" id="only-call-hooks-from-react-functions"></a>
* usehooks-ts
  * 간단한 서버를 만들고, custom hook 을 사용하여 서버에서 데이터를 받아옴
  *   설치

      ```
      npm i usehooks-ts
      ```
* useBoolean
  * **불리언 상태**를 관리하는 커스텀훅
  * 참/거짓을 다룰 땐 toggle 같이 의도가 명확한 함수를 쓰는 게 좋다.
* useEffectOnce
  * **useEffect**를 **한 번만 실행**하도록 하는 커스텀 훅
  * 의존성 배열을 빈 배열로 넣어서 한 번만 실행하는 Effect 를 잡아줄 때가 많은데, useEffectOnce 를 쓰면 더 명확히 드러난다.
  * **useEffectOnce**와 **useEffect**의 차이점
    * useEffect : 의존성 배열에 값이 변경될 때마다 실행 / 빈 배열(\[])을 사용하면 컴포넌트가 **마운트될 때만** 한 번 실행
    * useEffectOnde : **useEffect**를 **한 번만 실행**하도록 래핑 / 의존성 배열을 직접 관리하는 것보다 훨씬 간편하게 사용
* useFetch
  * 데이터 fetching 작업을 React 컴포넌트에서 간편하게 처리
  * loading, data, error 상태를 관리
    * **loading**: 데이터를 요청 중일 때 `true`로 설정
    * **data**: 요청이 성공적으로 완료되었을 때 응답 데이터
    * **error**: 요청 중에 발생한 오류
* useInterval
  * **특정 시간** 간격마다 **반복적으로 실행**되는 작업(예: 타이머, 데이터 polling 등)을 쉽게 구현하는 커스텀훅
* useEventListener
  * **DOM 이벤트**를 React 컴포넌트에서 간편하게 처리할 수 있도록 돕는 커스텀 훅
* useLocalStorage
  * **로컬 스토리지(LocalStorage)**&#xB97C; **React 상태**처럼 쉽게 다룰수 있는 커스텀 훅
  * localStorage를 활용하여 데이터를 저장하고 불러오는 과정을 React 상태 관리와 비슷한 방식으로 처리
  * 새로 고침 시에도 계속 유지 / 사용자 설정이나 임시 데이터를 저장할 때 사용
* useDarkMode
  * 사용자가 선택한 **다크 모드** 또는 **라이트 모드** 설정을 관리
  * 로컬 스토리지에 저장하여 페이지 새로 고침 후에도 유지
* swr
  * 데이터 패칭 라이브러리
  * API 요청을 간소화하고 상태 관리 및 UI 업데이트를 최적화
  * 데이터 요청, 캐싱, 재검증, 자동 리프레시 등 처리
  * 주요 기능
    * **자동 캐싱**: 요청된 데이터는 내부적으로 자동으로 캐시되어, 같은 데이터 요청이 있을 때 불필요한 네트워크 요청을 피할 수 있습니다.
    * **자동 리패칭**: 데이터를 일정 시간 간격으로 다시 가져오도록 설정할 수 있어 최신 데이터를 유지할 수 있습니다.
    * **백그라운드 재검증**: 데이터가 사용되면 SWR은 백그라운드에서 데이터를 다시 요청하여 최신 상태로 유지합니다.
    * **Error Handling**: 오류 발생 시 재시도하거나 에러 메시지를 관리할 수 있습니다.
    * **Suspense와의 호환성**: React Suspense와 함께 사용할 수 있어 더 나은 로딩 상태 관리를 지원합니다.
  *   설치

      ```
      npm install swr
      ```
* react-query
  * 서버 상태를 관리하는 라이브러리
  * **서버에서 가져온 데이터**를 효율적으로 **패칭, 캐싱, 동기화 및 업데이트**할 수 있도록 도움
  *   설치

      ```
      npm install @tanstack/react-query
      ```
