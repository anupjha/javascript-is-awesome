#### Parent to Child — Use Prop
```javascript
class App extends React.Component {
render() {
  // somewhere in here I define a variable listName which I think will be useful as data in my ToDoList component...
  return (
    <div>
      <InputBar/>
      <ToDoList listNameFromParent={listName}/>
    </div>
  );
  }
}
```

#### Child to Parent — Use a callback and states

Define a callback in my parent which takes the data I need in as a parameter.
Pass that callback as a prop to the child (see above).
Call the callback using this.props.[callback] in the child (insert your own name where it says [callback] of course), and pass in the data as the argument.
```javascript
class ToDoList extends React.Component {          myCallback = (dataFromChild) => {
   // we will use the dataFromChild here...
  },
  render() {
    return (
      <div>
        <ToDoItem callbackFromParent={this.myCallback}/>
      </div>
    );
  }
}
```
Now from within ToDoItem we can pass something to callbackFromParent:
```javascript
class ToDoItem extends React.Component{           someFn = () => {
  // somewhere in here I define a variable listInfo which    I think will be useful as data in my ToDoList component...]        this.props.callbackFromParent(listInfo);
  };
  render() {
    // Do something
    }
};
```

But what if I want to use listInfo in a different function within ToDoList, not just in myCallback?
```javascript
class ToDoList extends React.Component {
constructor(props) {
    super(props);
    this.state = {
        listDataFromChild: null
    };
  }
  myCallback = (dataFromChild) => {
      this.setState({ listDataFromChild: dataFromChild });
  }
  otherFn = () => {
    // within this other function now I still have access to this.state.listDataFromChild...]
    }

 render() {
  return (
      <div>
          <ToDoItem callbackFromParent={this.myCallback}/>
  // now here I can pass this.state.listDataFromChild as a prop to any other child component...
    </div>
  );
}
};
```