# Routing

[Window.location](https://developer.mozilla.org/ko/docs/Web/API/Window/location)

[Location](https://developer.mozilla.org/ko/docs/Web/API/Location)

일반적인 웹 사이트는 URL에 따라 다른 웹 페이지를 보여준다. 하나의 웹 페이지를 하나의 컴포넌트로 만들고, URL에 따라 적절한 컴포넌트가 보이게 함으로써 구현 가능함.

## location

* location
* location.pathname : `'/'` 문자 뒤 URL의 경로를 값으로 하는 `DOMString`입니다.
* location.host : URL의 호스트 부분을 값으로 하는 `DOMString`으로, 호스트명, `':'`, 포트 번호를 포함합니다.
* location.hostname : URL의 도메인 부분을 값으로 하는 `DOMString`입니다.
* location.hash : `'#'` 문자 뒤 URL의 프래그먼트 식별자를 값으로 하는 `DOMString`입니다.
* decodeURI(location.hash)



## 실습

### 1차 - 링크 연결

Header.tsx

```jsx
export default function Header() {
  return (
    <header>
      <nav>
        <ul>
          <li>
            <a href="/">Home</a>
          </li>
          <li>
            <a href="/about">About</a>
          </li>
        </ul>
      </nav>
    </header>
  );
}
```

App.tsx

```jsx
import Header from './components/Header';
import Footer from './components/Footer';

import HomePage from './pages/HomePage';
import AboutPage from './pages/AboutPage';

export default function App() {
  const path = window.location.pathname;

  return (
    <div>
      <Header />
      <main>
        {path === '/' && <HomePage />}
        {path === '/about' && <AboutPage />}
      </main>
      <Footer />
    </div>
  );
}
```

### 2차 - path 연결

app.tsx

```jsx
import Header from './components/Header';
import Footer from './components/Footer';

import HomePage from './pages/HomePage';
import AboutPage from './pages/AboutPage';

const pages = {
  '/': HomePage,
  '/about': AboutPage,
};

export default function App() {
  const path = window.location.pathname;

  const Page = Reflect.get(pages, path) || HomePage;

  return (
    <div>
      <Header />
      <main>
        <Page />
      </main>
      <Footer />
    </div>
  );
}
```

## React

```jsx
// 이렇게 쓴걸
{path === '/' ? (
  조건문
) : null}

// 이렇게 쓸 수 있다.
{path === '/' && (
  조건문
)}

// 한 줄로 줄일 수 있다.
{path === '/' && 조건문}
```



<figure><img src="../.gitbook/assets/스크린샷 2024-12-03 오후 6.33.46.png" alt=""><figcaption></figcaption></figure>
