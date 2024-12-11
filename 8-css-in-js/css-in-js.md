# CSS in JS

[CSS in JS](https://en.wikipedia.org/wiki/CSS-in-JS)

[React: CSS in JS (2014)](https://blog.vjeux.com/2014/javascript/react-css-in-js-nationjs.html)

1. Global Namespace
2. Dependencies
3. Dead Code Elimination
4. Minification
5. Sharing Constants
6. Non-deterministic Resolution
7. Isolation

[A Unified Styling Language (2017)](https://megaptera.notion.site/1bda981f17224c058b612598d4323c63?pvs=4)

1. Scoped styles
2. Critical CSS
3. Smarter optimisations
4. Package management
5. Non-browser styling

[All You Need To Know About CSS-in-JS (2017)](https://megaptera.notion.site/CSS-in-JS-d5904960ac564b0c8cdf5aa3bc2df5da?pvs=4)

1. Thinking in components
2. CSS-in-JS **leverages the full power of the JavaScript ecosystem** to enhance CSS.
3. True rules isolation
4. Scoped selectors
5. Vendor Prefixing
6. Code sharing
7. **Only the styles which are currently** in use on your screen are also in the DOM (react-jss).
8. Dead code elimination
9. Unit tests for CSS

[Most popular CSS-in-JS libraries](https://npmtrends.com/aphrodite-vs-emotion-vs-glamorous-vs-jss-vs-radium-vs-styled-components-vs-styletron)

→ 2023년 1월 기준으로 styled-components, JSS, Emotion 순서.

#### 성능 이슈

[CSS-in-JS와 성능 (2021)](https://megaptera.notion.site/CSS-in-JS-0afa302408f74f7a9712924ead6318be?pvs=4)

→ CSS 파일과 JS 파일 로딩의 차이.

[Why We're Breaking Up with CSS-in-JS (2022)](https://megaptera.notion.site/CSS-in-JS-4022ede93d06407ea6474a40be4cd906?pvs=4)

**대안**

[Linaria](https://linaria.dev/)

* CSS를 평범한 텍스트로 작성.
* React에 종속적이지 않지만, React Styled Component도 지원함.

[vanilla-extract](https://vanilla-extract.style/)

* CSS를 오브젝트 형태로 표현. React의 Inline Style과 유사함.
* React와 무관하게 사용 가능.
