# Destructure `console`

Logging and debugging your app while developing (or even on production sometimes)?

Instead of writing `console.log(...)` all over the place, you could do:

```js
const { log } = console
```

Even better:

```js
const { log, warn, error } = console 
```

And then just use `log(...)` or `warn(...)` or `error(...)` whenever you need to log something.