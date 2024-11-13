# usehooks-ts

## usehooks-ts

[usehooks-ts](https://usehooks-ts.com/)

### 설치

```
npm i usehooks-ts
```

## useBoolean

[useBoolean](https://usehooks-ts.com/react-hook/use-boolean)

참/거짓을 다룰 땐 toggle 같이 의도가 명확한 함수를 쓰는 게 좋다.

### 예시

#### const { value, toggle } = useBoolean();

변경 전

```jsx
export default function TimerControl() {
  const [playing, setPlaying] = useState(false);
  ...
```

변경 후

```jsx
import { useBoolean } from 'usehooks-ts';

export default function TimerControl() {
  const [playing, setPlaying] = useState(false);
  const { value: playing, toggle: togglePlaying } = useBoolean();
  
  const handleClick = () => {
    togglePlaying();
  };
  ...
```

## useCounter

[useCounter](https://usehooks-ts.com/react-hook/use-counter)

### 예시

#### const { count, increment } = useCounter(0);

변경 전

```jsx
const [count, setCount] = useState(0);
...
<p>{count}</p>
<button type="button" onClick={() => setCount(count + 1)}>Increase</button>
```

변경 후

```jsx
const { count, increment } = useCounter(0);
...
<p>{count}</p>
<button type="button" onClick={increment}>Increase</button>
```

## useEffectOnce

[useEffectOnce](https://usehooks-ts.com/react-hook/use-effect-once)

의존성 배열을 빈 배열로 넣어서 한 번만 실행하는 Effect를 잡아줄 때가 많은데, 이걸 쓰면 더 명확히 드러난다.

### 예시

변경 전

```jsx
import { useEffect, useState } from 'react';

export default function useFetchProducts() {

  useEffect(() => {
    ...
  }, []);
  return products;
}
```

변경 후

```jsx
import { useEffectOnce } from 'usehooks-ts';

export default function useFetchProducts() {

  useEffectOnce(() => {
    ...
  });
  return products;
}
```

`뭐지? usehooks-ts에 들어가면 useEffectOnce가 없다.. 그래서 useEffectOnce를 찾을 수 없다는 에러 메시지 나옴 ㅎ 아 이거때문에 코드 계속 저거 없다고 에러나면서 화면 npm run 안된다 분명 지웠는데 하.. 시간차가 있네..ㅎ`

## useFetch

[useFetch](https://usehooks-ts.com/react-hook/use-fetch)

```jsx
import { useFetch } from 'usehooks-ts';

export default function useFetchProducts() {
  const url = 'http://localhost:3000/products';
  const { data } = useFetch(url);
  if (!data) {
    return [];
  }
  return data.products;
}
```

`얘도 없는 듯..`

## useInterval

[useInterval](https://usehooks-ts.com/react-hook/use-interval)

React에서 setInterval 등을 쓸 때는 주의해야 할 부분이 있어서 **Custom Hook**을 만들어서 해결해야 함.

## useEventListener

[useEventListener](https://usehooks-ts.com/react-hook/use-event-listener)

모든 종류의 이벤트를 확인할 수 있음. 특히 dispatchEvent로 전달되는 커스텀 이벤트에 반응하기 좋다. (강력 추천!)

## useLocalStorage

[useLocalStorage](https://usehooks-ts.com/react-hook/use-local-storage)

이벤트를 통해(dispatchEvent + useEventListener) 다른 컴포넌트와 동기화하는 게 매우 중요한 특징.

## useDarkMode

[useDarkMode](https://usehooks-ts.com/react-hook/use-dark-mode)



useWindowSize, useElementSize 등등 다양하게 사용할 수 있다.









