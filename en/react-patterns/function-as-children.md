## Function as children

Using a function as `children` isn't inherantly useful.

```js
<div>{(() => "hello world!")()}</div>
```

However, it can be used in component authoring for some serious power. This technique is often referred to as `render callbacks` and powers libraries like [ReactMotion](https://github.com/chenglou/react-motion).

This is a powerful technique used by libraries like ReactMotion. When applied, rendering logic can be kept in the owner component, instead of being delegated.

See [Render callbacks](./render-callbacks.html), for more details.