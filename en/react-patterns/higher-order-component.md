## Higher-order component

A higher-order is a function takes and/or returns a function as an argument. It's not more complicated than that. So, what's a higher-order component? You guessed it, it's going to take and/or return a component.

If you're already using Container components, these are just generic containers, wrapped up in a function.

Let's start with our stateless component.

```js
const MyComponent = ({ data }) => {
  if (!data) { return <div>Waiting...</div> }

  return <div>{data}</div>
}
```

If it has data, it's gonna render. Otherwise it'll say that it's "waiting." Now for the the higher-order bit.

```js
const Enhance = ComposedComponent =>
  class extends React.Component {
    state = { data: null }

    componentDidMount() {
      this.setState({ data: 'Hello' })
    }

    render() {
      return (
        <ComposedComponent 
          {...this.props} 
          data={this.state.data} 
        />
      );
    }
  }
```

This is just a function that returns component that renders the component we wrap with it.

There's just one thing left to do. Wrap our component.

```js
const EnhancedMyComponent = Enhance(MyComponent)
```