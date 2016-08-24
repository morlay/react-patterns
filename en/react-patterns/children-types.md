## Children Types

React can render `children` of many types. In most cases it's either an `array` or a `string`.

`string`

```js
<div>
  Hello World!
</div>
```

`array`

```js
<div>
  {["Hello ", <span>World</span>, "!"]}
</div>
```

Functions may be used as children. However, it will required special consideration to be useful.

`function`

```js
<div>
  {(() => "hello world!")()}
</div>
```