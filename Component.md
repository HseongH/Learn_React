# 컴포넌트

전체 페이지를 구성하는 하나의 조각이라고 할 수 있다.

```javascript
import React from "react";

function App() {
  return (
    <div className="App">
      <header>
        <h1 className="logo">logo</h1>

        <ul className="menu">
          <li className="menu-items">menu1</li>
          <li className="menu-items">menu2</li>
          <li className="menu-items">menu3</li>
        </ul>
      </header>

      <section>
        <div className="content">
          <img src="#" alt="image" />

          <p>내용</p>
        </div>
      </section>
    </div>
  );
}

export default App;
```

위와 같은 구조에서 header와 section을 하나의 독립적인 컴포넌트로 구성해 더 깔끔하고 간편하게 사용할 수 있다.

```javascript
import React from "react";

function App() {
  return (
    <div className="App">
      <Header />
      <Section />
    </div>
  );
}

export default App;
```

## 1. 클래스형 컴포넌트

컴포넌트를 선언하는 방법은 클래스형과 함수형 두 가지이다.

클래스형 컴포넌트는 자바스크립트 ES6의 클래스 형태로 구성한다.

클래스형 컴포넌트의 특징은 다음과 같다.

- render() 함수를 통해 JSX를 반환한다
- state 기능 및 라이프사이클 기능을 사용할 수 있다.
- 클래스 내부에 메서드를 정의해 사용하는 것도 가능하다.

**클래스형 컴포넌트의 형태**

```javascript
import React from "react";

class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {};
  }

  render() {
    return <h1>클래스형 컴포넌트 사용해보기</h1>;
  }
}

export default App;
```

---

## 2. 함수형 컴포넌트

함수형 컴포넌트의 장점은 다음과 같다.

- 클래스형 컴포넌트에 비해 선언하기 편하다.
- 메모리 공간도 클래스형 컴포넌트보다 덜 사용한다.
- 배포할 때 결과물의 크기가 더 작다.
- 리액트 16.8 이전 버전에서는 함수형 컴포넌트에서 state를 사용할 수 없다는 단점이 있었지만 16.8 버전부터 Hooks 기능을 이용해 함수형 컴포넌트에서도 state를 사용할 수 있게 되었다.

이러한 이유로 리액트 공식 메뉴얼에서는 함수형 컴포넌트와 Hooks를 사용할 것을 권장하고 있다.

**함수형 컴포넌트의 형태**

```javascript
import React from "react";

function FunctionComponent() {
  return <h1>함수형 컴포넌트 사용해보기</h1>;
}

export default FunctionComponent;
```

ES6의 화살표 함수를 이용하여 구성할 수도 있다.

```javascript
import React from "react";

const FunctionComponent = () => {
  return <h1>함수형 컴포넌트 사용해보기</h1>;
};

export default FunctionComponent;
```

---

## 3. props

properties를 줄인 표현으로 컴포넌트 속성 설정 시 사용하는 요소이다. props는 컴포넌트가 부모 컴포넌트로부터 받아온 데이터이다.

props는 부모 컴포넌트가 설정하는 값으로 자식 컴포넌트는 해당 props를 읽기 전용으로만 사용할 수 있다. 따라서 props의 값을 자식 컴포넌트에서 변경하는 것은 불가능하고 부모 컴포넌트에서만 변경이 이루어질 수 있다.

### 3.1 JSX 내부에서 props 렌더링

자바스크립트 표현식을 사용할 때와 마찬가지로 { } 내부에 props 값을 지정해준다.

```javascript
import React from "react";

const FunctionComponent = (props) => {
  return <h1>props 값 출력해보기 {props.name}</h1>;
};

export default FunctionComponent;
```

### 3.2 부모 컴포넌트에서 props 값 넘겨주기

```javascript
import React from "react";
import FunctionComponent from "./FunctionComponent";

class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {};
  }

  render() {
    return <FunctionComponent name="레미" />;
  }
}

export default App;
```

### 3.3 props 더 잘쓰기

[Proptypes](https://ko.reactjs.org/docs/typechecking-with-proptypes.html)

---

## 4. state

컴포넌트가 직접 가지고 있는 데이터이며 컴포넌트 내부에서 바뀔 수 있는 값을 의미한다.

리액트에는 두 가지 종류의 state가 있는 데 하나는 클래스형 컴포넌트가 지니고 있는 state이고, 다른 하나는 함수형 컴포넌트에서 useState 함수를 통해 사용하는 state이다.
