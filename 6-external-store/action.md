# Action을 메소드로 처리하기

```tsx
type Listener = () => void;

export default class ObjectStore {
  private listeners = new Set<Listener>();

  addListener(listener: Listener) {
    this.listeners.add(listener);
  }

  removeListener(listener: Listener) {
    this.listeners.delete(listener);
  }

  protected publish() {
    this.listeners.forEach((listener) => listener());
  }
}
```

`src/stores/CounterStore.ts` 파일

```tsx
import { singleton } from 'tsyringe';

import ObjectStore from './ObjectStore';

@singleton()
export default class CounterStore extends ObjectStore {
  count = 0;

  increase(step = 1) {
    this.count += step;
    this.publish();
  }

  decrease() {
    this.count -= 1;
    this.publish();
  }
}
```

`src/hooks/useObjectStore.ts` 파일

```tsx
import { useEffect } from 'react';

import useForceUpdate from './useForceUpdate';

import ObjectStore from '../stores/ObjectStore';

export default function useObjectStore<T extends ObjectStore>(store: T) {
  const forceUpdate = useForceUpdate();

  useEffect(() => {
    store.addListener(forceUpdate);
    return () => store.removeListener(forceUpdate);
  }, [store]);

  return store;
}
```

`src/hooks/useCounterStore.ts` 파일

```tsx
import { container } from 'tsyringe';

import useObjectStore from './useObjectStore';

import CounterStore from '../stores/CounterStore';

export default function useCounterStore() {
  const store = container.resolve(CounterStore);

  return useObjectStore(store);
}
```

`여기도 다 코드 따라하기군..`
