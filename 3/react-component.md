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





## 학습 키워드

* REST API 란 무엇인가?
  * 정의
    * REST 기반으로 서비스 API를 구현한 것
    * 클라이언트와 서버 간의 두 컴퓨터 시스템이 인터넷을 통해 정보를 안전하게 교환하기 위해 사용하는 인터페이스
    * 웹 서비스가 어떻게 동작해야 하는지에 대한 아키텍쳐 스타일 또는 설계 원칙
  * 설계규칙
    * 명사를 사용 / 동사는 사용하지 않는다.
    * 소문자 사용
    * 하이픈(-)은 가독성 높이는데 사용
    * 밑줄(\_)은 사용하지 않는다.
    * 파일 확장자 적지 않기
  * 장점
    * HTTP 프로토콜을 사용함으로 웹 브라우저 호환 용이
    * 독립적이고 확장성이 높다.
    * 자원 기반으로 URL 직관적이고 구조화
  * 단점
    * 상태가 없는 프로토콜이므로 매 요청마다 인증 정보 필요
    * 복잡한 작업을 다루기엔 적합하지 않음
  * 특징
    * 다양한 서비스에 많이 사용되고 있어 다른 시스템 간의 상호 작용을 위한 효율적인 방법 제공
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

