## Proxy component

*(I'm not sure if this name makes sense)*

Buttons are everywhere in webapps. And every one of them must have the `type` attribute set to "button".

```js
(<button type="button">)
```

Writing this attribute hundreds of times is error prone. We can write a higher level component to proxy `props` to a lower-level `button` component.

```js
const Button = props => (<button type="button" {...props}>)
```

We can use `Button` in place of `button` and ensure that the `type` attribute is consistently applied everywhere.

```js
(<Button />)
// <button type="button"><button>

(<Button className="CTA">Send Money</Button>)
// <button type="button" class="CTA">Send Money</button>
```