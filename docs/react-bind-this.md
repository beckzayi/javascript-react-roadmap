## this in React

`this` sometimes is confusing. There are a few ways to handle `this` in React.

```javascript
handleClick = () => {
    this.setState({ count: this.state.count + 1 })
}
```


```javascript
constructor(props) {
    super(props);
    this.handleClick = this.handleClick.bind(this);
}
handleClick() {
    this.setState({ count: this.state.count + 1 })
}
```


```javascript
render() {
    return(
        <div>
            <button onClick={() => this.setState({ count: this.state.count + 1 })}>Add to Count<button>
        </div>
    );
}
```
