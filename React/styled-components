# Styled-Components

Created: May 26, 2021 10:47 PM
Tags: CSS, React

## 개요

- `CSS in JS` 기술 중 하나
- `Tagged Template Literal`을 사용하여 작동

## Styled-Components 사용하기

- `div`를 `styled-components`를 사용하여 스타일링

```jsx
import React from 'react';
import styled from 'styled-components';

const Circle = styled.div`
  width: 5rem;
  height: 5rem;
  background: black;
  border-radius: 50%;
`;

function App() {
  return <Circle />;
}

export default App;
```

- `styled-components`에 `props`를 추가하는 법

```jsx
import React from 'react';
import styled from 'styled-components';

const Circle = styled.div`
  width: 5rem;
  height: 5rem;
  background: ${props => props.color || 'black'};
  border-radius: 50%;
  ${props =>
    props.huge &&
    css`
      width: 10rem;
      height: 10rem;
    `}
`;

function App() {
  return <Circle color="blue" />;
}

export default App;
```

- `Toggle element state` 사용법

```jsx
import React from 'react';
import styled from 'styled-components';

const StyledButton = styled.button`
  /* 공통 스타일 */
  display: inline-flex;
  outline: none;
  border: none;
  border-radius: 4px;
  color: white;
  font-weight: bold;
  cursor: pointer;
  padding-left: 1rem;
  padding-right: 1rem;

  /* 크기 */
  height: 2.25rem;
  font-size: 1rem;

  /* 색상 */
  background: #228be6;
  &:hover {
    background: #339af0;
  }
  &:active {
    background: #1c7ed6;
  }

  /* 기타 */
  & + & {
    margin-left: 1rem;
  }
`;

function Button({ children, ...rest }) {
  return <StyledButton {...rest}>{children}</StyledButton>;
}

export default Button;
```

- Custom component를 `styled-components`로 스타일링 하는 방법 (`antd` 사용)

```jsx
import styled from 'styled-components';
import { Input } from 'antd';

const CommonInput = styled(Input)`
  width: 450px;
  height: 30px;
  border: 1px solid #bbbbbb;
  padding: 0px;
`;

const IdInput = styled(CommonInput)`
	width: 200px;
`

const PasswordInput = styled(CommonInput)`
	width: 200px;
	height: 20px;
`

export default function Login() {
	return (
		<>
			<IdInput />
			<PasswordInput />
		</>
	)
}
```

## 참고

[https://react.vlpt.us/styling/03-styled-components.html](https://react.vlpt.us/styling/03-styled-components.html)