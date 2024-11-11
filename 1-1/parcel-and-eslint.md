---
description: Parcel & ESLint
---

# Parcel & ESLint

## Parcel

특별한 설정 없이 바로 사용 가능한 빌드 도구

### 참고 사이트

* [Parcel 공식문서](https://parceljs.org/)
* [Parcel](https://megaptera.notion.site/Parcel-1a41ab8ce2044b6db24a47590ac9c33b?pvs=4)
* [vite](https://megaptera.notion.site/Vite-ca25958a716b4ff9be31bf0ea9247f33?pvs=4)

### 세팅

*   패기지 설치

    ```
    npm i -D parcel-reporter-static-files-copy
    ```
*   .parcelrc 파일 생성\
    아래 설정 넣기

    ```
    {
      "extends": ["@parcel/config-default"],
      "reporters":  ["...", "parcel-reporter-static-files-copy"]
    }
    ```
* 이미지가 보이게 됨\
  ![](<../.gitbook/assets/스크린샷 2024-10-23 오후 4.58.18.png>)\

*   코딩 화면

    <figure><img src="../.gitbook/assets/스크린샷 2024-10-23 오후 4.57.23.png" alt=""><figcaption><p>코딩 화면</p></figcaption></figure>

### 빌드&#x20;

*   dist 폴더가 생성 되고 그 안에 작업 된 파일들이 들어가게 된다.

    ```
    // dist 폴더 삭제
    rm -rf dist

    // 빌드 실행
    npx parcel build
    ```
*   dist 폴더만 실행해도 화면이 동일하게 열린다.

    ```
    npx servor ./dist
    ```

    *   터미널 화면

        <div align="left">

        <figure><img src="../.gitbook/assets/스크린샷 2024-10-23 오후 5.05.55.png" alt=""><figcaption></figcaption></figure>

        </div>

## ESLint

### 참고 사이트

* [ESLint 공식문서](https://eslint.org/)
* [린트](https://ko.wikipedia.org/wiki/%EB%A6%B0%ED%8A%B8\_\(%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4\))
* [정적 프로그램 분석](https://ko.wikipedia.org/wiki/%EC%A0%95%EC%A0%81\_%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%A8\_%EB%B6%84%EC%84%9D)
* [Coding conventions](https://en.wikipedia.org/wiki/Coding\_conventions)

### 무엇을 위해서?

* 스타일 통일
* 잠재적 문제 발견
* 베스트 프랙티스 추천 → 최신 트렌드를 학습하는데 활용할 수 있다.



***



npm run lint 했을 때 설정되어 있는 부분이 문제가 있는지 작동이 되지 않음
