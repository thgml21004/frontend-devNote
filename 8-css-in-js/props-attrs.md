# props 와 attrs

## props

[Passed props](https://styled-components.com/docs/basics#passed-props)

### 함수

```jsx
import styled from 'styled-components';
import { useBoolean } from 'usehooks-ts';

type ButtonProps = {
  active: boolean;
}

function background(props: ButtonProps) {
  return props.active ? '#f00' : '#000';
}

const Button = styled.button<ButtonProps>`
    background: ${background};
    color: #fff;
`;

export default function Switch() {
  const { value: active, toggle } = useBoolean(false);

  return (
    <>
      <Button type="button" onClick={toggle} active={active}>
        on/off
      </Button>
    </>
  );
}
```

### style

```jsx
import styled from 'styled-components';
import { useBoolean } from 'usehooks-ts';

type ButtonProps = {
  active: boolean;
}

const Buttons = styled.button<ButtonProps>`
  background: ${(props) => (props.active ? 'green' : 'orange')};
`;

export default function Switch() {
  const { value: active, toggle } = useBoolean(false);

  return (
    <>
      <Buttons type="button" onClick={toggle} active={active}>
        on/off
      </Buttons>
    </>
  );
}
```

### props

```jsx
import styled, { css } from 'styled-components';
import { useBoolean } from 'usehooks-ts';

type ButtonProps = {
  active: boolean;
}

const Buttons = styled.button<ButtonProps>`
  background: ${(props) => (props.active ? 'green' : 'orange')};
  ${(props) => props.active && css`
    font-size: 2rem;
  `}
`;

export default function Switch() {
  const { value: active, toggle } = useBoolean(false);

  return (
    <>
      <Buttons type="button" onClick={toggle} active={active}>
        on/off
      </Buttons>
    </>
  );
}
```

## attrs

[Attaching additional props](https://styled-components.com/docs/basics#attaching-additional-props)

기본 속성을 추가할 수 있음. 불필요하게 반복되는 속성을 처리할 때 유용한데, 버튼 등을 만들 때 적극 활용함.

```tsx
import styled from 'styled-components';

const Button = styled.button.attrs({
  type: 'button',
})`
  border: 1px solid #888;
  background: transparent;
  cursor: pointer;
`;

export default Button;
```
