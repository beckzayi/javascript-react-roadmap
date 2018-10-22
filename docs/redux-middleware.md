## Redux Middleware

It is something sitting between action creators and reducers.


Depending on the action type and payload. The middleware can choose to let the action pass through, manipulate the action, log it, or stop it at together before it reaches the reducer.


A few popular packages: `redux-thunk`, `redux-promise`, `redux-saga`

#### `redux-thunk`

The purpse of redux-thunk is to give you direct access to the dispatch method. In action creators, instead of returning an object, return a function. By returning a function, this function is how we get direct access to the dispatch method.


index.js
```javascript
import { createStore, applyMiddleware } from 'redux';
import { Provider } from "react-redux";
import reduxThunk from 'redux-thunk';

const store = createStore(rootReducers, applyMiddleware(reduxThunk));
// And then, put store to <Provider>
```

in action creator
```javascript
export function fetchUsers() {
    return function(dispatch) {
        dispatch({ type: 'FETCH_USERS' });
    }
}
```

If you want to add logger to middleware, simply to add to `applyMiddleware`.
```javascript
const { logger } = require('redux-logger');
const store = createStore(rootReducers, applyMiddleware([reduxThunk, logger]));
```
