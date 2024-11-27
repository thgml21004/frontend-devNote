# TSyringe

## TSyringe

[TSyringe](https://github.com/microsoft/tsyringe)&#x20;

[reflect-metadata](https://github.com/rbuckton/reflect-metadata)

[Props 전달하기의 문제점](https://react.dev/learn/passing-data-deeply-with-context#the-problem-with-passing-props)

### 설치

```bash
npm i tsyringe reflect-metadata
```

### 싱글톤(singleton)

```jsx
import { singleton } from 'tsyringe';

@singleton()
export default class Store {
  count = 0;
}
```

```jsx
import { container } from 'tsyringe';

import useForceUpdate from '../hooks/useForceUpdate';

import Store from '../stores/stores';

export default function Counter() {
  const store = container.resolve(Store);

  const forceUpdate = useForceUpdate();

  const handleClick = () => {
    store.count += 1;
    forceUpdate();
  };
  return (
    <div>
      <p>{store.count}</p>
      <button type="button" onClick={handleClick}>클릭</button>
    </div>
  );
}
```

1.  `src/main.tsx` 파일과 `src/setupTests.ts` 파일에서 reflect-metadata 임포트.

    ```
    import 'reflect-metadata';
    ```
2.  tsconfig.json 주석 풀기

    ```
    "experimentalDecorators": true,
    "emitDecoratorMetadata": true,
    ```

