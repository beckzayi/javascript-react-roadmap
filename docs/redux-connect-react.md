## How to connect Redux to React?

They are connected via a package called `react-redux`.

`<Provider>` - in index.js or a root js file
```jsx
import { createStore } from 'redux';
import { Provider } from 'react-redux';

const store = createStore(reducers); // import reducers

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root'));
```

`connect()` - in a React component js file (WrappedComponent)
```jsx
import { connect } from 'react-redux';

function mapStateToProps(state) {
    return {
        users: state.users
    }
}

function mapDispatchToProps() {
    // react-redux has a shorthand for this function
    // See below
}

connect(mapStateToProps, mapDispatchToProps)(WrappedComponent);
```

Redux can put action creators to the connect function.
```jsx
import * as actions from '../actions'; // import action creators

export default connect(mapStateToProps, actions)(WrappedComponent);
```

Or
```jsx
import { fetchUsers } as actions from '../actions'; // import action creators

export default connect(mapStateToProps, { fetchUsers })(WrappedComponent);
```

