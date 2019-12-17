##### With the introduction of React 16, we can now return multiple children elements in a component’s render method using an array of components, elements and/or strings. For example, this is now valid syntax as of React 16:
```javascript
class App extends Component {
  render() {
    return [
      <Card key="1" />,
      'Just a text node',
      <Card key="2" title="Hello" content="I'm just a card in the world" />
    ];
  }
}
```
##### And this works just a well in stateless functional components (SFCs):
```javascript
const App = () => {
  return [
    <Card key="1" />,
    'Just a text node',
    <Card key="2" title="Hello" content="I'm just a card in the world" />
  ];
};
```
The problem is that the syntax using an array is a little bit awkward, and we need to add a unique key to elements. The solution, which was introduced with React 16.2, is to make use of React Fragments.

Using the `Fragment component`, we can now accomplish the same without the array syntax and without using keys. Just use the React.Fragment component to wrap your returned elements:

```javascript
import React, { Component } from 'react';

class App extends Component {
  render() {
    return (
      <React.Fragment>
        <Card />
        Just a text node
        <Card title="Hello" content="I'm just a card in the world" />
      </React.Fragment>
    );
  }
}
```
We can make the syntax more concise by importing the Fragment component directly:

```javascript
import React, { Component, Fragment } from 'react';

class App extends Component {
  render() {
    return (
      <Fragment>
        <Card />
        Just a text node
        <Card title="Hello" content="I'm just a card in the world" />
      </Fragment>
    );
  }
}
````
##### <> </> Shorthand Syntax
You can achieve the paramount of conciseness by using the new <> </> shorthand syntax:
```javascript
import React, { Component } from 'react';

class App extends Component {
  render() {
    return (
      <>
        <Card />
        Just a text node
        <Card title="Hello" content="I'm just a card in the world" />
      </>
    );
  }
}
```
##### Notes:
Use React.Fragment, to avoid `side effects` of `<div>` element.

Babel 7, which is still in beta at the time of this writing, is needed for this shorthand syntax to be properly transpiled to the <React.Fragment> equivalent.


