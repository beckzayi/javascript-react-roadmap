## `setState()`

`this.setState()` is asynchronous. React is trying to avoid unnecessary re-render.

Imagine below, what is the result of count?
```javascript
constructor(props) {
    super(props);
    this.state = {
        count: 0
    };
}

handleIncrement() {
    this.setState({ count: this.state.count + 3 });
    this.setState({ count: this.state.count + 1 });
    this.setState({ count: this.state.count + 2 });
}
```

Result is 2. Effectively, you're quening up state changes. React will batch them up, figure out the result and then efficiently make that change.

Try to work as we expect. When you pass functions to `this.setState()`, it plays through each of them.
```javascript
// Result is to increase 6
handleIncrement() {
    this.setState(state => {
      return { count: state.count + 3 };
    });
    this.setState(state => {
      return { count: state.count + 1 };
    });
    this.setState(state => {
      return { count: state.count + 2 };
    });
}
```

With passing a function to `setState()`, it can have programatic control.
```javascript
handleIncrease() {
    this.setState(state => {
        if (state.count >= 5 )
            return;
        return { count: state.count + 1 };
    });
}
```

State should be considered private data. Don't use `this.state` for derivations of `props`. Don't do this below.
```javascript
constructor(props) {
    super(props);
    this.state = {
        fullName: props.firstName = ' ' + props.lastName
    };
}
```

Instead, derive computed properties directly from the `props` themselves.
```jsx
render() {
    const { firstName, lastName } = this.props;
    const fullName = firstName + ' ' + lastName;
    return (
        <h1>{ fullName }</h1>
    );
}
```
