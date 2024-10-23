---
description: TypeScript
---

# TypeScript

## 참고 사이트

* [TypeScript 공식문서](https://www.typescriptlang.org/ko/)
* [TypeScript for the New Programmer](https://www.typescriptlang.org/ko/docs/handbook/typescript-from-scratch.html)
* [TypeScript for JavaScript Programmers](https://www.typescriptlang.org/ko/docs/handbook/typescript-in-5-minutes.html)



## 터미널 ts-node 실행

간단히 REPL을 쓰고 싶다면 ts-node를 실행하면 된다.

*   TypeScript 실행

    ```
    npx ts-node
    ```



## 타입 지정

### 참고 사이트

* [타입 정의하기 (Defining Types)](https://www.typescriptlang.org/ko/docs/handbook/typescript-in-5-minutes.html#%ED%83%80%EC%9E%85-%EC%A0%95%EC%9D%98%ED%95%98%EA%B8%B0-defining-types)
* [타입 별칭과 인터페이스의 차이점](https://www.typescriptlang.org/ko/docs/handbook/2/everyday-types.html#%ED%83%80%EC%9E%85-%EB%B3%84%EC%B9%AD%EA%B3%BC-%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90)

### 예시1. 기본

<pre class="language-typescript"><code class="lang-typescript"><strong>
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

### 예시2. 타입 앨리어스

타입을 정의하여 사용

```typescript

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

### 예시3. 인터페이스

```typescript

interface Person {
  name: string;
  age: number;
};

let girl: Person;

girl = { name: '영숙이', age: 7 };

// 결과
{ name: '영숙이', age: 7 }


```

### 예시4. 매개변수 / 리턴 값에도 타입 지정

```typescript

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

### 예시5. 정해진 값 타입 지정 (Union에서 쓰인다)

```typescript
let category: 'food';

category = 'food';
```

### 예시6. 배열

```typescript

let numbers: number[]

numbers = [3,5,7]

// 결과
[ 3, 5, 7 ]

```

### 예시7. any

```typescript

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

### 예시8. Tuple : 배열보다 깐깐하게 관리

```typescript

let pair: [string, number];

// 잘된 예시
pair = ['hp', 256];

// 잘못된 예시
pair = ['hp', '256'];

```

## 타입 추론

[타입 추론](https://www.typescriptlang.org/ko/docs/handbook/typescript-in-5-minutes.html#%ED%83%80%EC%9E%85-%EC%B6%94%EB%A1%A0-types-by-inference)

타입을 지정하지 않아도 데이터 값으로 타입 확인 가능

```typescript

const name: string = '홍길동';

// 이렇게 쓴 것 만으로 name의 타입은 string 인 걸 알 수 있다.
const name = '홍길동';

```

## Union 타입&#x20;

[Union Type](https://www.typescriptlang.org/ko/docs/handbook/typescript-in-5-minutes.html#%EC%9C%A0%EB%8B%88%EC%96%B8-unions)

합집합?&#x20;

type a = true | false;

```typescript

let z: a;

z = true;

z = false;

let y: true | false;

y = true;
 
y = false;

```

### 예시1. 매개변수 제한

```typescript

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

### 예시3. 타입을 두개 설정

[React Types](https://github.com/facebook/react/blob/main/packages/shared/ReactTypes.js)

```typescript

let target: string | number;

target = '홍길동';

target = 13;


// undefined를 출력하고 싶을 때

let targetName: string | undefined;

targetName = '홍길동';

targetName = undefined;

```

*   타입 설정 후 데이터 하나만 입력해도 undefinedd 출력 되어 하나의 데이터도 나오게

    ```typescript

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
*   기본값을 잡아주면 더 좋음 [Optional Parameter](https://www.typescriptlang.org/docs/handbook/2/functions.html#optional-parameters)

    ```typescript

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

    ```typescript

    function greeting({ name, age }: { name: string; age?: number; }): string {
      return age ? `${name} (${age})` : name;
    }

    greeting({name: '홍길동', age: 15})

    //결과
    '홍길동 (15)'

    ```
*   타입 선정하여 쓰기

    ```typescript

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

## Intersection Type (교집합?)

### 참고 사이트

* [교집합](https://www.typescriptlang.org/ko/docs/handbook/typescript-in-5-minutes-func.html#%EA%B5%90%EC%A7%91%ED%95%A9)
* [Intersection Types](https://www.typescriptlang.org/docs/handbook/2/objects.html#intersection-types)

### 예시 1. 기본

```typescript

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



## 화면에 적용하기

### 코드 안에서 작성&#x20;

*   app.tsx

    ```typescript
    export default function App({ name = 'psh' }: {
        name?: string
    }) {
        return (
            <p>Hellow, {name}</p>
        )
    }
    ```
*   main.tsx

    ```typescript
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

### 타입 지정

*   app.tsx

    ```typescript
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

    ```typescript
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
