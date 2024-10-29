# JSX

## 선 강의 후..

JSX를 한주동안 공부를 해야하는지 이해되지 않았다. \
그리고 강의의 설명이 이해되지가 않으니 귀에도 머리에도 남지 않는 내용이었다.\
검색을 해봤지만 다들 HTML 구조와 비슷하다고 하고 JavaScript의 확장 문법이라고만 설명을 해서 리액트에서 쓰는\
태그 문법을 설명해 주는건가? 뭘 설명하기 위한거지? JSX를 이해하게 되면 컴포넌트를 왜 그렇게 쪼개서 쓰는지 알 수 있다고 하는건지 이해가 되 않았다.&#x20;

***



## JSX

* HTML 구조를 작성할 수 있도록 만들어진 JavaScript 확장 문법
* HTML 코딩과 비슷하지만 다른 문법

### 특징

*   하나의 부모 태그로 작성된 구조

    ```
    # 옳은 방식
    export default function App() {
        return (
            <div>
                /* 자식 태그  */
            </div>
        )
    }

    # 잘못된 방식
    export default function App() {
        return (
            <div>
                /* 자식 태그  */
            </div>
            <p></p>
        )
    }
    ```
*   닫는 태그가 있어야 한다.

    ```
    # 잘못된 방식
    <br>

    # 옳은 방식
    <br />
    ```
*   class 속성은 className으로 작성

    ```
    # class라고 작성해도 오류가 나지 않지만 className으로 작성
    <div className="container">
      test
    </div>
    ```
*   style 속성 객체 형태로 작성

    ```
    <div style={{ color: 'red', fontSize : '16px' }}>
      test
    </div>
    ```
*   변수 대입 가능

    ```
    export default function App() {
        const name = 'test'
        return (
            <div>
                { name }
            </div>
        )
    }
    ```



## JSX -> JS 변환

변환기 : [Babel](https://babeljs.io/repl)

* JSX는 XML처럼 작성된 부분을 React.createElement을 쓰는 JavaScript 코드로 변환

### 예제 1.

```xml
# JSX 문법
<p>Hello, world!</p>

# 변환된 JS 문법
# null : 태그 속성
React.createElement("p", null, "Hello, world!");
```

### 예제 2.&#x20;

```
# JSX 문법
<Greeting name="world" />

# 변환된 JS 문법
React.createElement(Greeting, {
  name: "world"
});
```

### 예제 3.

```
# JSX 문법
<Button type="submit">Send</Button>

# 변환된 JS 문법
React.createElement(Button, {
  type: "submit"
}, "Send");
```

### 예제 4.

```
# JSX 문법
<div className="test">
  <p>Hello, world!</p>
  <Button type="submit">Send</Button>
</div>

# 변환된 JS 문법
React.createElement("div", {
  className: "test"
}, 
React.createElement("p", null, "Hello, world!"), 
React.createElement(Button, {
  type: "submit"
}, "Send"));
```

### 예제 5.

```
# JSX 문법
<div>
  <p>Count: {count}!</p>
  <button type="button" onClick={() => setCount(count + 1)}>Increase</button>
</div>

# 변환된 JS 문법
React.createElement("div", null, 
  React.createElement("p", null, "Count: ", count, "!"), 
  React.createElement("button", {
    type: "button",
  onClick: () => setCount(count + 1)
}, "Increase"));
```

`왜 굳이 jsx에서 js로 변환하는 걸까? 이로 인해 jsx 문법에 대해서 이해할 수 있는건가? 그러기에는 더 헷갈린다..`

## React Element

* 일반 객체이며 쉽게 생성
* 리액트 Virtual DOM에 존재하는 Element
* 자바스크립트 객체 형태로 존재
* `type`과 `props`를 가지는 React의 객체
* JSX 없이 사용하는 React
* 빌드 환경에서 컴파일 설정을 하고싶지 않을 때 사용
* 순수 자바스크리트로 작성 가능

```
const element = <h1>Hello, world</h1>;
```

## createElement

React Element 객체를 만드는 역할

```
# 태그 만들기
document.createElement('div');
=> <div></div>

# 클래스 넣기
const element = document.createElement('div');
element.className = 'test'
=> <div class="test"></div>

React.createElement(
    'div',
    { className: 'name' },
    'React'
)

{
  type: 'div',
  props: {    
      className: 'name',    
      children: 'React'  
  }
}
```

\=> JSX 대신 React.createElement를 써서 React Element 트리를 갱신하는데 쓴다

`두번이나 들었는데도 이해가 안된다`\
`내가 이해한 바로는 JSX를 쓰지 않고 순수 자바스크립트로 작성하려면 React.createElement를 써야 되고 이거를 작성하여 완성된 문법이 React Element인가..?`

`` `React Element 와 React.createElement를 두번째 강의 후 검색해 보았다 여전히 알 수가 없다. 어쨌든 자바스크릭트로 할 수 있는것 같은데... 흠..` ``

`프론튼 개발자가 이런걸 알고 있어야 되는건가? 이해가 가지도 않아서 학습하기 어렵다 왜 다 설명하시다가 조금 있다가 설명하시겠다고 하는지.. 뭔가 더 정리안되고 귀에 안들어 온다.`

## VDOM (Virtual DOM)

* 가상의 DOM을 만들어서 사용한다.
* ReactDOM과 같은 라이브러리에 의해 실제 DOM과 동기화
* DOM으로 하는 것보다 VDOM으로 하는게 비용이 적고, 훨씬 빠르게 화면을 그려줌
* 유지보수가 가능
* 선언적 API 가능

```
=> <div class="test"></div>
```

## Strict Mode

* 애플리케이션 내의 잠재적인 문제를 알아내기 위한 도구
* `Fragment`와 같이 UI를 렌더링하지 않으며, 자손들에 대한 부가적인 검사와 경고를 활성화

```
# Header, Footer 컴포넌트는 검사가 이루어지지 않음
# App, Main 컴포넌트는 각각의 자손까지 검자 함

root.render((
  <div>
    <Header />
    <StrictMode>
      <App />
      <Main />
    </StrictMode>
    <Footer />
  </div>
));
```

### 특징

* 안전하지 않은 생명주기를 사용하는 컴포넌트 발견
* 레거시 문자열 ref 사용에 대한 경고
* 권장되지 않는 findDOMNode 사용에 대한 경고
* 예상치 못한 부작용 검사
* 레거시 context API 검사
* Ensuring reusable state

## 학습 키워드

* React에서 JSX를 사용하는 목적
*   Syntactic sugar

    ```
    읽는 사람 또는 작성하는 사람이 편하게 디자인 된 문법이라는 뜻
    직관적이고 간결한 문법
    번거롭게 작성해야 했던 코드가 짧아진 덕분에 가독성이 좋아짐
    ```
*   React.createElement

    ```
    순수 자바스크립트로 작성 된 React
    ```
*   React Element

    ```
    DOM Element의 가상 표현
    ```
*   React StrictMode

    ```
    애플리케이션 내의 잠재적인 문제를 알아내기 위한 도구
    자손들에 대한 부가적인 검사와 경고를 활성화
    ```
*   VDOM(Virtual DOM)이란?

    ```
    가상의 DOM
    실제 DOM의 복사본 (DOM의 element, 속성 공유)
    ```
*   DOM이란?

    ```
    Element(HTML)들을 담고 있는 웹페이즈를 Doment라고 하는데, 
    이를 브라우저에서 분석해서 페이지를 띄워주는 방식
    ```
*   DOM과 Virtual DOM의 차이

    ```
    # DOM
    트리 구조안의 element에 접근해 원하는 대로 내용, 스타일, 레이아웃 등을 수정 가능
    트리에 있는 정보를 업데이트 시켜주고 이를 반복적으로 사용함으로 써 무거워짐

    # VDOM
    화면에 보여지는 내용을 직접 수정할 수 없다.
    화면 UI를 조작할 수 없음으로 매우 가볍고 빠른 작업 가능
    유지보수가 가능
    ```
*   Reconciliation(재조정) 과정은 무엇인가?

    ```
    렌더링 이전에 화면의 내용을 담고있는 첫번째 갓상돔과 업데이트 이후에 발생할 두번째 가상돔을 비교해 정확히
    어떤 Element가 변했는지 비교 후 차이가 발생한 부분만 실제 DOM에 적용

    ex) 10개의 항목이 수정되었을 때 실제로 DOM을 10번 수정하는 것이 아닌,한번에 실제 DOM에 적용하는 방식
    ```



`2주차 평 : 진짜 뭔소린지 모르겠다.. 수업을 진행해야되니깐 일단 열심히 찾아보고 하긴 했지만 진짜 뭔소린지 모르겠다..별거 아닌 내용이 절대 아닌듯.. 진짜로 알필요는 없지만 아직 내가 리액트에 대한 이해가 안되서 그런가 오늘의 강의는 더 어려웠음.. ㅎ 모르겠으면 VDOM으로 다시 학습하라는데 몇번을 봐도 제자리 ㅎㅎㅎ`
