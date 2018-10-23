## Code Splitting

Scenario: we don't want to load the whole giant bundle.js on every route. For example, if on PageAbout, only load PageAbout component js, don't load PageContact js.

A package called `react-loadable` makes this easier to implement.

`npm install --save react-loadable`

Below is just a simple example.
```jsx
import Loadable from 'react-loadable';

const Loading = () => {
    return <div>Loading</div>;
}

const PageAbout = Loadable({
    loader: import('./components/PageAbout'),
    loading: Loading
});

const PageContact = Loadable({
    loader: import('./components/PageContact'),
    loading: Loading
});

export default class App extends React.Component {
    render() {
        // if (route === 'pageabout')
        // return <PageAbout />

        // if (route === 'pagecontact')
        // return <PageContact />
    }
}
```
