# Immer vs Immutable

Created: May 31, 2021 12:05 PM
Tags: JavaScript, React

## Immutability in JavaScript

- JS의 primitive 변수는 불변하다

```jsx
var name = "mark cuban"
name = "John Steve"
```

- 위와 같은 코드에서 값이 변했다고 보여지지만 실제로는 변수가 재할당 된 것.
    - `JavaScript`에는 새로운 공간에 값을 할당하고 변수가 가르키는 주소를 변경하는 방식으로 변수에 값을 재할당
- 값을 재 할당 하는 것은 불변성과는 다름.
- `JavaScript`에서 `mutable`한 자료구조가 몇 있음. 그 중 하나가 `Arrays`

```jsx
let arrOne = [];
arrOne.push(2);
```

- `.push()` 함수를 이용하여 `array`의 값을 변경할 수 있음

## Immer

### About

- `copy-on-write` 메커니즘을 사용
- 현재 상태에 대해 프록시의 역할을 하는 `draftState`에 변경 사항을 적용하는 것

### Usage

```jsx
produce(currentState, producer: (draftState) => void): nextState
```

- `currentState`와 `draftState`를 가져와서 `draftState`의 변경 사항을 반영하도록 `nextState`를 업데이트

### Example

```jsx
const nextState = produce(baseState, draftState => {
    draftState.push({todo: "Tweet about it"})
    draftState[1].done = true
})
```

- baseState는 그대로 있고 draftState가 업데이트 되면서 반영nextState에 반영됨

## Immutable.js

### Aboue

- `List`와 `Map`과 같은 데이터 구조에 대한 API를 제공

### Example

```jsx
const { Map } = require('immutable');

const map1 = Map({ a: 1, b: 2, c: 3 });

const map2 = map1.set('b', 50);

map1.get('b') + " vs. " + map2.get('b'); // 2 vs. 50
```

- 데이터 불변을 유지하면서 `get`, `set`으로 작업 수행

```jsx
List(['apple','orange','grape'])
```

- `Immutable.js`에서 `List`사용

```jsx
fromJS(['apple','orange','grape'])
```

- `fromJS`를 사용하면 `List`나 `Map`으로 래핑할 필요 없이 변경 불가능한 데이터로 변환해줌

## Immer v. Immutable.js

## Benefits that comes with `Immer`

- BolerPlate가 적어서 코드베이스를 전반적으로 줄일 수 있음
- `JavaScript`의 데이터 타입 및 구조에서 작동하기 때문에 새 API를 배울 필요 없음
- Support for patches

## Downsides to `Immer` as a library

- 프록시 오브젝트를 지원하는 환경이 필요
- class instance와 같은 복잡한 객체 타입에 대한 지원을 하지 않음

## Benefits that comes with `Immutable.js`

- `JavaScript`의 고유 데이터 구조가 아닌 다른 데이터 구조를 제공함 (Ordered Map, Record 등)
- `reducer`에서 변경된 정확한 데이터를 알 수 있음
- 빠름

## Downsides to `Immutable.js` as a library

- 데이터 쓰는 속도는 빠르지만 읽기 속도는 느림
- 새롭고 복잡한 구문과 API를 알아야함 ( `.set()` 과 같은)
- 구성하는 모든 불변 컬렉션에 대해 새로 적절한 `Immutable.js` 컬렉션을 사용해야함

## 참고

- [https://blog.logrocket.com/immer-and-immutable-js-how-do-they-compare/](https://blog.logrocket.com/immer-and-immutable-js-how-do-they-compare/)
- [https://immerjs.github.io/immer/](https://immerjs.github.io/immer/)
- [https://immutable-js.github.io/immutable-js/docs/#/](https://immutable-js.github.io/immutable-js/docs/#/)