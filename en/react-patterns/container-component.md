## Container component

"A container does data fetching and then renders its corresponding sub-component. That’s it."&mdash;[Jason Bonta](https://twitter.com/jasonbonta)

So, given a reusable `CommentList` component.

```js
const CommentList = ({ comments }) =>
  <ul>
    {comments.map(comment =>
      <li>{comment.body}-{comment.author}</li>
    )}
  </ul>
```

We can create a new component responsible for fetching data and re-rendering the unopinionated `CommentList` component.

```js
class CommentListContainer extends React.Component {
  state = { comments: [] }

  componentDidMount() {
    $.ajax({
      url: "/my-comments.json",
      dataType: 'json',
      success: comments => this.setState({ comments }),
    });
  }

  render() {
    return <CommentList comments={this.state.comments} />
  }
}
```

We can write different containers for different application contexts.