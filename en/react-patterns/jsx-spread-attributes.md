## JSX Spread Attributes

Spread Attributes is a JSX feature. It's syntactic sugar for passing all of an object's properties as JSX attributes.

These two examples are equivalent.
```js
// props written as attributes
(<main className="main" role="main">{children}</main>)

// props "spread" from object
(<main {...{className: "main", role: "main", children}} />)
```

Spread Attributes is handy where you want a component to proxy some `props` and past the rest along.

```js
const FancyDiv = props => (<div className="fancy" {...props} />)
```

Order matters here. If `props.className` is define, it'll clobber the `className` definition (in the example above). If we want our component's `className` to win, it has to go after `{...props}`.

```js
// our `className` clobbers your `className`
const FancyDiv = props => (<div {...props} className="fancy" />)
```

In most cases, you're gonna have to trust people. Make your component durable by gracefully handling `props` your component is opinionated about.

```js
const FancyDiv = ({ className, ...props }) => (
  <div
    className={["fancy", className].join(' ')}
    {...props}
  />
)  
```
