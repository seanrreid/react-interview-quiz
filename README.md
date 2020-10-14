# React JS Quiz

#### Sourced from https://ui.dev/react-interview-questions/ & https://www.sitepoint.com/react-interview-questions-solutions/

### What is React?

<details>
<summary><b>Answer</b></summary>
<p>
React is an open-source JavaScript library created by Facebook for building complex, interactive UIs in web and mobile applications.

The key point in this answer is that React’s core purpose is to build UI components;it is often referred to as just the “V” (View) in an “MVC” architecture. Therefore it has no opinions on the other pieces of your technology stack and can be seamlessly integrated into any application.
</p>
</details>

---

### How is React different from other Javascript frameworks?

<details>
<summary><b>Answer</b></summary>
<p>
React is a small library focused on building UI components.

By comparison, AngularJS (1.x) approaches building an application by extending HTML markup and injecting various constructs (e.g. Directives, Controllers, Services) at runtime. As a result, AngularJS is very opinionated about the greater architecture of your application.

By contrast, React focuses exclusively on the creation of components, and has few (if any) opinions about an application’s architecture. This allows a developer an incredible amount of flexibility in choosing the architecture they deem “best” — though it also places the responsibility of choosing (or building) those parts on the developer.
</p>
</details>

_Note:_ There are likely _many_ answers to this question. Most will depend on experiences with other frameworks.

---

### What is JSX?

<details>
<summary><b>Answer</b></summary>
<p>
JSX, aka 'JavaScript eXtension' is XML like syntax developed for use in React. It allows developers to write Javascript that <em>looks</em> like HTML. JSX code by itself cannot be read by the browser; it must be transpiled into traditional JavaScript using tools like Babel and webpack.
</p>

The following in JSX:

```jsx
<div className="container" />
```

Is translated to this in Javascript:

```javascript
React.createElement(
  'div',
  {className: 'container'}
)
```

#### Key Talking Points

* Developers do not have to use JSX (and ES2015) to write an application in React.
* Having said that, many React developers prefer to use JSX as its syntax is far more declarative and reduces overall code complexity. Facebook certainly encourages it in all of their documentation!
* Adopting JSX allows the developer to simultaneously adopt ES2015 — giving immediate access to some wonderful syntactic sugar.
</details>

---

### What is the virtual DOM?

<details>
<summary><b>Answer</b></summary>
<p>

> The virtual DOM is an in-memory representation of the actual HTML elements that make up your application’s UI. When a component is re-rendered, the virtual DOM compares the changes to its model of the DOM in order to create a list of updates to be applied. The main advantage is that it’s highly efficient, only making the minimum necessary changes to the actual DOM, rather than having to re-render large chunks.

</p>
</details>

---

### What is the difference between a state and a prop?

<details>
<summary><b>Answer</b></summary>
<p>

>In a React component, props are variables passed to it by its parent component. State on the other hand is a variable, but directly initialized and managed by the component.
>
> The state can be initialized by props.

More Reading: [https://flaviocopes.com/react-state-vs-props/](https://flaviocopes.com/react-state-vs-props/)

</p>
</details>

---

### What is a functional component?

<details>
<summary><b>Answer</b></summary>
<p>

A functional, component is _just_ a Javascript function that can receive props and return a React element.

In general, they're usually somewhat more performant than a Class based component because they return simple UI.

</p>

```jsx
const myGreetingComponent = props => {
    return (
        <div>
            <h1>Hello {props.name}</h1>
        </div>
    )
}
```

#### Note:
Prior to React 16.8, functional components were _stateless_, and did not have any lifecycle methods.

With the introduction of Hooks, functional components are now able to access state (`useState`) and have similar functionality to lifecycle methods (`useEffect`).

</details>

---

### What happens during the lifecycle of a React component?

<details>
<summary><b>Answer</b></summary>
<p>

> At the highest level, React components have lifecycle events that fall into three general categories:
>
> * Initialization
> * State/Property Updates
> * Destruction
>
> Every React component defines these events as a mechanism for managing its properties, state, and rendered output. Some of these events only happen once, others happen more frequently; understanding these three general categories should help you clearly visualize when certain logic needs to be applied.

</p>

> `componentDidMount()`: Called after the first render; the component’s DOM element is now available

> `componentWillUnmount()`: Called before the component is removed from the DOM, allowing you to clean up things like event listeners.

In functional components, the `useEffect` Hook gives us similar functionalty to these lifecycle methods.

</details>

---

### What is the purpose of "key" in React?

<details>
<summary><b>Answer</b></summary>
<p>

Keys are what help React keep track of what items have changed, been added, or been removed from a list.

</p>
</details>

---

### What happens when you call setState?

<details>
<summary><b>Answer</b></summary>
<p>

> The first thing React will do when setState is called is merge the object you passed into setState into the current state of the component.

> This will kick off a process called reconciliation. The end goal of reconciliation is to, in the most efficient way possible, update the UI based on this new state.

> To do this, React will construct a new tree of React elements (which you can think of as an object representation of your UI). Once it has this tree, in order to figure out how the UI should change in response to the new state, React will diff (`diff`: check the differences of) this new tree against the previous element tree.

> By doing this, React will then know the exact changes which occurred, and by knowing exactly what changes occurred, will able to minimize its footprint on the UI by only making updates where absolutely necessary.

</p>
</details>

---

### Why call `setState` instead of directly mutating state?

<details>
<summary><b>Answer</b></summary>
<p>

> If you try to mutate a component’s state directly, React has no way of knowing that it needs to re-render the component. By using the setState() method, React can update the component’s UI.

> [S]tate updates are not guaranteed to be synchronous. If you need to update a component’s state based on another piece of state (or props), pass a function to setState() that takes state and props as its two arguments:

```jsx
this.setState((state, props) => ({
  counter: state.counter + props.increment
}));
```

_Note:_ The above example is not as common, but is handy to know.

</p>
</details>

---

### What is meant by "Data is passed down"?

<details>
<summary><b>Answer</b></summary>
<p>

React has _one-way_  data binding.  Specifically, React's UI is changed based on changes to the data model. The changes move from the model, it is the single source of truth.

By comparison, two-way data binding means that the model changes with the UI, and vice-versa.

One-way data binding means that data is always moving in one direction. This flow is more predictable, with has fewer side effects.

Common React data flow patterns are:

* Parent -> Child
* Child -> Parent (using callbacks)
* Between siblings (messy, but possible).

More Reading: [https://medium.com/@lizdenhup/understanding-unidirectional-data-flow-in-react-3e3524c09d8e](https://medium.com/@lizdenhup/understanding-unidirectional-data-flow-in-react-3e3524c09d8e)

</p>
</details>

---

### What does `create-react-app` do?

<details>
<summary><b>Answer</b></summary>
<p>

Per the [docs](https://facebook.github.io/create-react-app/docs/getting-started)

> Create React App is an officially supported way to create single-page React applications. It offers a modern build setup with no configuration.

Using `create-react-app` will quickly scaffold out a React application with all the basic libraries, folder structure, and scripts that you need to get a React application up and running quickly.

</p>
</details>

### What’s the difference between a controlled and an uncontrolled component?

<details>
<summary><b>Answer</b></summary>
<p>

(emphasis added)

> In an HTML document, many form elements (e.g. `<select>`, `<textarea>`, `<input>`) maintain their own state. An **uncontrolled component** treats the DOM as the source of truth for the state of these inputs.
>
> In a **controlled component**, the internal state is used to keep track of the element value. When the value of the input changes, React re-renders the input.

</p>
</details>

---

## BONUS

### What’s the difference between an Element and a Component in React?

<details>
<summary><b>Answer</b></summary>
<p>

> A React _element_ describes what you want to see on the screen. It is an object representation of some UI.
>
> A React _component_ is a function or a class which optionally accepts input and returns a React element (typically via JSX which gets transpiled to a createElement invocation).

</p>
</details>

---

### What is the purpose of "refs" in React?

<details>
<summary><b>Answer</b></summary>
<p>

> Refs allow direct access to a DOM element or an instance of a component.

> In order to use them you add a ref attribute to your component whose value is a callback function which will receive the underlying DOM element or the mounted instance of the component as its first argument.

</p>
</details>

---

### What is a higher order component in React?

<details>
<summary><b>Answer</b></summary>
<p>

> A higher-order component (HOC) is an advanced technique in React for reusing component logic. HOCs are not part of the React API, per se. They are a pattern that emerges from React’s compositional nature.
>
> Concretely, a higher-order component is a function that takes a component and returns a new component.

React Docs: [https://reactjs.org/docs/higher-order-components.html](https://reactjs.org/docs/higher-order-components.html)

</p>
</details>

---

### Is anything wrong with this code?

```
this.setState((prevState, props) => {
    return {
        streak: prevState.streak + props.count
    }
})
```

<details>
<summary><b>Answer</b></summary>
<p>

"Nothing is wrong with it 🙂.

It’s rarely used and not well known, but you can also pass a function to `setState` that receives the previous state and props and returns a new state, just as we’re doing above.

This is actually recommended if you’re setting state based on previous state." - Tyler McGinnis

</p>
</details>
