## Children pass-through

There are times you might create a component designed to apply `context` and render it's `children`.

```js
class SomeContextProvider extends React.Component {
  getChildContext() {
    return { some: "context" }
  }

  render() {
    // how best do we return `children`?
  }
}
```

You're faced with a decision. Wrap `children` in an extranious `<div />` or return `children` directly. The first options gives you extra markup (which can break some stylesheets). The second will result in unhelpful errors.

```js
// option 1: extra div
return <div>{children}</div>

// option 2: unhelpful errors
return children
```

It's best to treat `children` as an opaque data type. React provides `React.Children` for dealing with `children` approprately and opting back into helpful errors.

```js
return React.Children.only(this.props.children)
```