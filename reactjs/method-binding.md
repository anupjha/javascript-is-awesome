### Bind during render(ES5 approach)
```javascript
// define method
handleChange(e) {
  // e is the event
}

// and call as
onChange = { this.handleChange.bind(this) }
```
### Bind in constructor(ES5 approach)
```javascript
constructor(props) {
  super(props);
  this.handleChange = this.handleChange.bind(this);
}

// define method
handleChange() { }

// and call as
onChange = { this.handleChange }
```
### Use arrow function in render(ES6 approach)
```javascript
// define method
handleChange(e) {
  // e is the event
}

// and call as
onChange = { e => this.handleChange(e) }
```
### Use arrow function while defining method(ES6 approach - recommended)
This is ES6 stage - 2 feature, so you might need to enable`transform-class-properties` in babel.
```javascript
  // define method
  handleChange = () => {
    // call this function from render
    // and this.whatever in here works fine.
  };

// and call as
onChange = { this.handleChange }
```
```
<button onClick = {(e) => this.deleteRow(id, e)}> Delete Row</button >
<button onClick={this.deleteRow.bind(this, id)}>Delete Row</button>
// The above two lines are equivalent, and use arrow functions and function.prototype.bind respectively.
< button onClick = {(e) => console.log(‘Button Clicked'}>Delete Row</button>
```