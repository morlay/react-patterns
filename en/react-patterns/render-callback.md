## Render callback

This a component that uses a Render callback. It does so a way that's not useful but it's good for illustration.

```js
const Width = ({ children }) => children(500)
```

The component calls `children` as a function, with some number of arguments. Here, it's the number `500`.

To use this component, we give it a [function as `children`](./function-as-children.html).

```js
<Width>
  {width => <div>window is {width}</div>}
</Width>
```

We get output that looks like this.

```js
<div>window is 500</div>
```

We can use this `width` value to make rendering decisions.

```js
<Width>
  {width =>
    width > 600
      ? <div>min-width requirement met!</div>
      : null
  }
</Width>
```

If we plan to use this condition a lot, we can define another components to encapsulate the reused logic.

```js
const MinWidth = ({ width: minWidth, children }) =>
  <Width>
    {width =>
      width > minWidth
        ? children
        : null
    }
  </Width>
```


Obviously a static `Width` component isn't valuable but one that watches the browser window is. Here's a sample implementation.

```js
class WindowWidth extends React.Component {
  constructor() {
    super()
    this.state = { width: 0 }
  }

  componentDidMount() {
    this.setState(
      {width: window.innerWidth},
      window.addEventListener(
        "resize",
        ({ target }) =>
          this.setState({width: target.innerWidth})
      )
    )
  }

  render() {
    return this.props.children(this.state.width)
  }
}
```

Alternatively, many developers favor [Higher Order Components](./higher-order-component.html) for this type of functionality.