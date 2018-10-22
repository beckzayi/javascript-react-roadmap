## Test with Jest and Enzyme

In an App built with React and Redux, How to test component, action creators, and reducers?

Jest expects fo find our tests in a `__tests__` folder.

Jest finds all files ending in `.test.js` and `.spect.js`, and executes tests inside of them.

1. /component/__tests__/App.test.js - To test if it contains a component
```javascript
import React from 'react';
import { shallow, mount, render } from 'enzyme';
import App from '../App';
import CommentBox from '../CommentBox';

let wrapped;

beforeEach(() => {
    wrapped = shallow(<App />);
});

it('show a comment box', () => {
    expect(wrapped.find(CommentBox).length).toEqual(1);
});
```

2. /actions/__tests__/index.test.js
```javascript
import { saveComment } from '../../actions';
import { SAVE_COMMENT } from '../types';

describe('saveComment', () => {
    it('has the correct action type', () => {
        const action = saveComment();
        expect(action.type).toEqual(SAVE_COMMENT);
    });

    it('has the correct action payload', () => {
        const action = saveComment('Save my comment');
        expect(action.payload).toEqual('Save my comment');
    });
});
```

3. /reducers/__test__/comments.test.js
```javascript
import commentsReducer from '../comments';
import { SAVE_COMMENT } from '../../actions/types';

it('handles actions of type SAVE_COMMENT', () => {
    const action = {
        type: SAVE_COMMENT,
        payload: 'Add New Comment'
    };
    const newState = commentsReducer([], action);
    expect(newState).toEqual(['Add New Comment']);
});

it('handles actions with unknown type', () => {
    const newState = commentsReducer([], {});
    expect(newState).toEqual([]);
});
```


Please note: to test Redux actions and reducers, we have to find an way to work around `<Provider>` (`store`) and Jest.

Put `<Provider>` in another file `Root.js`, instead of `index.js`.
Root.js
```jsx
export default ({ children, initialState = {} }) => {
    const store = createStore(
        reducers, 
        initialState
    );

    return (
        <Provider store={store}>
            {children}
        </Provider>
    );
};
```

index.js
```jsx
import Root from './Root';
import App from './components/App';
ReactDOM.render(
    <Root>
        <App />
    </Root>, 
    document.getElementById('root'));
```

####Redux Test Errors
Invariant Violation: Could not find `store` in either the context or props of `connect(CommentBox)`.
Either wrap the root component in a `<Provider>`, or explicitly pass `store` as a prop to `connect(CommentBox)`.

TypeError: Cannot read property '`map`' of undefined.
Because `axios` fails in command line environment, then use `moxios`.

For mock API, [Json Placeholder](http://jsonplaceholder.typicode.com/) is free to ues.
