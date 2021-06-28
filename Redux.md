# 리덕스 (Redux)

리액트 상태 관리 라이브러리이다. 리덕스 사용 시 컴포넌트의 상태 업데이트 관련 로직을 다른 파일로 분리시켜서 효율적으로 관리 가능하고, 컴포넌트끼리 같은 상태를 공유해야 할 때 여러 컴포넌트를 거치지 않고 쉽게 상태 값을 전달하거나 업데이트할 수 있다.

## 1. 용어 정리

### 1.1 액션

상태에 어떠한 변화가 필요할 때 액션이 발생한다. 하나의 객체로 구성된다.

```javascript
{
  type: "UPDATE";
}
```

액션 객체는 반드시 type을 가지고 있어야 한다. 이 값을 액션의 이름이라 생각하면 된다. type 이외의 값은 나중에 상태 업데이트 시 참고해야 할 값이며, 작성자 마음대로 넣을 수 있다.

```javascript
{
    type: "TASK",
    data: {
        id: 1,
        content: "모던 자바스크립트 DEEP DIVE 정독하기"
    }
}
```

### 1.2 액션 생성 함수

액션 객체를 만들어 주는 함수이다.

```javascript
function addTask(data) {
  return {
    type: "TASK",
    data,
  };
}

const addTask = (data) => ({
  type: "TASK",
  data,
});
```

어떤 변화를 일으켜야 할 때마다 액션 객체를 만들어야 하는데 매번 액션 객체를 직접 작성하기 번거롭고 실수가 발생할 수 있기 때문에 함수로 만들어서 관리한다.

### 1.3 리듀서

변화를 일으키는 함수이다. 액션을 만들어서 발생시키면 리듀서가 현재 상태와 전달받은 액션 객체를 파라미터로 받아오고 두 값을 참조해 새로운 상태를 만들어서 반환해준다.

```javascript
const initialState = {
  data: {
    id: 1,
    content: "모던 자바스크립트 DEEP DIVE 정독하기",
  },
};

function reducer(state = initialState, action) {
  switch (action.type) {
    case TASK:
      return {
        data: {
          ...state.data,
          id: id + 1,
          content: "공부하기",
        },
      };

    default:
      return state;
  }
}
```

### 1.4 스토어

프로젝트에 리덕스를 적용하기 위해 생성한다. 한 개의 프로젝트는 하나의 스토어만 가질 수 있다. 스토어 안에는 현재 애플리케이션 상태와 리듀서, 내장 함수가 포함되어 있다.

### 1.5 디스패치

스토어 내장 함수 중 하나이다. 액션을 발생시키는 역할을 한다. 이 함수는 dispatch(action);과 같은 형태로 액션 객체를 파라미터로 넣어서 호출한다.

디스패치 함수가 호출되면 스토어는 리듀서 함수를 실행해 새로운 상태를 만들어준다.

### 1.6 구독

스토어 내장 함수 중 하나, subscribe 함수 안에 리스너 함수를 파라미터로 넣어서 호출해 주면, 이 함수가 액션이 디스패치되어 상태가 업데이트될 때마다 호출된다.

```javascript
const listener = () => {
  console.log("Update!!");
};

const unsubscribe = store.subscribe(listener);

unsubscribe(); // 구독을 해제할 때 호출
```
