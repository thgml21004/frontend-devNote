---
description: TypeScript
---

# TypeScript

*   TypeScript 실행

    ```
    npx ts-node
    ```



타입 지정

<pre><code><strong>
</strong><strong>// 타입 지정
</strong>let name: string;
let age: number;

// 잘된 예시
name = '홍길동';
age = 13;

// 잘못된 예시
name = 13;
age = '홍길동';

// 묶어서 타입 지정
let human: {
  name: string;
  age: number;
};

// 묶어서 데이터 값 입력
human = { name: '홍길동', age: 13 };

</code></pre>

*   타입 앨리어스\
    \=> 타입을 정의하여 사용

    ```

    type Human = {
      name: string;
      age: number;
    };

    let boy: Human;

    boy = { name: '홍길동', age: 13 };

    // 결과
    { name: '홍길동', age: 13 }


    let girl: Human;

    girl = { name: '꽃분이', age: 7 };

    // 결과
    { name: '꽃분이', age: 7 }

    ```
*   인터페이스

    ```

    interface Person {
      name: string;
      age: number;
    };

    let girl: Person;

    girl = { name: '영숙이', age: 7 };

    // 결과
    { name: '영숙이', age: 7 }


    ```
*   매개변수 / 리턴 값에도 타입 지정

    ```

    function add(x: number, y: number): number {
      return x + y;
    }

    add(1, 10)

    //결과
    11

    // 잘못된 타입 지정
    // 매개변수는 number인데 리턴값이 string 
    function sub(x: number, y: number): string {
      return x - y;
    }

    ```
*   정해진 값 타입 지정 (Union에서 쓰인다)

    ```
    let category: 'food';

    category = 'food';
    ```
*   배열

    ```

    let numbers: number[]

    numbers = [3,5,7]

    // 결과
    [ 3, 5, 7 ]

    ```
*   any

    ```

    let a : any;

    a = 1;

    // 결과
    1

    a = 'psh';

    //결과
    psh

    let anythings: any[];

    anythings = ['hp', 256];

    //결과
    ['hp', 256]

    anythings = ['hp', '256', 3];

    //결과
    ['hp', '256', 3]

    ```
*   Tuple : 배열보다 깐깐하게 관리

    ```

    let pair: [string, number];

    // 잘된 예시
    pair = ['hp', 256];

    // 잘못된 예시
    pair = ['hp', '256'];

    ```
*   타입 추론\
    타입을 지정하지 않아도 데이터 값으로 타입 확인 가능// 이렇게 타입을 지정하지 않아도

    ```

    const name: string = '홍길동';

    // 이렇게 쓴 것 만으로 name의 타입은 string 인 걸 알 수 있다.
    const name = '홍길동';

    ```
*   Union 타입 (합집합?)type a = true | false;

    ```

    let z: a;

    z = true;

    z = false;

    let y: true | false;

    y = true;
     
    y = false;

    ```
*   매개변수 제한

    ```

    type Category = 'food' | 'toy' | 'bag';

    function fetchProducts({ category }: { category: Category }) {
      console.log(`Fetch ${category}`);
    }

    // 잘된 예시
    fetchProducts({category:'food'}) 
    // 결과 Fetch food

    // 잘못된 예시
    fetchProducts({category:'desk'})

    ```
*   타입을 두개 설정

    ```

    let target: string | number;

    target = '홍길동';

    target = 13;


    // undefined를 출력하고 싶을 때

    let targetName: string | undefined;

    targetName = '홍길동';

    targetName = undefined;

    ```
*   타입 설정 후 데이터 하나만 입력해도 undefinedd 출력 되어 하나의 데이터도 나오게

    ```

    // 이것보다는 
    function add(x: number, y?: number | undefined) {
        return x + (y || 0);
    }

    // 이렇게 쓰는게 좋다.
    function add(x: number, y: number = 0) {
        return x + y;
    }

    add(2)

    //결과
    2

    add(3,5)

    //결과
    8

    ```
*   기본값을 잡아주면 더 좋음

    ```

    function greeting(name: string = 'world'): string {
      return `Hello, ${name}`;
    }

    greeting();

    //결과 
    'Hello, world'

    greeting('hi');

    //결과
    'Hello, hi'

    ```
*   합쳐 쓰기

    ```

    function greeting({ name, age }: { name: string; age?: number; }): string {
      return age ? `${name} (${age})` : name;
    }

    greeting({name: '홍길동', age: 15})

    //결과
    '홍길동 (15)'

    ```
*   타입 선정하여 쓰기

    ```

    type Human = {
      name: string;
      age?: number;
    };

    function greeting({ name, age }: Human): string {
      return age ? `${name} (${age})` : name;
    }

    // 잘못된 예시
    greeting()

    greeting({ name: '홍길동' })

    //결과
    '홍길동'

    greeting({ name: '홍길동', age: 13 })

    //결과
    '홍길동 (13)'

    ```
*   Intersection Type (교집합?)

    ```

    type Human = {
      name: string;
      age: number;
    };

    type Creature = {
      hp: number;
      mp: number;
    };

    type Person = Human & Creature;

    let person: Person;

    person = { name: '홍길동', age: 13, hp: 256, mp: 16 };

    ```



예시)

* 코드 안에서 작성&#x20;
  *   app.tsx

      ```
      export default function App({ name = 'psh' }: {
          name?: string
      }) {
          return (
              <p>Hellow, {name}</p>
          )
      }
      ```
  *   main.tsx

      ```
      import ReactDOM from "react-dom/client";
      import App from "./app";


      const element = document.getElementById("root");

      if (element) {
          const root = ReactDOM.createRoot(element);

          root.render(<App name='하하하' />);
      }

      ```
  * 결과\
    \<App />에 name 데이터를 넣었기 때문에 **Hellow, 하하하** 출력됨\
    \<App />에 name 데이터를 넣지 않으면 기본 데이터 **Hellow, psh** 출력됨
* 타입 지정
  *   app.tsx

      ```
      type AppProps = {
        name?: string;
      }

      export default function App({ name = 'psh' }: AppProps) {
          return (
              <p>Hellow, {name}</p>
          )
      }
      ```
  *   main.tsx

      ```
      import ReactDOM from "react-dom/client";
      import App from "./app";


      const element = document.getElementById("root");

      if (element) {
          const root = ReactDOM.createRoot(element);

          root.render(<App name='하하하' />);
      }
      ```
  * 결과\
    \<App />에 name 데이터를 넣었기 때문에 **Hellow, 하하하** 출력됨\
    \<App />에 name 데이터를 넣지 않으면 기본 데이터 **Hellow, psh** 출력됨
