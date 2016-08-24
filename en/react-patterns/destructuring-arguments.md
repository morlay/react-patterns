## Destructuring Arguments

Destructuring is an ES2015 feature. It pairs nicely with `props` in Stateless Funcions.

These examples are equivalent.

```js
const Greeting = props => <div>Hi {props.name}!</div>

const Greeting = ({ name }) => <div>Hi {name}!</div>
```

The spread operator allows you to collect all the remaining properties in a new object.

```js
const Greeting = ({ name, ...props }) =>
  <div>Hi {name}!</div>
```

We can use JSX Spread Attributes to proxy these to the rendered component.

```js
const Greeting = ({ name, ...props }) =>
  <div {...props}>Hi {name}!</div>
```

If your component is concerned with non-DOM `props`. It's important to "clean" `props` before passing it along. By destructuring `props`, we're making a new object **without** our API `props`.