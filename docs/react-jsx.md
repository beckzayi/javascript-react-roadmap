# JSX

React is a library for creating and updating HTML elements. `ReactDOM.render()` is the function that actaully does the creating and updating. It takes a React Element object that describes that to render, and uses this to update the DOM node that's passed in as the second argument.
The "elements" that `React.createElement()` returns are actually plain old JavaScript objects that describe the element that you'd like `ReactDOM.render()` to create. It might help to think of React Elements as configuration objects for `ReactDOM.render()`.


There are three properties of a React Element:

`type`: what type of HTML element to use. For example 'div'.

`props`: the attributes on the element. For example, the style prop.

`children`: specify the element's content; it can contain a string, another React Element, or an array (containing strings or React Elements)

JSX with ES2015:
```jsx
const App = (props) => {
    var myStyle = { backgroundColor: '#000' };
    return (
        <div style={myStyle}>
            <a></a>
            <a href="#" onClick={update}>
                This is the TEXT // this is essentially this.props.children
                {i > 1 ? 'More than one' : 'one'}
            </a>
        </div>
    )
}
```

JavaScrpt tranpiled by Babel:
```javascript
"use strict";
var App = function App(props) {
    var myStyle = { backgroundColor: '#000' };
    return React.createElement(
        "div",
        { style: myStyle }, // the props of the div
        React.createElement("a", null),
        React.createElement(
            "a", 
            { href: "#", onClick: update },
            "This is the TEXT",
            I > 1 ? 'More than one' : 'one'
        )
    );
}
```
