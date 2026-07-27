# Redux

This document explains Redux — a predictable state container for JavaScript apps — and shows a practical example integrating Redux with a React app. It covers core concepts, setup, a complete counter example, async actions with thunk, and a brief note on Redux Toolkit (recommended).

---

## What is Redux?

Redux is a predictable state container for JavaScript applications. It helps manage application state in a single place (the store), making the state changes explicit and easier to debug and test.

Core principles:
- Single source of truth: The whole app state is stored in a single store object.
- State is read-only: The only way to change state is to emit an action describing what happened.
- Changes are made with pure functions: Reducers are pure functions that take the previous state and an action, and return the next state.


## Main concepts

- Store: Holds the application state.
- Action: Plain JavaScript object describing what happened. Must have a `type` property.
- Action creator: Function that returns an action object.
- Reducer: Pure function (state, action) => newState.
- Middleware: Optional extension point between dispatching an action and the moment it reaches the reducer (used for logging, async, etc.).


## When to use Redux

Use Redux when:
- You have complex state that must be shared across many components.
- You need time-travel debugging or strict tracing of state changes.
- You want predictable state transitions and easier testing.

If your state needs are simple, prefer React's built-in Context + hooks or local component state. For new projects, consider Redux Toolkit (RTK) which simplifies Redux usage.


## Setup

Install packages:

```bash
npm install redux react-redux
# For async actions
npm install redux-thunk
# Recommended: Redux Toolkit (simpler, includes thunk)
npm install @reduxjs/toolkit
```


## Example: Counter (plain Redux + React)

This example shows how to build a simple counter using Redux and React.

Files:
- src/store.js
- src/counterSlice.js (not a Toolkit slice — here it's plain reducer/actions)
- src/index.js
- src/Counter.js


### src/counterSlice.js

```js
// counterSlice.js (plain Redux style)
// Actions
export const INCREMENT = 'counter/increment';
export const DECREMENT = 'counter/decrement';
export const INCREMENT_BY = 'counter/incrementBy';

export const increment = () => ({ type: INCREMENT });
export const decrement = () => ({ type: DECREMENT });
export const incrementBy = (amount) => ({ type: INCREMENT_BY, payload: amount });

// Reducer
const initialState = { value: 0 };

export default function counterReducer(state = initialState, action) {
  switch (action.type) {
    case INCREMENT:
      return { ...state, value: state.value + 1 };
    case DECREMENT:
      return { ...state, value: state.value - 1 };
    case INCREMENT_BY:
      return { ...state, value: state.value + action.payload };
    default:
      return state;
  }
}
```


### src/store.js

```js
import { createStore, applyMiddleware, combineReducers } from 'redux';
import thunk from 'redux-thunk';
import counterReducer from './counterSlice';

const rootReducer = combineReducers({
  counter: counterReducer,
});

// Add middleware. Thunk is optional, used for async actions.
const store = createStore(rootReducer, applyMiddleware(thunk));

export default store;
```


### src/Counter.js

```jsx
import React from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { increment, decrement, incrementBy } from './counterSlice';

export default function Counter() {
  const value = useSelector((state) => state.counter.value);
  const dispatch = useDispatch();

  return (
    <div>
      <h2>Counter: {value}</h2>
      <button onClick={() => dispatch(decrement())}>-</button>
      <button onClick={() => dispatch(increment())}>+</button>
      <button onClick={() => dispatch(incrementBy(5))}>+5</button>
    </div>
  );
}
```


### src/index.js

```jsx
import React from 'react';
import { createRoot } from 'react-dom/client';
import { Provider } from 'react-redux';
import App from './App'; // assume App renders <Counter />
import store from './store';

const root = createRoot(document.getElementById('root'));
root.render(
  <Provider store={store}>
    <App />
  </Provider>
);
```


## Async actions (thunk)

For side effects and async logic (network requests), use middleware like redux-thunk or redux-saga. Thunk lets action creators return a function that receives dispatch and getState.

Example: fetch a numeric value from an API and set it in the counter.

```js
// asyncActions.js
export const fetchInitialValue = () => async (dispatch) => {
  dispatch({ type: 'counter/fetchStart' });
  try {
    const res = await fetch('/api/counter');
    const data = await res.json();
    dispatch({ type: 'counter/set', payload: data.value });
  } catch (err) {
    dispatch({ type: 'counter/fetchError', payload: err.message });
  }
};
```

Reducer would handle the new action types accordingly.


## Debugging and DevTools

Install Redux DevTools extension in your browser and enable the enhancer in your store when in development. Many setups (including Redux Toolkit) enable DevTools by default.


## Redux Toolkit (recommended)

Redux Toolkit (RTK) is the official, opinionated, batteries-included toolset for efficient Redux development. It reduces boilerplate and includes utilities like `createSlice`, `configureStore`, and built-in thunk support.

Quick RTK counter example:

```js
// src/features/counter/counterSlice.js (RTK)
import { createSlice } from '@reduxjs/toolkit';

const counterSlice = createSlice({
  name: 'counter',
  initialState: { value: 0 },
  reducers: {
    increment(state) {
      state.value += 1; // Immer allows "mutating" syntax
    },
    decrement(state) {
      state.value -= 1;
    },
    incrementBy(state, action) {
      state.value += action.payload;
    },
  },
});

export const { increment, decrement, incrementBy } = counterSlice.actions;
export default counterSlice.reducer;

// store.js (RTK)
import { configureStore } from '@reduxjs/toolkit';
import counterReducer from './features/counter/counterSlice';

export default configureStore({
  reducer: { counter: counterReducer },
});
```

RTK is the recommended approach for most new projects because it eliminates much of the manual wiring shown in the plain example.


## Best practices

- Keep reducers pure and small.
- Normalize deeply nested state (use entity maps by id).
- Prefer selectors to read computed/derived data from state.
- Co-locate related actions and reducers (slices in RTK).
- Use middleware for side effects; prefer thunks or saga depending on complexity.


## Resources

- Official Redux docs: https://redux.js.org/
- Redux Toolkit: https://redux-toolkit.js.org/
- React-Redux: https://react-redux.js.org/


---

Generated: Detailed Redux guide with examples suitable for inclusion in a Learn-React repository.
