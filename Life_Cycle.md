# 라이프 사이클 (Life Cycle)

모든 리액트 컴포넌트에는 라이프 사이클(수명 주기)이 존재한다. 컴포넌트의 수명은 페이지가 렌더링되기 전인 준비 과정에서 시작하여 페이지가 사라질 때 끝난다.

프로젝트 진행 시 컴포넌트를 처음으로 렌더링할 때 처리해야 할 작업, 업데이트 전후로 처리해야 할 작업 또는 불필요한 업데이트를 방지하는 작업이 필요할 때가 있다.

이때 컴포넌트의 라이프 사이클 메서드를 사용한다. 라이프 사이클 메서드는 클래스형 컴포넌트에서만 사용 가능하며 함수형 컴포넌트에서는 Hooks 기능을 통해 비슷한 작업을 처리할 수 있다.

[공식 문서](https://ko.reactjs.org/docs/react-component.html)

## 1. 라이프 사이클 메서드

라이프 사이클 메서드는 총 아홉 가지가 있다.

**Will** 접두사가 붙은 메서드는 어떤 작업을 작동하기 **전** 실행되는 메서드, **Did** 접두사가 붙은 메서드는 어떤 작업을 작동한 **후**에 실행되는 메서드이다.

라이프 사이클은 총 세 가지 **마운트**, **업데이트**, **언마운트** 카테고리로 나뉜다.

> - 마운트: 페이지에 컴포넌트가 나타남
> - 업데이트: 컴포넌트 정보를 업데이트, 리렌더링 됨
> - 언마운트: 페이지에서 컴포넌트가 사라짐

### 1.1 마운트

DOM이 생성되고 웹 브라우저상에 나타나는 것을 말한다.

**마운트 메서드**

- constructor: 컴포넌트를 새로 만들 때마다 호출되는 클래스 생성자 메서드이다.
- getDerivedStateFromProps: props에 있는 값을 state에 넣을 때 사용하는 메서드이다.
- render: 렌더링하는 메서드이다.
- componentDidMount: 컴포넌트가 웹 브라우저상에 나타난 후 호출하는 메서드이다.

### 1.2 업데이트

컴포넌트는 다음 네 가지 경우에 업데이트한다.

1. props가 바뀔 때
2. state가 바뀔 때
3. 부모 컴포넌트가 업데이트 되었을 때(리렌더링했을 때)
4. forceUpdate()로 강제 업데이트를 수행할 때

**업데이트 메서드**

- getDerivedStateFromProps: 마운트 과정과 같이 props의 변화에 따라 state 값에도 변화를 주고 싶을 때 사용한다.
- shouldComponentUpdate: 컴포넌트가 리렌더링을 해야 할지 여부를 결정하는 메서드, 이 메서드는 boolean 값을 반환해야 하며 true를 반환 시 다음 라이프사이클 메서드를 계속 실행하고, false 반환 시 작업을 중지한다.
- render: 리렌더링 한다.
- getSnapShotBeforeUpdate: 컴포넌트 변화를 DOM에 반영하기 바로 직전에 호출하는 메서드이다.
- componentDidUpdate: 컴포넌트의 업데이트 작업이 끝난 후 호출하는 메서드이다.

### 1.3 언마운트

컴포넌트를 DOM에서 제거하는 것을 말한다.

**언마운트 메서드**

- componentWillUnmount: 컴포넌트가 웹 브라우저상에서 사라지기 전에 호출하는 메서드이다.
