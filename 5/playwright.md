# Playwright

[Playwright](https://playwright.dev/)

[Playwright Configuration](https://playwright.dev/docs/test-configuration)

[Ashal의 Playwright](https://megaptera.notion.site/Playwright-63daee13a990446bad9d8f1c22a00ec6?pvs=4)

### 패키지 설치

```
npm i -D @playwright/test eslint-plugin-playwright
```

### 세팅

`playwright.config.ts` 파일

```jsx
import { PlaywrightTestConfig } from '@playwright/test';

const config: PlaywrightTestConfig = {
  testDir: './tests',
  retries: 0,
  use: {
    channel: 'chrome',
    baseURL: 'http://localhost:8080',
    headless: !!process.env.CI,
    screenshot: 'only-on-failure',
  },
};

export default config;
```

`tests/.eslintrc.js` 파일

```jsx
module.exports = {
  env: {
    jest: false,
  },
  extends: ['plugin:playwright/playwright-test'],
  rules: {
    'import/no-extraneous-dependencies': 'off',
  },
};
```

`tests/home.spec.ts` 파일

```jsx
import { test, expect } from '@playwright/test';

test('Show all products', async ({ page }) => {
  await page.goto('/');

  await expect(page.getByText('Apple')).toBeVisible(); // 어떤건 있고
  await expect(page.getByText('Grape')).toBeHidden(); // 어떤건 없다.
});

```

### 테스트 실행

```
// 화면을 랜더링하기 때문에 좀 느림
npx playwright test

// 더 빠르게 확인 하려면 이 명령어
CI=true npx playwright test
```

`실행 시 3000 서버와 8080 포트 열고선 테스트 실행 해야된다.`



`tests/home.spec.ts` 파일

```jsx
import { test, expect } from '@playwright/test';

// 데이터에 'Apple'이 있을 때, 보이고 'Grape' 있으면 숨김 테스트
test('Show all products', async ({ page }) => {
  await page.goto('/');

  await expect(page.getByText('Apple')).toBeVisible();
  await expect(page.getByText('Grape')).toBeHidden();
});

// input에 'a'입력했을 때 테스트
test('Filter products', async ({ page }) => {
  await page.goto('/');

  await expect(page.getByText('Apple')).toBeVisible();

  const searchInput = page.getByLabel('Search'); // label로 찾은 input

  await searchInput.fill('a'); // a를 넣는다.

  await expect(page.getByText('Apple')).toBeVisible(); // 보였다가

  await searchInput.fill('aa'); // aa를 넣는다.

  await expect(page.getByText('Apple')).toBeHidden(); // 숨겨짐
});

// Increase 버튼을 13번 클릭 했을 때 테스트
test('Click the “Increase” button', async ({ page }) => {
  await page.goto('/');

  const count = 13;

  await Promise.all((
    [...Array(count)].map(async () => {
      await page.getByText('Increase').click();
    })
  ));

  await expect(page.getByText(`${count}`)).toBeVisible();
});
```

!'가가' -> 문자열은 비어있지 않으면 true이기 때문에 false

!!'가가' -> true

### .gitignore에 에러 상황 스크린샷 파일 제거

`.gitignore` 파일에 에러 상황의 스크린샷 등이 담기는 `test-results` 디렉터리 추가.

```
/test-results/
```

<figure><img src="../.gitbook/assets/스크린샷 2024-11-19 오후 8.26.10.png" alt=""><figcaption></figcaption></figure>

### E2E 테스팅 도구 CodeceptJS

[CodeceptJS](https://codecept.io/)

[CodeceptJS 3 시작하기](https://megaptera.notion.site/CodeceptJS-3-596f707e911e40668858f381fd12cdd3?pvs=4)

[CodeceptJS 사용 예시](https://megaptera.notion.site/CodeceptJS-da08dc50ba9549f69be468ab8ebc13bf?pvs=4)
