# useRef & Custom Hook

## useRef

### 참고문서

* [beta 문서의 useRef (현재의 공식 문서)](https://ko.react.dev/reference/react/useRef)&#x20;
* [공식 문서의 useRef (예전의 공식 문서)](https://ko.legacy.reactjs.org/docs/hooks-reference.html#useref)

### 정의

* 객체 자체가 값은 아님, 값을 참조하기 위한 객체
* 어떠한 값을 유지하고 싶을 때
* 공통으로 쓰이는 컴포넌트들 중에서 하나의 컴포넌트에서만 값이 변경 되고 싶을 때
* 화면 렌더링할 때만 반영 됨

### 주요 용도

1. 컴포넌트가 사라질 때까지 동일한 값을 써야 하는 경우. ⇒ input 등의 ID 관리.
2. (특히 useEffect 등과 함께 쓰면서 만나게 되는) 비동기 상황에서 현재 값을 제대로 쓰고 싶은 경우.



## Custom Hook

로직을 재사용하기 쉬움

### Hook의 규칙

[Hook의 규칙](https://ko.legacy.reactjs.org/docs/hooks-rules.html)



`프론트엔드? 아님 리액트?는 컴포넌트 코드만 있어야 되나보다.. 모든 복잡해 보이는걸 숨기는게 그게 포인트인듯.. 그럴 숨기기위해서 utils, types, hooks 다양하게 숨기네.. util은 함수고 hook도 함수인것 같은데 흠.. 차이점이 뭔지 모르겠다 처음엔 hook은 사용자 데이터 불러는 함수들만 인줄 알았는데 강의 내용은 아닌 것 같기도 하고 보여주려고 하는건가..? 흠.. 이 차이점은 더 들어보고 찾아봐야겠다.`
