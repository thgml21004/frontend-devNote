# MSW

## MSW (Mock Service Worker)

[MSW](https://v1.mswjs.io/)

[Service Worker API](https://developer.mozilla.org/ko/docs/Web/API/Service\_Worker\_API)

[아샬의 Mock Service Worker (MSW)](https://megaptera.notion.site/Mock-Service-Worker-MSW-4b95a309c11a46bd82fe4a478e3ce5d3?pvs=4)&#x20;

[Mocking REST API](https://v1.mswjs.io/docs/getting-started/mocks/rest-api)

[Integrate mocking into Node](https://v1.mswjs.io/docs/getting-started/integrate/node)

### 패키지 설치

```
npm i -D msw@0.36.4
```

### 세팅

jest.config.js 파일의 “setupFilesAfterEnv” 속성에 setupTests.ts 파일 추가.

```jsx
module.exports = {
  testEnvironment: 'jsdom',
  setupFilesAfterEnv: [
    '@testing-library/jest-dom/extend-expect',
    '<rootDir>/src/setupTests.ts',
  ],
  transform: {
    '^.+\\.(t|j)sx?$': ['@swc/jest', {
      jsc: {
        parser: {
          syntax: 'typescript',
          jsx: true,
          decorators: true,
        },
        transform: {
          react: {
            runtime: 'automatic',
          },
        },
      },
    }],
  },
};
```

`src/setupTests.ts` 파일 생성

```jsx
import server from './mocks/server';

beforeAll(() => server.listen({ onUnhandledRequest: 'error' }));

afterAll(() => server.close());

afterEach(() => server.resetHandlers());
```

`src/mocks/server.ts` 파일

```jsx
import { setupServer } from 'msw/node';

import handlers from './handlers';

const server = setupServer(...handlers);

export default server;
```

`src/mocks/handlers.ts` 파일

```jsx
import { rest } from 'msw';

const BASE_URL = 'http://localhost:3000';

const handlers = [
  rest.get(`${BASE_URL}/products`, (req, res, ctx) => {
    const products = [
      {
        category: 'Fruits', price: '$1', stocked: true, name: 'Apple',
      },
    ];

    return res(
      ctx.status(200),
      ctx.json({ products }),
    );
  }),
];

export default handlers;
```

`App.test.ts` 파일

```jsx
import { render, screen, waitFor } from '@testing-library/react';

import App from './App';

// jest.mock 불필요.

test('App', async () => {
  render(<App />);

  await waitFor(() => {
    screen.getByText('Apple');
  });
});
```

### fetch가 안될 때

[GitHub에서 만든 fetch polyfill](https://github.com/github/fetch)

```
npm i -D whatwg-fetch
```

`setupTests.ts`에 설정

```jsx
import 'whatwg-fetch';

import server from './mocks/server';

beforeAll(() => server.listen({ onUnhandledRequest: 'error' }));

afterAll(() => server.close());

afterEach(() => server.resetHandlers());
```

### 실행

```
npx jest --watchAll
```

`에러남..ㅎ 저번주 강의 시간에 useFetch 안됐었는데 그거때문인가? github에서 만든 fetch로 했는데도 안된다 왜 안될까? 알수가 없네..ㅎㅎㅎ`&#x20;
