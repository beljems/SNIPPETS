# REACT HOOKS

### Example
```sh
class App extends React.Component {
  state = {
    test: 1,
    test2: 1
  };

  /*   // props or state is changed
  componentDidUpdate() {
    console.log('updated app');
  }
   */
  render() {
    if (this.state.test < 5) {
      return (
        <div>
          <App3 test={this.state.test} test2={this.state.test2} />
          <button onClick={() => this.setState({ test: this.state.test + 1 })}>
            Click
          </button>
          <button
            onClick={() => this.setState({ test2: this.state.test2 + 1 })}
          >
            Click 2
          </button>
        </div>
      );
    } else {
      // componentDidUnmount
      return <div>Done</div>;
    }
  }
}```

### Class Component

```sh
class App2 extends React.Component {
  // component is added to DOM
  componentDidMount() {
    console.log("mounted");
  }

  // props or state is changed
  componentDidUpdate(oldProps, newProps) {
    console.log("updated");
  }

  // component is removed from DOM
  componentWillUnmount() {
    console.log("unmount");
  }

  render() {
    return <div>Test 2</div>;
  }
}```

### Functional Component
```sh
function App3(props) {
  // componentDidMount
  React.useEffect(() => {
    console.log("mount");

    function handleClick() {}
    document.querySelector("button").addEventListener("click", handleClick);

    return function () {
      document
        .querySelector("button")
        .removeEventListener("click", handleClick);
      console.log("unmounted");
    };
  }, []);

  // componentDidUpdate
  // use React. if no import React, { useEffect } from 'react'
  React.useEffect(() => {
    console.log("updated test");
  }, [props.test]);

  React.useEffect(() => {
    console.log("updated test2");
  }, [props.test2]);

  React.useEffect(() => {
    console.log("updated test 1 + 2");
  }, [props.test, props.test2]);

  // componentWillUnmount
  React.useEffect(() => {
    return function () {
      console.log("unmounted");
    };
  }, []);

  return <div>Test 3</div>;
}

ReactDOM.render(<App />, document.querySelector("#app"));```
