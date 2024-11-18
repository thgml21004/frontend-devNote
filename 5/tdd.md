# TDD

## TDD - 테스트 주도 개발

[테스트 주도 개발](https://megaptera.notion.site/01b100f1f70e4a97a4565d47f39b22d6?pvs=4)&#x20;

[TDD FAQ](https://megaptera.notion.site/TDD-FAQ-edcaa36e8cf246d9a2aa546d99810202?pvs=4)&#x20;

[Jest를 이용한 간단한 TDD 예제](https://megaptera.notion.site/Jest-TDD-4149c9f23b2d4402ad44d4d569a3ae13?pvs=4)

### TDD Cycle

테스트 코드 작성 -> 실패 -> 통과되도록 코드 작성 -> 중복 코드 제거 (리팩터링)

1. **Red** → 실패하는 테스트 코드를 작성. 인터페이스와 스펙에 집중한다.
2. **Green** → 재빨리 테스트를 통과시킨다. 올바른 방법이 아니어도 괜찮다.
3. **Refactor** → 리팩터링을 통해 코드를 올바르게 만든다. TDD에서 가장 중요한 부분이지만, 간과될 때가 많다.

## JEST

테스트 도구

[Jest](https://jestjs.io/)

[Given-When-Then](https://megaptera.notion.site/Given-When-Then-5b2e7e746be140a0a6e26e642b52c1e5?pvs=4)

1. test 함수로 개별 테스트를 나열하는 방식.
2. BDD 스타일로 주체-행위 중심으로 테스트를 조직화하는 방식.

### Jest에서 TypeScript 사용하도록 `jest.config.js` 파일 작성

```jsx
module.exports = {
  testEnvironment: 'jsdom',
  setupFilesAfterEnv: [
    '@testing-library/jest-dom/extend-expect',
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

### JEST 실행

```jsx
// 실행
npx jest

// 바로 확인하기
npx jest --watchAll -> 엔터
```

### 예시

1.  테스트 코드 작성

    ```jsx
    test('add 두 숫자를 더하는 함수', () => {
      expect(add(1, 2)).toBe(3); // => add(1, 2) === 3을 변환한거
    });
    ```
2.  실패 코드 작성

    ```jsx
    function add(x: number, y: number): number {
      return 0;
    }

    test('add 두 숫자를 더하는 함수', () => {
      expect(add(1, 2)).toBe(3); // => add(1, 2) === 3을 변환한거
    });
    ```
3.  통과 코드 작성

    ```jsx
    function add(x: number, y: number): number {
      return 1 + 2;
    }

    test('add 두 숫자를 더하는 함수', () => {
      expect(add(1, 2)).toBe(3); // => add(1, 2) === 3을 변환한거
    });
    ```
4.  중복 코드 제거

    ```jsx
    function add(x: number, y: number): number {
        return x + y;
    }

    test('add 두 숫자를 더하는 함수', () => {
      expect(add(1, 2)).toBe(3); // => add(1, 2) === 3을 변환한거
    });
    ```

### BDD 스타일 예시

```jsx
describe('add', () => {
  it('두 숫자의 합을 리턴', () => {
    expect(add(1, 2)).toBe(3);
  });
});
```

#### 코드 작성 순서 간략화

1.  코드 작성

    ```jsx
    function add(...numbers: number[]): number {
      if (numbers.length === 0) {
        return 0;
      }

      if (numbers.length === 1) {
        return numbers[0];
      }
      if (numbers.length === 2) {
        return numbers[0] + numbers[1];
      }
      if (numbers.length === 2) {
        return numbers[0] + numbers[1] + numbers[2];
      }
    }

    describe('add', () => {
      context('with no argument', () => {
        it('returns zero', () => {
          expect(add()).toBe(0);
        });
      });

      context('with only one number', () => {
        it('returns the same number', () => {
          expect(add(1)).toBe(1);
        });
      });

      context('with two numbers', () => {
        it('returns sum of two numbers', () => {
          expect(add(1, 2)).toBe(3);
        });
      });

      context('with three numbers', () => {
        it('returns sum of three numbers', () => {
          expect(add(1, 2, 3)).toBe(6);
        });
      });
    });

    ```
2.  간략하게

    ```jsx
    function add(...numbers: number[]): number {
      if (numbers.length === 0) {
        return 0;
      }

      return add(...numbers.slice(0, numbers.length - 1))
          + numbers[numbers.length - 1];
    }
    ```
3.  최종 간략화

    ```jsx
    function add(...numbers: number[]): number {
      if (numbers.length === 0) {
        return 0;
      }
      
      return numbers.reduce((acc, number) => acc + number);
    }
    ```

