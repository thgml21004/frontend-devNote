# React Testing Library

## React Testing Library

[React Testing Library](https://github.com/testing-library/react-testing-library)

[jest-dom](https://github.com/testing-library/jest-dom)

React 컴포넌트를 사용자 입장에 가깝게 테스트할 수 있는 도구.



## TextFiled 예시

### 테스트 코드

```jsx
import { render, screen } from '@testing-library/react';

import TextField from './TextField';

test('TextField', () => {
  const text = 'Tester';
  const setText = () => {
    // do nothing...
  };

  render((
    <TextField
      label="Name"
      placeholder="Input your name"
      text={text}
      setText={setText}
    />
  ));

  screen.getByLabelText('Name');
});
```

### TDD 스타일

```jsx
import { fireEvent, render, screen } from '@testing-library/react';
import TextField from './TextField';

const cntext = describe;

describe('TextField', () => {
  // given
  const label = 'Name';
  const text = 'Tester';

  const setText = jest.fn();

  beforeEach(() => {
    // 초기화
    setText.mockClear();
  });

  function renderTextField() {
    render((
      <TextField
        label={label}
        placeholder="Input your name"
        text={text}
        setText={setText}
      />
    ));
  }


  it('renders elements', () => {
    // when
    renderTextField();

    // then
    screen.getByLabelText(label);
  });

  // ------------------------------------

  // context : 입력했을 때
  cntext('when user enters name', () => {
    beforeEach(() => {
      // given
      renderTextField();
    });

    it('calls "setText" handler', () => {
      // when
      fireEvent.change(screen.getByLabelText('Name'), {
        target: {
          value: 'New Name',
        },
      });

      // then
      expect(setText).toBeCalledWith('New Name');
    });
  });
});
```

## 초기화

```
beforeEach(() => {
  // setText.mockClear(); => setText만 초기화
  
  // 전체 초기화
  jest.clearAllMocks();
});
```

## 컴파일 잘못된 곳 잡기

```
npx tsc --noEmit
```



`뭐야.. 이거 내가 들을 수 있는거 맞아? 아니... 와... 할말을 잃었다.. 왜 더 어려워지냐 ㅎ 멘탈 파사삭된다.. 학습할 의욕을 잃는다.. 뭐냐 뭔데..`&#x20;
