# React Class Components

Create a react class syntax:

```jsx
import React, { Component } from "react";

class Application extends Component {
 render() {
  return <div></div>;
 }
}
```

Compared to functional hook:

```jsx
import React, { Component } from "react";

function Application(props) {
  return <div></div>;
}
```

Useful documentations:

- [React.Component](https://reactjs.org/docs/react-component.html)
- [State and Lifecycle](https://reactjs.org/docs/state-and-lifecycle.html)
- [Component State](https://reactjs.org/docs/faq-state.html)

Pass a onClick function as a props and handling the function over the child component

Vs.

Handle the onclick function at the root compoent and then pass everything to the child compoennt

Example:

```jsx
<Panel
key={panel.id}
id={panel.id}
label={panel.label}
value={panel.value}
onSelect={this.selectPanel}
/>

class Panel extends Component {
  render() {
    const { label, value, id, onSelect } = this.props;

    return (
      <section
        className="dashboard__panel" onClick={onSelect(id)}
      >
        <h1 className="dashboard__panel-header">{label}</h1>
        <p className="dashboard__panel-value">{value}</p>
      </section>
    );
  }
}
```

```jsx
<Panel
key={panel.id}
label={panel.label}
value={panel.value}
onSelect={event => this.selectPanel(panel.id)}
/>

class Panel extends Component {
 render() {
  const { label, value, onSelect } = this.props;

  return (
   <section className="dashboard__panel" onClick={onSelect}>
    <h1 className="dashboard__panel-header">{label}</h1>
    <p className="dashboard__panel-value">{value}</p>
   </section>
  );
 }
}
```

## How to handle this in react:

Read the [React Binding Patterns: 5 Approaches for Handling this](https://medium.com/free-code-camp/react-binding-patterns-5-approaches-for-handling-this-92c651b5af56) article by Cory House.

A lot of useful Links for React, JS, Test, Job, Connections...

[https://web.compass.lighthouselabs.ca/days/w08d4/activities/1084](https://web.compass.lighthouselabs.ca/days/w08d4/activities/1084)