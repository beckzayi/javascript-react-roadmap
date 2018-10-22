## ES6 Features

* Arrow Functions
```javascript
var removeUser = (id) => {
    // code to remove user
}
```

* Block Scope
let vs var
```javascript
let
const
```

* Default Values and the Spread Operator
```javascript
function(state = {}, action) {
    switch (action.type) {
        case 'FETCH_USERS':
            return state;
        case 'INVITE_USER':
            return [ ...state, action.payload ];
        default:
            return state;
    }
}
```

* Destructuring
```javascript
const {
    createStore, 
    combineReducers,
    compose,
    bindActionCreators,
    applyMiddleware
} = Redux;
```

* Template Strings
```javascript
function consoleId(id) {
    return `The id is: ${id}`;
}
```