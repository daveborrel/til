# Redux in a nutshell

Redux is a JS library that manages global state. Whenever the UI does something these "actions" will be tracked by "reducers" and will be updated.
The main idea is that there is a single place to store all of this state.

### How to Install

```
npm install @reduxjs/toolkit
npm install react-redux
```

Redux is most useful when there is a lot of application state needed in many places.

### Important Concepts

Action

```ts
const addTodoAction = {
  type: "todos/todoAdded",
  payload: "Buy milk",
};
```

Action Creator

```ts
const addTodo = (text) => {
  return {
    type: "todos/todoAdded",
    payload: text,
  };
};
```

A Very Basic Reducer

```ts
const initialState = { value: 0 };

function counterReducer(state = initialState, action) {
  // Check to see if the reducer cares about this action
  if (action.type === "counter/increment") {
    // If so, make a copy of `state`
    return {
      ...state,
      // and update the copy with the new value
      value: state.value + 1,
    };
  }
  // otherwise return the existing state unchanged
  return state;
}
```

https://redux.js.org/tutorials/essentials/part-1-overview-concepts
