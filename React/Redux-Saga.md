# Redux-Saga

Created: July 8, 2021 3:58 PM
Tags: React

## 개요

> redux-saga is a library that aims to make application side effects (i.e. asynchronous things like data fetching and impure things like accessing the browser cache) easier to manage, more efficient to execute, easy to test, and better at handling failures. -

- `Action`에 대한 `Listener`
- 어플리케이션의 비동기 작업 또는 브라우저 캐시 액세스 같은 작업을 관리하기 쉽게, 효율적으로, 테스트하기 쉽게, 오류를 잘 처리하도록 하는 라이브러리
- `Generator`문법을 사용하여 비동기 flow를 쉽게 읽고 테스트를 작성할 수 있음
- 

## 기본 개념

- redux-saga의 기본 흐름

    `action => saga => action => reducer`

```jsx
// User List를 가져오는 Saga 함수
function* fetchUser(action) {
  try {
    const user = yield call(Api.fetchUser, action.payload.userId);
    yield put({type: "USER_FETCH_SUCCEEDED", user: user});
  } catch (e) {
    yield put({type: "USER_FETCH_FAILED", message: e.message});
  }
}

export default function* mySaga() {
	// action이 실행되면 fetchUser도 항상 실행
	yield takeEvery("USER_FETCH_REQUESTED", fetchUser);
}
```

- `USER_FETCH_REQUESTED` 액션을 감시하고, API호출을 트리거함
- `saga`를 사용하기 위해 redux-saga 미들웨어를 만들고 Redux Store에 연결해야함

```jsx
import { createStore, applyMiddleware } from 'redux'
import createSagaMiddleware from 'redux-saga'

import reducer from './reducers'
import mySaga from './sagas'

// create the saga middleware
const sagaMiddleware = createSagaMiddleware()
// mount it on the Store
const store = createStore(
  reducer,
  applyMiddleware(sagaMiddleware)
)

// then run the saga
sagaMiddleware.run(mySaga)
```

## Method

## 👿all

- 동시에 실행되고 전부 resolve되는 패턴

```jsx
export function* testSaga() {
  const [response1, response2] = yield all([asyncTask1(), asyncTask2()]);
}
```

## 👺call

- `Function.prototype.call()`과 같음

## 🐧takeEvery

- type에 맞게 들어오는 모든 액션을 다 실행

## 🇲🇰takeLastest

- 액션이 호출되었을 때 같은 액션이 실행중이면 그 액션은 파기되고 마지막 호출만 실행
- `POST`, `PUT`, `DELETE` 같은 리소스 변경할 때 유용

## 🦘put

- 액션을 호출함 (`dispatch`)

# 참고자료

[About | Redux-Saga](https://redux-saga.js.org/docs/About)

[The Basics Of ES6 Generators](https://davidwalsh.name/es6-generators)