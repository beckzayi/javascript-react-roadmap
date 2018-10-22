##  Presentational Components

Presentational components are written as functional components unless they need state, lifecyle hooks, or performance optimizations.

A functional component using an ES2015 (ES6) arrow function:
```javascript
var Aquarium = (props) => {
  var fish = getFish(props.species);
  return <Tank>{ fish }</Tank>;
};
```

Or with destructuring and an implicit return, simply:
```javascript
var Aquarium = ({species}) => (
  <Tank>
    { getFish(species) }
  </Tank>
);
```
Then use this component: 
```javascript
<Aquarium species="rainbowfish" />
```

These components behave just like a React class with only a render method defined. This pattern is designed to encourage the creation of these simple components that should comprise large portions of your apps.

For more details, check out the [post](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0) from Redux's author.