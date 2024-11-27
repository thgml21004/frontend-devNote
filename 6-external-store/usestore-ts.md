# usestore-ts 사용

## usestore-ts

[usestore-ts](https://usestore-ts.com/)

### 세팅

1.  설치

    ```
    npm install usestore-ts
    ```
2.  `tsconfig.json` 주석 풀기

    ```
        "experimentalDecorators": true,
        "emitDecoratorMetadata": true,
    ```

### 코드

Store 작성.

```tsx
import { singleton } from 'tsyringe';

import { Store, Action } from 'usestore-ts';

@singleton()
@Store()
export default class CounterStore {
  count = 0;

  @Action()
  increase(step = 1) {
    this.count += step;
  }

  @Action()
  decrease() {
    this.count -= 1;
  }
}
```

커스텀 Hook 작성.

```tsx
import { container } from 'tsyringe';

import { useStore } from 'usestore-ts';

import CounterStore from '../stores/CounterStore';

export default function useCounterStore() {
  const store = container.resolve(CounterStore);
  return useStore(store);
}
```

비동기 함수에 `@Action`을 붙이면 다르게 작동할 수 있다는 점에 주의! 별도의 액션을 만들면 신경 쓸 부분이 줄어든다.

```tsx
@singleton()
@Store()
class PostStore {
  posts: Post[] = [];

  async fetchPosts() {
    this.startLoading();

    const posts = await fetchPosts();

    this.completeLoading(posts);
  }

  @Action()
  startLoading() {
    this.posts = [];
  }

  @Action()
  completeLoading(posts: Post[]) {
    this.posts = posts;
  }
}
```



[https://immerjs.github.io/immer/](https://immerjs.github.io/immer/) -> 강사님은 좋아하지 않음



[useSyncExternalStore](https://react.dev/reference/react/useSyncExternalStore)

[FECONF 2022 - 상태관리 이 전쟁을 끝내러 왔다](https://youtu.be/KEDUqA9JeIo)



왜 쓰는지 기억하고 써야한다. ⇒ **Separation of Concerns**

어떻게 하면 좋을 프로그램을 만들 수 있을지 고민하면서 공부하는게 좋다고 하심



`이해하고 써야 된다고 하는데 이해를 못해서 아직 못 쓸 것 같다..`
