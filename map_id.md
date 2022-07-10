# Map ID

This scenario plays out quite often:

```js
const someListOfObjects = [...]
const listOfIds = someListOfObjects.map(obj => obj.id)
```

It plays so often in apps that you could have a `mapIds` function for it:

```js
const mapIds = list => list.map(o => o.id)
```

And now it's easy to use like so:

```js
const someListOfObjects = [...]
const ids = mapIds(someListOfObjects)
```

In fact, this pattern can be generalized further:

```js
const mapKeys = key => list => list.map(o => o[k])
```

Now, creating different kinds of maps is easy:

```js
const someListOfObjects = [...]

// map the key 'id' to get all ids from a list of objects 
const mapIds = mapKeys('id')
const ids = mapIds(someListOfObjects)

// map the key 'name' to get all 'names' from a list of objects
const mapNames = mapKeys('name')
const names = mapNames(someListOfObjects)
```