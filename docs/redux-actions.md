## How Actions work

Actions are plain JavaScript objects.
```javascript
const addUser = (user) => {
    return {
        type: 'ADD_USER',
        payload: user
    }
}
```

To handle AJAX responses, we have another way to trigger action creators.
Redux passes `dispatch` method to the inner function, and dispatch it to reducer. In this case, `redux-thunk` middleware may be used.
```javascript
const api_url = `http://api.com/users`;
const showUser = (id) => {
    return (dispatch) => {
        axios.get(`${api_url}/${id}`).
            .then(response => {
                dispatch(
                    type: 'SHOW_USER',
                    payload: response.data
                );
            });
    };
}
```