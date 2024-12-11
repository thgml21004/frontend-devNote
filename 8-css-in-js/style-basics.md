# Style Basics

## Basic: Class

[스타일링과 CSS](https://ko.reactjs.org/docs/faq-styling.html)

예제

`index.html` 파일에 간단히 CSS 추가.

```tsx
<style>
  .greeting {
    color: #00F;
  }
</style>
```

“className” 지정.

```tsx
export default function Greeting() {
  return (
    <p className="greeting">
      Hello, world!
    </p>
  );
}
```

## Basic: Inline Style

“style” 속성 활용. 평범한 JavaScript 객체를 활용하므로 변수, 함수 등을 재사용하기 쉽다. \
텍스트가 아니라서 실수하거나 불편할 때가 있다. \
TypeScript의 힘으로 자동완성, 타입 검사 등의 도움을 받을 수 있다.

```jsx
export default function Greeting() {
  const style = {
    color: '#00F',
  };

  return (
    <p style={style}>
      Hello, world!
    </p>
  );
}
```

```jsx
export default function Greeting() {
  return (
    <p
      style={{
        color: '#00F',
      }}
    >
      Hello, world!
    </p>
  );
}
```

### 예시

```jsx
export default function Greating() {
  const darkMode = false;

  function defaultColor() {
    return darkMode ? 'pink' : 'orange';
  }
  const style = {
    color: '#00F',
  };
  const PrimaryColor = 'red';
  return (
    <div>
      <p style={style}>
        Hello, world!
      </p>
      <p style={{
        color: 'skyblue',
      }}
      >
        Hello, world!
      </p>
      <p style={{ color: PrimaryColor }}>
        Hello, world!
      </p>
      <p style={{ color: defaultColor() }}>
        Hello, world!
      </p>
    </div>
  );
}

```
