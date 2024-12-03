# Router

React Router 버전 6.4부터 지원하는, 라우터 객체를 만들어서 쓰는 방법.

라우팅 정보만 별도의 파일로 관리.



## 실습

### 1차

App.tsx

-> page 함수로 빼기

```jsx
import {
  Routes, Route,
} from 'react-router-dom';

import Header from './components/Header';
import Footer from './components/Footer';

import HomePage from './pages/HomePage';
import AboutPage from './pages/AboutPage';

function Page() {
  return (
    <Routes>
      <Route path="/" element={<HomePage />} />
      <Route path="/about" element={<AboutPage />} />
    </Routes>
  );
}

export default function App() {

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

### 2차

App.tsx

```jsx
import {
  Routes, Route, createBrowserRouter, RouterProvider,
} from 'react-router-dom';

import Header from './components/Header';
import Footer from './components/Footer';

import HomePage from './pages/HomePage';
import AboutPage from './pages/AboutPage';

const routes = [
  { path: '/', element: <HomePage /> },
  { path: '/about', element: <AboutPage /> },
];

const router = createBrowserRouter(routes);

export default function App() {
  return (
    <RouterProvider router={router} />
  );
}
```

main.tsx

->기존 BrowserRouter 삭제

```jsx
import 'reflect-metadata';

import ReactDOM from 'react-dom/client';
import { StrictMode } from 'react';
// eslint-disable-next-line import/extensions,import/no-unresolved
import { BrowserRouter } from 'react-router-dom';
import App from './App';

function main() {
  const element = document.getElementById('root');

  if (!element) {
    return;
  }

  const root = ReactDOM.createRoot(element);

  root.render((
    <StrictMode>
      <App />
    </StrictMode>
  ));
}

main();
```

### 3차

... 7주차 실습 따라한 부분 확인하기
