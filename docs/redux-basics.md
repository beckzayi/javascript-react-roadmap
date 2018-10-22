# Redux Basics

In short, a few steps to set up Redux in React.
1. `npm install redux react-redux`
2. index.js - import `Provider` and use `createStore`
3. component js file, use `connect()` method to connect the component with Redux
4. Action creators
5. Reducers
6. `applyMiddleware([redux-thunk, redux-logger])` optional

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