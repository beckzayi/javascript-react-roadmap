## I don't want the development code on production (Node.js)

Scenario:
The App is built with React and Redux in Node.js (express for instance). We want to have `redux-logger` to console log the state changes. Obviously, redux-logger is not required on production site.

The origina code below. In this case, on production site user can see the `redux-logger`, which is not what we want.
```javascript
import { createStore, applyMiddleware } from 'redux';
import reduxThunk from 'redux-thunk';
import logger from 'redux-logger'
import reducers from './reducers';

const store = createStore(reducers, applyMiddleware([reduxThunk, logger]));
```

Solution: we split the code by `process.env.NODE_ENV` variable.
```javascript
// Do not import 'redux-logger' on the top
const middlewares = [reduxThunk];

if (process.env.NODE_ENV === 'development') {
  const { logger } = require('redux-logger');
  middlewares.push(logger);
}

const store = createStore(reducers, applyMiddleware(...middlewares));
```

`process.env.PUBLIC_URL`

when navigating to GitHub Pages link, nothing might shows up. Why was the app working perfectly fine locally but not on a server? Enter the mysterious, ethereal `process.env.PUBLIC_URL`. Below is an example in a React app.
```jsx```
<Router basename={process.env.PUBLIC_URL}>
  <App />
</Router>
```
