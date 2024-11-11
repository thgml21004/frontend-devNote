# React State

## React State

### 정의

* React의 state는 **변경**
* 컴포넌트의 state가 변경되면 해당 컴포넌트와 하위 컴포넌트를 다시 랜더링

### 일관성 & 효율성

* [DRY (Don’t Repeat Yourself)](https://ko.wikipedia.org/wiki/%EC%A4%91%EB%B3%B5%EB%B0%B0%EC%A0%9C) : 중복 배제
* [SSOT (Single Source of Truth)](https://ko.wikipedia.org/wiki/%EB%8B%A8%EC%9D%BC\_%EC%A7%84%EC%8B%A4\_%EA%B3%B5%EA%B8%89%EC%9B%90) : 단일 진실 공급원

### React State의 조건

* 변경돼야 함. 변경되지 않는 건 state로 다룰 가치가 없다.
* 부모 컴포넌트가 props를 통해 전달한다면 state가 아님.
* 다른 state나 props를 이용해 계산 가능하다면 state가 아님.

### 최상위 컴포넌트가 state를 가지고 있는다.

### Lifting State Up

* [Lifting State Up](https://ko.legacy.reactjs.org/docs/lifting-state-up.html) : state 끌어올리기
* 동일한 데이터에 대한 변경사항을 여러 컴포넌트에 반영해야 할 필요가 있다 이럴 때는 가장 가까운 공통 조상으로 state를 끌어올리는 것

### Sharing State Between Components

* [Sharing State Between Components](https://ko.react.dev/learn/sharing-state-between-components) : 컴포넌트 강의 state 공유
* 두 컴포넌트의 state가 항상 함께 변경되기를 원할 수 있다 그렇게 하려면 각 컴포넌트에서 state를 제거하고 가장 가까운 공통 부모 컴포넌트로 옮긴 후 props로 전달

## Inverse Data Flow

하위 컴포넌트의 props로 함수를 전달. 흔히 콜백 함수라고 부름.

### 일급함수

[일급 함수](https://developer.mozilla.org/ko/docs/Glossary/First-class\_Function)

* 어떤 함수를 다른 함수에 인자로 넘겨주거나, 어떤 함수를 리턴값으로 사용할 수 있다



#### Effect 이렇게 쓰지 말기&#x20;

```
function Form() {
  const [firstName, setFirstName] = useState('Taylor');
  const [lastName, setLastName] = useState('Swift');

  // 🔴 Avoid: redundant state and unnecessary Effect
  const [fullName, setFullName] = useState('');
  useEffect(() => {
    setFullName(firstName + ' ' + lastName);
  }, [firstName, lastName]);
  // ...
}
```

#### toggle 버튼은 이렇게 작성 (!)

```
const toggleDarkMode = () => {
    setIsDarkMode(!prevMode);
};
```



`이번 강의는 각각 3번을 들었다 처음은 어떤 수업인지 시청만 두번째는 실습을하기 위해서 세번째는 과제를 하기 위해 더 정확한 학습을 위해서 실습을 따라하면서 여전히 utils 폴더를 왜 만드는지 이해하지 못했고 세번째 들으면서 다른 곳에서도 쓰일 수 있으니 함수를 utils에 뺀거라고 이해했다. 근데 그 과정이 너무  어려워서 내가 따로 빼서 하지는 못할 것 같다.`
