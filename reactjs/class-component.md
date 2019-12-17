#### With constructor

```javascript
import React from 'react';
import PropTypes from 'prop-types';
class ComponentName extends React.Component {
  constructor(props) {
    super(props);
  }
  componentDidMount() {
    // do what you want after component mount
    // good place to add event listeners
  }
  componentWillUnmount() {
    // do what you want after component unmounts
    // don't forget to remove event listeners here
  }
  render() {
    const { name } = this.props;
    return (
      <div>Hello, {name}</div>;
    );
  }

  ComponentName.propTypes = {
    name: PropTypes.string
  };
  ComponentName.defaultProps = {
    name: 'John'
  };
}
export default ComponentName;
```
#### Without constructor
```javascript
class ComponentName extends React.Component {
static propTypes = {
name: PropTypes.string.isRequired,,
}

static defaultProps = {
name: 'John',
}

state= {};
render() {
    const { name } = this.props;
    const { xyz } = this.state;
    return (
      <div>Hello, {name}</div>;
    );
  }
```