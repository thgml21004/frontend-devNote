---
description: Jest & React Test Library
---

# Testing Library

## JEST

### 참고사이트

* [Jest 공식문서](https://jestjs.io/)
* [BETTER SPECS](https://www.betterspecs.org/) : RSpec 베스트 프랙티스 모음. 그대로 쓸 수는 없지만, 참고하자.
* [Ginkgo - Go 언어 개발자를 위한 BDD 테스팅 프레임워크](https://youtu.be/gfTsSBRvdqI) : Go 언어 사례
* [JUnit5로 계층 구조의 테스트 코드 작성하기](https://johngrib.github.io/wiki/junit5-nested/) : Java 언어 사례
* [Let’s RSpec](https://megaptera.notion.site/Let-s-RSpec-dce5253c17e3427496174eff4e63c0f4?pvs=4) : Jest는 RSpec의 let 같은 걸 지원하지 않기 때문에, 핵심 아이디어를 가져와서 적당한 수준에서 잘 써야 한다.
* [Given-When-Then](https://megaptera.notion.site/Given-When-Then-5b2e7e746be140a0a6e26e642b52c1e5?pvs=4)

### 기본 테스트 코드

*   src/main.test.ts 파일 생성

    ```typescript
    test('숫자 더하기', () => {
        expect(1 + 2).toBe(3);
    })
    ```
*   터미널 명령어 입력 &#x20;

    ```
    npm test
    ```

    *   명령어 안먹혀서 chatGPT 도움으로 해결\
        \=> jest.setup.js 파일생성하고 설정 추가 후 실행 됨

        ```
        // jest.setup.js

        import '@testing-library/jest-dom';
        ```
* 결과
  *   실패

      <figure><img src="../.gitbook/assets/스크린샷 2024-10-23 오후 2.44.40 (1).png" alt=""><figcaption><p>Fail</p></figcaption></figure>
  *   성공

      <figure><img src="../.gitbook/assets/스크린샷 2024-10-23 오후 2.43.44 (1).png" alt=""><figcaption><p>Pass</p></figcaption></figure>

### BDD 스타일의 테스트 코드

테스트 짜고 그 후 구현부 작성 후 테스트 결과 확인

*   main.test.ts

    ```typescript
    function add(x: number, y: number) : number {
        return x + y;
    }

    test('숫자 더하기', () => {
        expect(add(1, 2)).toBe(3);
    })
    ```
*   터미널 명령 : 실시간 테스트 결과 확인 가능

    ```
    npm run watch:test
    ```
*   결과



    <figure><img src="../.gitbook/assets/스크린샷 2024-10-23 오후 2.53.26.png" alt=""><figcaption></figcaption></figure>

### 주어가 되는 테스트

### 예시 1.&#x20;

```typescript
function add(x: number, y: number) : number {
    return x + y;
}

describe('add 함수', () => {
    it('returns sum of two numbers', () => {
        expect(add(1, 2)).toBe(3);
    })
})
```

### 예시 2.

```typescript
function add(x: number, y: number) : number {
    return x + y;
}

const context = describe;

describe('add 함수', () => {
    it('두 숫자의 합을 리턴', () => {
        expect(add(1, 2)).toBe(3);
    })
    context('두 개의 양수가 주어졌을 때', () => {
        it('항상 두개의 숫자보다 큰 값을 돌려준다.', () => {
            expect(add(1, 2)).toBeGreaterThan(1);
        })
    })
})
```

## React Test Library

### 참고 사이트

* [React Testing Library 공식문서](https://testing-library.com/docs/react-testing-library/intro)
* [jest-dom](https://testing-library.com/docs/ecosystem-jest-dom/)

### 참고 영상

* [프론트엔드(Front-end)도 테스트해야 하나요?](https://youtu.be/-kUmsKRmOnA)
* [Mocking 때문에 테스트 코드를 작성하기 어렵나요](https://youtu.be/RoQtNLl-Wko)

### 간단 테스트 코드

```typescript
import {render, screen} from "@testing-library/react";
import Greeting from "./Greeting";

test('Greeting', () => {
    render(<Greeting name='hoho' />);

    screen.getByText('Hello, hoho');

    screen.getByText('Hello, hoho');

    expect(screen.queryByText(/Hi/)).not.toBeInTheDocument();
})
```
