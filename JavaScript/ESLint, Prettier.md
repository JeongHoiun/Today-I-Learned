# ESLint, Prettier

Created: May 28, 2021 8:29 AM
Tags: DevCulture, JavaScript

## ESLinst & Prettier

- `ESLint` : 코드 문법 자동 검사와 코딩 스타일에 대한 규칙 정의
- `Prettier` : 코딩 스타일에 특화
- 팀원 간의 코드 규칙을 맞출 수 있음
- 코드의 가독성을 높임

## 설치

```
yarn add -D eslint prettier
```

## 설치해야하는 패키지

### eslint-config-prettier

- `eslint`와 `prettier`에 겹치는 포매팅 룰을 삭제

### eslint-plugin-prettier

- `eslint`에 `prettier`의 포매팅 기능을 추가

## 설정

## ESline 설정

- `.eslinerc` 파일 수정

```json
{
  "extends": ["plugin:prettier/recommended"]
}
```

## Prettier 설정

- `.prettierrc`파일 수정

```json
{
    "trailingComma": "es5",  // 여러 줄을 사용할 때, 후행 콤마 사용 방식
    "tabWidth": 2,  // 탭 너비
    "semi": true,  // 세미콜론 꼭 붙여야함
    "singleQuote": true  // 작은따옴표 사용 여부
}
```

- 옵션에 대한 더 많은 정보는 다음 확인

[Options · Prettier](https://prettier.io/docs/en/options.html)

## Airbnb 스타일 가이드 코드 규칙 적용하기

## airbnb with eslint 패키지 설치

- 기본적으로 이 패키지는 ECMAScript 6+와 (자바스크립트란 소리) 리액트를 포함하는 airbnb `ESLint` 규칙을 제공하고 아래 5개의 패키지들을 필수로 합니다.
- `esline`, `eslint-plugin-import`, `eslint-plugin-react`, `eslint-plugin-react-hooks`, `eslint-plugin-jsx-a11y`

### eslint-config-airbnb

- Airbnb의 ESlint 스타일 가이드

### eslint-plugin-import

- ES2015+의 `import`/`export` 구문 지원

### eslint-plugin-react

- `react` 지원

### eslint-plugin-jsx-a11y

- 접근성 지원

### eslint-plugin-react-hoos

- `react hook` 지원

## eslint 설정파일 변경

- `.eslintrc` 파일 수정

```json
{
    "plugins": ["prettier"],
    "extends": ["airbnb", "plugin:prettier/recommended"],  //airbnb lint 사용
    "parserOptions": {  //javascript 언어 옵션 지정
        "sourceType": "module",
        "ecmaFeatures": {
            "jsx": true
        }
    },
    "env": {
        "browser": true,  //browser 변수 사용
        "node": true
    },
    "ignorePatterns": ["node_modules/"],  // node_modules에 있는 파일들은 무시
    "rules": {
        "prettier/prettier": "error",  //prettier 설정에 반하는 구문은 error표시
        "react/jsx-filename-extension": ["warn", { "extensions": [".js", ".jsx"] }] // js, jsx 확장자의 파일을 import할때 js, jsx 확장자는 무시
    },
}
```

## 결과

- 세미콜론을 붙이지 않으면 다음과 같은 에러를 볼 수 있음

![ESLint,%20Prettier%20/Untitled.png](ESLint%2C%20Prettier/Untitled.png)

## 참고

- [https://simsimjae.medium.com/prettier와-eslint설정하기-타입스크립트-설정-110dc8ab94b6](https://simsimjae.medium.com/prettier%EC%99%80-eslint%EC%84%A4%EC%A0%95%ED%95%98%EA%B8%B0-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%84%A4%EC%A0%95-110dc8ab94b6)
- [https://prettier.io/docs/en/index.html](https://prettier.io/docs/en/index.html)
- [https://eslint.org/docs/user-guide/configuring/](https://eslint.org/docs/user-guide/configuring/)