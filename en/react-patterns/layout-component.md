## Layout component

Layout components result in some for of static DOM element. It might not need to update frequently, if ever.

Consider a component that renders two `children` side-by-side.

```js
<HorizontalSplit
  leftSide={<SomeSmartComponent />}
  rightSide={<AnotherSmartComponent />}
/>
```

We can aggressively optimize this component.

While `HorizontalSplit` will be `parent` to both components, it will never be their `owner`. We can tell it to update never, without affecting the updating components inside.

```js
class HorizantalSplit extends React.Component {
  shouldComponentUpdate() {
    return false
  }

  render() {
    <FlexContainer>
      <div>{this.props.leftSide}</div>
      <div>{this.props.rightSide}</div>
    </FlexContainer>
  }
}  
```