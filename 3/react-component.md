# React Component

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





## 학습 키워드

* REST API 란 무엇인가?
* GraphQL 란 무엇인가?
* GraphQL은 왜 등장했는가?
* REST API vs GraphQL
* JSON
* DSL(Domain-Specific Language)
* 선언형 프로그래밍
* 명령형 프로그래밍
* SRP(단일 책임 원칙)
* Atomic Design
* React component 와 props
* React state란?
* DRY 원칙
* SSOT(Single Source of Truth)
* useState
* 1급 객체(first-class object)란?
* Lifting State Up

