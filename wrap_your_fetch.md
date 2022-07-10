# Wrap your fetch

Ever written a fetch or an axios API call and then forgot to handle an error?

Not all async functions are safe – ie, some throw an error. Typically, you would go for the `Promise.then().catch()` or the `try ... catch` mechanism. But you have to remember to write a `catch` or you have to face runtime errors. Plus, the code gets verbose all the time.

A better alternative is just using a wrapper function so that you can just do something like this:

```js
const getData = (params) => fetch('some url here').then(r => r.ok ? r.json() : {throw new Error('error msg')})
const { data, error } = await wrapper(() => getData({ id: 1 }))
if (error) {
  // handle error path
} else {
  // handle success path with `data`
}
```

Here's the wrapper function:

```js
const wrapper = async fn => {
  let res, err;
  try {
    res = await fn()
  } catch (e) {
    err = e
  } finally {
    return { data: res, error: err }
  }
}
```

This can be used for both async and normal functions that _could_ throw an error.
