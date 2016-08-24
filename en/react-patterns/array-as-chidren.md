## Array as children

Providing an array as `children` is a very common pattern. It's how lists are drawn in React.

We can use `map()` to create an array of React Elements for every value in the array.

```js
(<ul>
  {["first", "second"].map((item, i) => (
    <li key={i}>{item}</li>
  ))}
</ul>)
```

That's equivalent to providing a literal `array`.

```js
(<ul>
  {[
    <li key={0}>first</li>,
    <li key={1}>second</li>,
  ]}
</ul>)
```

This pattern can be combined with destructuring, JSX Spread Attributes, and other components, for some serious terseness.

```js
(<ul>
  {arrayOfMessageObjects.map(({ id, ...message }) =>
    <Message key={id} {...message} />
  )}
</ul>)
```