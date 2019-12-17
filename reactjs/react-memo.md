#### `React.memo` gives us the ability of pure components in React but for functional based components rather than class based ones.

Memoization is computer science jargon which means caching the result of expensive function calls and returning the cached version when the arguments are the same.

##### In React terms:
We don’t want MyNewComponent re-rendering when the props being passed are the same.

Example:

Imagine the Banner is a UI component that can have different types, in this case you want to use the info type banner so you create your Banner as follows:

```javascript
<Banner type="info" />
Our CounterComponent looks like this:

class CounterComponent extends Component {
  state = { buttonPressedCount: 0 };
  render() {
    const { buttonPressedCount } = this.state;
    return (
      <div className="new-component">
        <h4>Button Pressed Count: {buttonPressedCount}</h4>
        <button
          onClick={() =>
            this.setState({ buttonPressedCount: buttonPressedCount + 1 })
          }
        >
          Increase Count
        </button>
        <Banner type="info" />
      </div>
    );
  }
}
```
And our Banner component looks as follows:
```javascript
const Banner = props => {
  const { type } = props;

  if (type === "info") {
    return <div className="info-banner">I am an info banner</div>;
  }
};
```
In our CounterComponent, every time we click the button we increase the buttonPressedCount variable which causes a re-render which is what you would expect. The problem with this is that the Banner component also re-renders even though the props being passed to it haven’t changed.

To circumvent this, we use memo which acts like PureComponent in the fact that it will stop re-renders when the props haven’t changed. Our code updated looks like:

```javascript
const Banner = memo(props => {
  const { type } = props;

  if (type === "info") {
    return <div className="info-banner">I am an info banner</div>;
  }
});
```
Now our Banner component will only re-render when the props to it have changed.

This is core fundamental idea of React memo.

#### areEqual
By default, memo only does a shallow comparison of props and prop’s objects. You can pass a second argument to indicate a custom equality check:

`React.memo(Component, [areEqual(prevProps, nextProps)]);`

This is similar to `shouldComponentUpdate` but the inverse i.e. returning true in shouldComponentUpdate causes another render whereas areEqual is the opposite.

Imagine we had a Person component that accepted a prop person which is an object, we could check if the name is the same.

```javascript
const areEqual = (prevProps, nextProps) => {
  return (prevProps.name === nextProps.name)
};
React.memo(Person, areEqual);
```