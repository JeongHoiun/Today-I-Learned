# 동시성모드(실험단계)

Created: May 24, 2021 1:57 PM
Tags: React

## 개요

- 자바스크립트는 단일 스레드로 동작함
- 그렇다고해서 동시에 여러개의 일을 수행 못하는 것은 아님.
- `React`에서 여러가지 일을 동시에 진행하는 것처럼 UX를 보여줄 수 있도록 `Concurrent Mode`를 개발중

## 동시성 모드란?

- `동시성` : 독립적으로 실행될 수 있는 여러 조각으로 나누어서 프로그램을 구조화하는 방식
- 렌더링 과정을 더 작은 작업들로 나누고, 스케줄러를 통하여 각 작업들에 중요도에 따른 우선 순위를 부여
- 동시성 제어를 통해 할 수 있는 것
    - 메인 스레드를 블록하지 않는다
    - 동시에 여러 작업들을 처리하고, 우선 순위에 따라 각 작업들 간에 전환할 수 있다
    - 최종 결과로 확정하지 않고도 부분적으로 트리를 렌더링할 수 있다
- 메인 스레드를 블록하지 않으므로 사용자가 키를 누르는 등 더 중요한 작업이 실행됐을 때, 렌더링을 미룰 수 있음
- 디바운싱(반복되는 이벤트를 마지막 이벤트가 들어왔을 때 한꺼번에 처리)이 아님.

## 동시성 모드 엿보기

### Suspense

- 스피너와 같이 데이터를 불러오는 동안 기다리는 상태를 선언적으로 지정

```xml
const ProfilePage = React.lazy(() => import('./ProfilePage')); // 지연 로딩

// 프로필을 불러오는 동안 스피너를 표시합니다
<Suspense fallback={<Spinner />}>
  <ProfilePage />
</Suspense>
```

### SuspenseList

- 여러 Suspense 컴포넌트들을 감싸서 자식 컴포넌트들의 표시 순서를 제어할 수 있음
- 불러온 컴포넌트를 언제 표시할 지 `React`에게 지시하는 역할만 담당

```xml
const [id, setId] = useState(1);
<SuspenseList revealOrder="forwards">
  <Suspense fallback={<Spinner />}>
    <Details id={id} />
  </Suspense>
  <Suspense fallback={<Spinner />}>
    <Comments id={id} />
  </Suspense>
</SuspenseList>
```

### useTransition

- 인터넷 연결이 빠른 사용자는 스피너를 아예 표시하지 않아도 됨
- `useTransition` 훅을 통해 스피너나 대체 컴포넌트를 표시하기 전까지 대기할 시간을 지정할 수 있음.
- 훅이 반환하는 값
    - `startTransition`: 어떤 State를 지연시키고자 하는지 React에게 알려주는 함수
    - `isPending`: 전환(Transition)이 현재 이루어지고 있는지 알려주는 불리언 값

```jsx
const [id, setId] = useState(1);
const [startTransition, isPending] = useTransition({ timeoutMs: 3000 });
const onClick = id => {
  startTransition(() => {
    setId(id);
  });
};
```