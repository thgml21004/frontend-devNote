# Routes

[React Router](https://reactrouter.com/)

[Routes](https://reactrouter.com/en/main/components/routes)

[Route](https://reactrouter.com/en/main/route/route)

## 설치

```
npm i react-router-dom
```

### 버그

그냥 설치하면 오류 걸리기 때문에 6버전 설치&#x20;

```
npm install react-router-dom@^6.9.0
```

## 실습

### react-router dom 이용하여 코드 변경

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

### 브라우저 라우터 내려주기

[BrowserRouter](https://reactrouter.com/en/main/router-components/browser-router)

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
      <BrowserRouter>
        <App />
      </BrowserRouter>
    </StrictMode>
  ));
}

main();

```

### 테스트 코드에선 메모리 라우터 사용

[MemoryRouter](https://reactrouter.com/en/main/router-components/memory-router)

```jsx
import {render, screen} from '@testing-library/react';

import { MemoryRouter } from 'react-router-dom';
import App from './App';

const context = describe;

describe('App', async () => {
  context('when the current path is "/"', () => {
    it('renders the home page', () => {
      render((
        <MemoryRouter initialEntries={['/']}>
          <App />
        </MemoryRouter>
      ));
    });
    screen.getByText(/Welcome/);
  });
});

describe('App', async () => {
  context('when the current path is "/about"', () => {
    it('renders the about page', () => {
      render((
        <MemoryRouter initialEntries={['/about']}>
          <App />
        </MemoryRouter>
      ));
    });
    screen.getByText(/Test/);
  });
});
```
