## React Component re-rendering

#### Avoid Multiple re-rendering

```jsx
// Not to re-render the Header component when update
class Header extends React.Component {
    shouldComponentUpdate(nextProps, nextState) {
        return false;
    }

    render() {
        return <h1>My Header</h1>;
    }
}
```

Update state may be async. We can take the current state as the argument to avoid async update.
```javascript
increment = () => {
    this.setState(state => {
        return { count: state.count + 1 };
    });
}

shouldComponentUpdate(nextProps, nextState) {
    if (this.state.count !== nextState.count) {
        return true;
    }
    return false;
}
```
