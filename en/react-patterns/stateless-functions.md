## Stateless functions

[Stateless functions](https://facebook.github.io/react/docs/reusable-components.html#stateless-functions) are a brilliant way to define highly reusable components.
They don't hold `state` or `refs`; they're just functions.

```js
const Greeting = () => <div>Hi there!</div>
```

They get passed `props` and `context`.

```js
const Greeting = (props, contex) =>
  <div style={{color: context.color}}>Hi {props.name}!</div>
```

They can define local variables when a function block is used.

```js
const Greeting = (props, contex) => {
  const style = {
    fontWeight: "bold",
    color: contex.color,
  }

  return <div style={style}>{props.name}</div>
}
```

But you could get the same affect with other fuctions.

```js
const getStyle = context => ({
  fontWeight: "bold",
  color: contex.color,
})

const Greeting = (props, contex) =>
  <div style={getStyle(context)}>{props.name}</div>
```

They can have `defaultProps`, `propTypes` and `contextTypes`.

```js
Greeting.propTypes = {
  name: PropTypes.string.isRequired
}
Greeting.defaultProps = {
  name: "Guest"
}
Greeting.contextTypes = {
  color: PropTypes.string
}
```
