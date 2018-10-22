## Higher Order Component

We can treat Higher Order Component as a component factory. Add a component (argument) to the factory, and the factory returns a component based on the component (argument) we add earlier. The new return component will have some additional properties.

```jsx
const WithCount = (WrappedComponent) => {
    class extends React.Component {
        state = { count: 0 };
        increment = () => {
            this.setState(state => ({
                count: state.count + 1
            }));
        }

        render() {
            return (
               <WrappedComponent
                    count={this.state.count}
                    onIncrement={this.increment}
                    {...this.props}
               /> 
            );
        }
    }
};
```
