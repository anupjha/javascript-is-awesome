#### All prop-types
```javascript
ComponentName.propTypes = {
  string: PropTypes.string,
  number: PropTypes.number,
  boolean: PropTypes.bool,
  array: PropTypes.array,
  arrayOfType: PropTypes.arrayOf(PropTypes.string),
  object: PropTypes.shape,
  objectOfShape: PropTypes.shape({
    name: PropTypes.string,
    age: PropTypes.number
  }),
  instanceOfClass: PropTypes.instanceOf(Message),
  method: PropTypes.func,
  anyType: PropTypes.any,
  direction: PropTypes.oneOf(['left', 'right']) // Enumerable
  requiredProp: PropTypes.string.isRequired,   // any type can be marked required
  node: PropTypes.node,  // anything that can be rendered is a node
  reactElement: PropTypes.element  // => Eg. children
};
```
#### Custom validation
```javascript
MyCo.propTypes = {
  customProp: (props, key, componentName) => {
    if (!/matchme/.test(props[key])) {
      return new Error('Validation failed!')
    }
  }
}
```