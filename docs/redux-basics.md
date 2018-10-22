# Redux Basics

There are 5 main functions in Redux.

```javascript
const {
    createStore, 
    combineReducers,
    compose,
    bindActionCreators,
    applyMiddleware
} = Redux;
```

```javascript
compose(func1, func2, func3)
```
It just compose multiple functions together, instead of 
```javascript
func3(func2(func1))
```

```javascript
const store = createStore(combineReducers({
    user: userReducer,
    error: errorReducer
}), {}, applyMiddleware(logger));
```

```javascript
function mapDispatchToProps(dispatch) {
    return bindActionCreators({
        fetchUser,
        clearError
    }, dispatch);
}
```