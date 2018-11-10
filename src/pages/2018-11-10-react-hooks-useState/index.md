---
path: "/react-hooks-useState"
date: "2018-11-10"
title: "React hooks useState"
tags: ['react', 'hooks', 'useState']
excerpt: "react hooks useState"
---
```javascript
const [state, setState] = useState(initialState);
```

## Functional updates

`setState` 接受一个`function`参数，可以获取上次的值。
```javascript
function Counter({initialCount}) {
  const [count, setCount] = useState(initialCount);
  return (
    <>
      Count: {count}
      <button onClick={() => setCount(0)}>Reset</button>
      <button onClick={() => setCount(prevCount => prevCount + 1)}>+</button>
      <button onClick={() => setCount(prevCount => prevCount - 1)}>-</button>
    </>
  );
}
```

**和`this.setState`不同，useState不会自动合并对象数据**

如有需要，可以自己手动合并
```js
setState(prevState => {
  // Object.assign would also work
  return {...prevState, ...updatedValues};
});
```

## Lazy initialization
如果`useState`的初始值是一个复杂计算，为了节省性能，可以给其传递一个 `function`

```js
const [state, setState] = useState(() => {
  const initialState = someExpensiveComputation(props);
  return initialState;
});
```
