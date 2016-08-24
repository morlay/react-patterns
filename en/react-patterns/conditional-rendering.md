## Conditional Rendering

You can't use regular if/else conditions inside a `render` function. [The conditional (ternary) operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator) is your friend.

#### `if`

```js
{condition && <span>Rendered when `truthy`</span> }
```

#### `unless`

```js
{condition || <span>Rendered when `falsey`</span> }
```

#### `if-else` (tidy one-liners)

```js
{condition
  ? <span>Rendered when `truthy`</span>
  : <span>Rendered when `falsey`</span>}
```

#### `if-else` (big blocks)

```js
{condition ? (
  <span>
    Rendered when `truthy`
  </span>
) : (
  <span>
    Rendered when `falsey`
  </span>
)}

```