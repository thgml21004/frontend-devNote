# Express

## 간단한 서버 앱 npm 패키지 세팅

*   폴더 생성\


    ```
    mkdir express-demo-app
    cd mkdir express-demo-app
    ```
*   .gitignore 파일 준비

    ```
    touch .gitignore
    echo "/node_modules/" > .gitignore
    ```
*   패키지 초기화

    ```
    npm init -y
    ```
*   TypeScript&#x20;

    ```
    npm i -D typescript
    npx tsc --init
    ```
*   ESLint

    ```
    npm i -D eslint
    npx eslint --init
    ```
*   ts-node

    ```
    npm i -D ts-node
    ```
* Express
* ```
  npm i express
  npm i -D @types/express
  ```

### npx eslint --init 설치 시 답변 참고

<figure><img src="../.gitbook/assets/스크린샷 2024-11-11 오후 7.14.47.png" alt=""><figcaption></figcaption></figure>

### app.ts 파일 생성

```
import express from 'express';

const port = 3000;

const app = express();

// http://localhost/
// req : 요청, res : 응답
// 응답한 걸 보낸다 'Hello, world!'
app.get('/', (req, res) => {
  res.send('Hello, world!');
});

app.listen(port, () => {
  console.log(`Server running at http://localhost:${port}`);
});
```

*   ts-node로 실행

    ```
    npx ts-node app.ts
    ```
*   package.json에서 명령어로 넣기

    ```
    "scripts": {
      "start": "ts-node app.ts",
      "lint": "eslint --fix ."
    },
    ```

서버에서 수정한 내용이 바로 반영되지 않는다.

서버를 껐다가 재 실행 후 새로고침 시 수정된 내용 반영되어 있음

### nodemon 설치

서버를 끊고 재실행하는것을 자동으로 대신 해줌

실제로는 사용하지 않음

```
npm i -D nodemon
npx nodemon app.ts
```

* package.json에서 명령어로 넣기

```
"scripts": {
  "start": "nodemon app.ts",
```

## REST API

* 필딩 제약 조건” 4가지를 모두 만족하지 않고, Resource와 HTTP Verb만 도입\
  `/write-post` (X)\
  `/posts` (O) -> 뭔가를 한다 (CRUD)
* CRUD에 대해 HTTP Method를 대입. Read는 Collection(복수)과 Item(Element)(단수)로 나뉨.
  * 기본 리소스 URL: `/products`
    1. Read (Collection) → `GET /products` ⇒ 상품 목록 확인
    2. Read (Item) → `GET /products/{id}` ⇒ 특정 상품 정보 확인
    3. Create (Collection Pattern 활용) → `POST /products` ⇒ 상품 추가 (JSON 정보 함께 전달)
    4. Update (Item) → `PUT 또는 PATCH /products/{id}` ⇒ 특정 상품 정보 변경 (JSON 정보 함께 전달)
    5. Delete (Item) → `DELETE /products/{id}` ⇒ 특정 상품 삭제
