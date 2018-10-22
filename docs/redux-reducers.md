## How Reducers work

Depending on actions (action's type and payload), reducers organise the change of state. For example, add a new user to the list, or filter users etc.

Some commonly used methods include:
`map()`, `filter()`, Spread Operator, Object.assign() etc.

```javascript
export default function(state = [], action) {
  switch (action.type) {
    case 'FETCH_USERS':
      return [...state, ...action.payload];
    case REMOVE_USER:
      return state.filter(user => user.email !== action.payload.email);
    default:
      return state;
  }
}
```

```javascript
export default function(state = null, action) {
  switch (action.type) {
    case 'SHOW_USER':
      return action.payload || false;
    default:
      return state;
  }
}
```

#### Put reducers together
/reducers/index.js
```javascript
import { combineReducers } from 'redux';
import authReducer from './authReducer';
import userReducer from './userReducer';

const rootReducers = combineReducers({
  // state: (state = {}) => state // use this empty if no reducers are created.
  auth: authReducer
  user: userReducer
});

export default rootReducers;
```