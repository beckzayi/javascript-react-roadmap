## Immutable JavaScript

Immutable, it sounds intimidating. Basically, it means do not mutate the original JavaScript object or array. Expecially in the context of Redux, immutable is always a good practice.

Here, we provide two examples: the Spread Operator (ES6) and `Object.assign()`.

```javascript
function update(user = { id: 1, name: 'John' }, newUser = { name: 'Kate' }) {
    return { ...user, ...newUser }; // output { id: 1, name: 'Kate' }
}
```

```javascript
function(user = { id: 1, name: 'John' }, newUser = { name: 'Kate' }) {
    return Object.assign(user, newUser);
}
```

Also, we can use other common methods to achieve immutable:
`map()`
`filter()`
`reduce()`
`concat()`

`push()` is commonly used, but it is immutable.