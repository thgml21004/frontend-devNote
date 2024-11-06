# React Component

`1회차 강의 시청 후 코드 강의를 하면 나한테 유익한 수업이 되고 내가 이거를 따라서 실습하면은 이해할 수 있을거라고 생각했다.. (오산이다..ㅎ) 따라하다가 손을 놓게 되었다.. 강의 내용을 그냥 듣기만했다.`&#x20;

## 데이터

B/E에서 JSON 형태의 데이터를 돌려주는 API를 제공한다고 가정(대부분은 REST API 또는 GraphQL).

### **Rest API**

* GET, POST, PUT/PATCH, DELETE (CRUD)
* Resource 중심

### GraphQL

* Graph 자료 구조
* 쿼리에서 얻고자 한는 걸 지정
*  쿼리(읽기), Mutation( Commend:  생성, 업데이트, 삭제), Subscription(Event)

### Json API

```
[
  { category: "Fruits", price: "$1", stocked: true, name: "Apple" },
  { category: "Fruits", price: "$1", stocked: true, name: "Dragonfruit" },
  { category: "Fruits", price: "$2", stocked: false, name: "Passionfruit" },
  { category: "Vegetables", price: "$2", stocked: true, name: "Spinach" },
  { category: "Vegetables", price: "$4", stocked: false, name: "Pumpkin" },
  { category: "Vegetables", price: "$1", stocked: true, name: "Peas" }
]
```



## 컴포넌트 계층 구조

간단한 컴포넌트를 모아서 복잡한 UI를 만든다.\
복잡한 컴포넌트를 만들고 있으면 리액트를 제대로 활용하지 못하고 있다고 생각하기

### 간단한 컴포넌트 기준

* 단일 책임 원칙
*  css를 예를 들어서 class를 작성 시 컨텐츠 박스로 작성하고 있기 때문에 이미 컴포넌트를 쪼개는 작업을 하고 있다.
* 디자인 레이아웃
* Information Architecture (JSON Schema의 영향) -> 실제로 많이 씀

### Atomic Design

계층 구조로 만들면 어떤 것인지 모르기 때문에 그걸 카테고리로 묶는 방법





## react 코드 기록

### acc.includes?(product.category) ? add : \[...acc, product.category]

```jsx
const categories = products.reduce((acc, product) => (
    acc.includes(product.category) ? acc : [...acc, product.category]
), []);
```

`reduce` 메서드를 사용하여 `products` 배열에 있는 `product.category` 값들을 고유하게 추출하려는 것

포함되어 있으면 `add`를 반환하고, 그렇지 않으면 `acc` 배열에 `product.category`를 추가한 새로운 배열을 반환합니다.

#### 설명:

1. `reduce` 함수는 누적값(`acc`)과 현재 항목(`product`)을 인수로 받습니다.
2. `acc.includes(product.category)`는 `acc` 배열에 `product.category`가 포함되어 있는지 확인합니다.
3. 포함되어 있다면 `acc`를 그대로 반환하고, 포함되어 있지 않다면 `[...acc, product.category]`로 `product.category`를 추가한 새로운 배열을 반환합니다.
4. 최종적으로 `categories`는 `products` 배열에서 중복 없이 카테고리만 모아진 배열이 됩니다.

### utils 폴더 생성

'컴포넌트 나누는 기준이 애매하면 다시 하나의 컴포넌트로 합쳤다가(Inline Method) 다시 나눠줘도 됨.'의 예시?

강의 58:39 강의 시청





`2회차 강의 시청.. 컴포넌트 조금 이해하다가 중간에 utils 나오면서 모르겠다... types는 대략? 이해했는데 utils는 아직 인해가 안갔다.. utils를 다른 방식으로 코딩하면서 컴포넌트를 쪼개는 방법이 다양하다고 하는데 아직 배우는 입장에서는 그게 오히려 문제인것 같다 너무 다양해서 이해하는게 어렵다. 이해하게 된다면 유용하게 쓸 수 있을 것 같다. 아마도..?`
