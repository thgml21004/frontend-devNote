# 학습 키워드

## HTML DOM API

### 개념

* HTML의 각 elements의 기능을 정의하는 인터페이스와  해당 요소가 의존하는 모든 지원 유형 및 인터페이스
* JavaScript가 HTML 문서의 구조와 상호작용할 수 있도록 해주는 인터페이스

## Location

### 개념

* 자바스크립트에서 window.location, document.location을 통해 접근 가능
* 현재 브라우저 열려있는 페이지의 위치
* 현재 페이지의 URL이 객체화

### 예시

* location.pathname : `'/'` 문자 뒤 URL의 경로를 값으로 하는 `DOMString`입니다.
* location.host : URL의 호스트 부분을 값으로 하는 `DOMString`으로, 호스트명, `':'`, 포트 번호를 포함합니다.
* location.hostname : URL의 도메인 부분을 값으로 하는 `DOMString`입니다.
* location.hash : `'#'` 문자 뒤 URL의 프래그먼트 식별자를 값으로 하는 `DOMString`입니다.

## pathname

* URL의 경로 부분
* https://example.com/about에서 **pathname**은 **/about**
* 라우팅된 페이지의 경로를 나타내는데 사용

## 라우터란?

* 사용자의 요청에 따라 적절한 페이지나 컴포넌트를 선택하여 렌더링하는 역할

## React Router

* 사용자가 입력한 주소를 감지하는 역할
* 여러 환경에서 동작할 수 있도록 여러 종유의 라우터 컴포넌트를 제공

## NavLink, Link, Navigate, useNavigate

### NavLink

* 활성화된 링크에 스타일을 자동으로 추가하는 기능
* 현재 URL경로와 일치하는 to경로에 스타일 적용 가능

```jsx
import { NavLink } from 'react-router-dom';

function Header() {
  return (
    <header>
      <nav>
        <ul>
          <li><NavLink to="/">Home</NavLink></li>
          <li><NavLink to="/about">About</NavLink></li>
        </ul>
      </nav>
    </header>
  );
}
```

### Link

* 페이지 내에서 다른 경로로 이동하는 링크
* 페이지를 새로고침하지 않고 URL 변경하고, 해당 경로에 맞는 컴포넌트를 랜더링함

```jsx
import { Link } from 'react-router-dom';

const Navigation = () => {
  return (
    <nav>
      <Link to="/">Home</Link>
      <Link to="/about">About</Link>
    </nav>
  );
};
```

### Navigate

* 라우팅을 제어
* 특정 이벤트나 조건에서 리다이렉트 할 수 있음
* 특정 경로로 자동으로 리다이렉트

```jsx
import { Navigate } from 'react-router-dom';

const RedirectComponent = () => {
  return <Navigate to="/home" />;
};
```

### useNavigate

* 네비게이션을 제어
* `navigate()` 함수를 사용하여 페이지를 동적으로 이동

```jsx
import { useNavigate } from 'react-router-dom';

const MyComponent = () => {
  const navigate = useNavigate();

  const handleNavigation = () => {
    navigate('/about');  // '/about' 경로로 이동
  };

  return (
    <div>
      <button onClick={handleNavigation}>Go to About</button>
    </div>
  );
};
```

## RouterProvider

### 개념

* 라우터를 설정할 때 사용하는 컴포넌트
* `createBrowserRouter`나 `createHashRouter`를 사용하여 라우팅을 설정하고, 생성된 라우터 설정을 `RouterProvider`에 전달

### 예시

```jsx
import React from 'react';
import ReactDOM from 'react-dom';
import { RouterProvider, createBrowserRouter } from 'react-router-dom';

// 페이지 컴포넌트들
import HomePage from './HomePage';
import AboutPage from './AboutPage';

const router = createBrowserRouter([
  {
    path: "/",
    element: <HomePage />,
  },
  {
    path: "/about",
    element: <AboutPage />,
  },
]);

const App = () => {
  return <RouterProvider router={router} />;
};

ReactDOM.render(<App />, document.getElementById('root'));

```

### 특징

* **라우터 설정 관리**: `RouterProvider`는 애플리케이션에서 라우터 설정을 관리하며, 라우팅 구조와 동작을 정의합니다.
* **라우터 객체 전달**: `RouterProvider`는 `createBrowserRouter`, `createHashRouter` 또는 `createMemoryRouter`와 같은 라우터 생성 함수에서 반환되는 라우터 객체를 받아야 합니다.
* **라우팅 환경 설정**: `RouterProvider`는 라우팅 환경을 초기화하며, 애플리케이션 전체에서 URL 변경에 따라 컴포넌트를 렌더링할 수 있도록 합니다.
* **라우팅 상태 관리**: `RouterProvider`는 `React Router`의 상태를 관리하며, URL 변경 시 적절한 컴포넌트를 렌더링합니다.

## Browser Router

### 개념

* **HTML5의 History API**를 기반으로 작동하여 페이지 간 네비게이션을 처리

### 예시

```jsx
import React from 'react';
import ReactDOM from 'react-dom';
import { BrowserRouter, Route, Routes } from 'react-router-dom';

// 페이지 컴포넌트들
import HomePage from './HomePage';
import AboutPage from './AboutPage';

const App = () => {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<HomePage />} />
        <Route path="/about" element={<AboutPage />} />
      </Routes>
    </BrowserRouter>
  );
};

ReactDOM.render(<App />, document.getElementById('root'));

```

### 특징

* **History API 사용**: `BrowserRouter`는 브라우저의 History API (`pushState`, `replaceState`)를 사용하여 URL을 변경하고 페이지를 새로 고침하지 않고도 다른 컴포넌트를 렌더링할 수 있습니다.
* **경로 관리**: URL 경로가 변경되면 해당 경로에 맞는 컴포넌트를 렌더링합니다.
* **HTML5 URL**: URL은 `/#/about` 대신에 `/about`와 같은 형태로 나타나며, 페이지의 URL을 깔끔하게 유지할 수 있습니다.

## Memory Router

### 개념

* 브라우저의 주소 표시줄을 사용하지 않고 메모리 내에서 라우팅을 관리

### 예시

```jsx
import React from 'react';
import ReactDOM from 'react-dom';
import { MemoryRouter, Route, Routes } from 'react-router-dom';

// 페이지 컴포넌트들
import HomePage from './HomePage';
import AboutPage from './AboutPage';

const App = () => {
  return (
    <MemoryRouter initialEntries={['/about']} initialIndex={0}>
      <Routes>
        <Route path="/" element={<HomePage />} />
        <Route path="/about" element={<AboutPage />} />
      </Routes>
    </MemoryRouter>
  );
};

ReactDOM.render(<App />, document.getElementById('root'));

```

### 특징

* **URL 변경 없음**: `MemoryRouter`는 브라우저의 주소 표시줄에 URL을 표시하지 않으며, 모든 라우팅 상태를 **메모리 내**에서 처리합니다. 따라서 경로 변경 시 브라우저의 URL은 업데이트되지 않습니다.
* **서버 사이드 렌더링(SSR)에서 유용**: 브라우저의 주소 표시줄을 다룰 필요 없이 애플리케이션의 라우팅을 처리할 수 있기 때문에 SSR 환경에서 사용됩니다.
* **테스트 환경에서 사용**: 라우팅을 테스트할 때도 `MemoryRouter`를 사용하여 테스트의 독립성을 유지하면서, 브라우저의 주소 표시줄을 변경하지 않고 라우팅을 처리할 수 있습니다.

## Route

### 개념

* React Router에서 경로(path)와 해당 경로에서 렌더링할 컴포넌트를 연결

### 예시

```jsx
import { Routes, Route } from 'react-router-dom';

import Header from './components/Header';
import Footer from './components/Footer';

import HomePage from './pages/HomePage';
import AboutPage from './pages/AboutPage';

export default function App() {
  return (
    <div>
      <Header />
      <main>
        <Routes>
          <Route path="/" element={<HomePage />} />
          <Route path="/about" element={<AboutPage />} />
        </Routes>
      </main>
      <Footer />
    </div>
  );
}
```

### 속성

* **path**: 경로를 설정합니다. 사용자가 이 경로로 이동할 때, 해당 경로에 연결된 `element` 컴포넌트가 렌더링됩니다.
* **element**: 경로에 맞는 컴포넌트를 지정합니다. `element`는 JSX로 정의된 컴포넌트를 받을 수 있습니다.
* **index**: `index` 속성을 `true`로 설정하면, 해당 `Route`는 부모 `Route`의 기본 경로로 작동합니다. 이 경우, 경로가 정확히 일치하는 경우에만 렌더링됩니다.

## Web APIs - History

### 기능

*   **history.pushState()**: 현재 페이지를 새 페이지로 대체하지 않고, 브라우저의 세션 기록 스택에 새 항목을 추가합니다. 주로 URL을 변경하고 페이지를 새로 고침 없이 업데이트할 때 사용됩니다.

    ```jsx
    // 현재 페이지에서 URL을 '/about'으로 변경
    history.pushState({ page: 'about' }, 'About', '/about');

    // 브라우저의 주소 표시줄에 '/about'이 표시되지만 페이지는 새로 고침되지 않습니다.
    ```
*   **history.replaceState()**: 현재 페이지를 새 페이지로 대체합니다. 이 메서드는 `pushState()`와 유사하지만, 브라우저의 세션 기록 스택을 변경하지 않고 현재 항목만 수정합니다.

    ```jsx
    // URL을 '/profile'로 바꾸고 현재 상태를 대체
    history.replaceState({ page: 'profile' }, 'Profile', '/profile');
    ```
* **history.state**: 현재 활성화된 기록 항목의 상태 객체를 반환합니다. 이 객체는 `pushState()`나 `replaceState()`로 설정된 상태 값을 나타냅니다.
*   **history.back()**: 브라우저의 이전 페이지로 이동합니다. 이는 사용자가 브라우저의 뒤로가기 버튼을 클릭할 때와 동일한 기능을 합니다.

    ```jsx
    // 뒤로 가기
    history.back();
    ```
*   **history.forward()**: 브라우저의 다음 페이지로 이동합니다. 이는 사용자가 브라우저의 앞으로가기 버튼을 클릭할 때와 동일한 기능을 합니다.

    ```jsx
    // 앞으로 가기
    history.forward();
    ```
*   **history.go()**: 주어진 숫자만큼 히스토리 항목을 이동합니다. 예를 들어, `history.go(-1)`은 뒤로 한 페이지 이동을 의미하고, `history.go(2)`는 앞으로 두 페이지 이동을 의미합니다.

    ```jsx
    // 한 페이지 뒤로 이동
    history.go(-1);

    // 두 페이지 앞으로 이동
    history.go(2);
    ```
*   **window.onpopstate**: 브라우저의 세션 기록 항목이 변경될 때마다 발생하는 이벤트입니다. 이 이벤트는 사용자가 뒤로 가기나 앞으로 가기 버튼을 클릭하거나, `pushState()`나 `replaceState()`로 URL이 변경될 때 트리거됩니다.

    ```jsx
    // 페이지의 상태 변경을 감지
    window.onpopstate = (event) => {
      console.log('현재 상태:', event.state);
      // 'popstate' 이벤트가 발생할 때마다 상태를 처리할 수 있습니다.
    };
    ```
