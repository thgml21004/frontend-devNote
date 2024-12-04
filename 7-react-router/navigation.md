# Navigation

## History.pushState

[History.pushState](https://developer.mozilla.org/ko/docs/Web/API/History/pushState)

```jsx
import { SyntheticEvent } from 'react';

export default function Header() {
  const handleClick = (event: SyntheticEvent) => {
    event.preventDefault(); // 이벤트 동작 막음
    const state = {};
    const title = '';
    const url = '/about';
    window.history.pushState(state, title, url);
  };

  return (
    <header>
      <nav>
        <ul>
          <li>
            <a href="/" onClick={handleClick}>Home</a>
          </li>
          <li>
            <a href="/about" onClick={handleClick}>About</a>
          </li>
        </ul>
      </nav>
    </header>
  );
}
```

## Link

[Link](https://reactrouter.com/en/main/components/link)

-> active={..} active를 특수하게 사용할 때 (현재 페이지 위치를 얻을 수 있다.)

-> className={abc ? 'active' : ''}

```jsx
import { Link } from 'react-router-dom';

export default function Header() {
  return (
    <header>
      <nav>
        <ul>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/about">About</Link>
          </li>
        </ul>
      </nav>
    </header>
  );
}
```

## NavLink

[NavLink](https://reactrouter.com/en/main/components/nav-link)

-> active 클래스가 자동으로 들어가짐

```jsx
import { NavLink } from 'react-router-dom';

export default function Header() {
  return (
    <header>
      <nav>
        <ul>
          <li>
            <NavLink to="/">Home</NavLink>
          </li>
          <li>
            <NavLink to="/about">About</NavLink>
          </li>
        </ul>
      </nav>
    </header>
  );
}

```

## Navigate

[Navigate](https://reactrouter.com/en/main/components/navigate)

Header.tsx

```jsx
import { Link } from 'react-router-dom';

export default function Header() {
  return (
    <header>
      <nav>
        <ul>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/about">About</Link>
          </li>
          <li>
            <Link to="/logout">Log out</Link>
          </li>
        </ul>
      </nav>
    </header>
  );
}
```

routes.tsx

```jsx
import Layout from './components/Layout';

import HomePage from './pages/HomePage';
import AboutPage from './pages/AboutPage';
import LogoutPage from "./pages/LogoutPage";

const routes = [
  {
    element: <Layout />,
    children: [
      { path: '/', element: <HomePage /> },
      { path: '/about', element: <AboutPage /> },
      { path: '/logout', element: <LogoutPage /> },
    ],
  },
];

export default routes;
```

LogoutPage.tsx

-> logout 클릭하면 home으로 이동

```jsx
import { Navigate } from 'react-router-dom';

export default function LogoutPage() {
  return (
    <Navigate to="/" />
  );
}
```



```jsx
import { Navigate } from 'react-router-dom';

export default function LoginPage() {
  return (
    <Navigate to="/" />
  );
}
```

테스트에서 “ReferenceError: Request is not defined” 에러가 나면 “whatwg-fetch”를 임포트해서 해결할 수 있다.

### whatwg-fetch 설치

```
npm i -D whatwg-fetch
```

### 세팅

setupTests.ts 파일에 설정

```jsx
// eslint-disable-next-line import/no-extraneous-dependencies
import 'whatwg-fetch';
```

## useNavigate

[useNavigate](https://reactrouter.com/en/main/hooks/use-navigate)

->  이걸 더 많이 사용

Header.tsx

```jsx
import { Link, useNavigate } from 'react-router-dom';

export default function Header() {
  const navigate = useNavigate();

  const handleClickLogout = () => {
    navigate('/');
  };

  return (
    <header>
      <nav>
        <ul>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/about">About</Link>
          </li>
          <li>
            <button type="button" onClick={handleClickLogout}>
              Logout
            </button>
          </li>
        </ul>
      </nav>
    </header>
  );
}
```

