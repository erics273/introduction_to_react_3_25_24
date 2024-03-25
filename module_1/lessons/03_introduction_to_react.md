# Introduction to React

React's component-based architecture makes composing applications straightforward and easy. Components are easily compartmentalized along with the styles and resources unique to each component. Components can render static content that is included in the render function and can render dynamic content that is passed to the component via props. Additionally, components can manage internal local state and update that state based on internal logic.

The primary difference between React and other frameworks is that React is designed to re-render the entirety of the application any time any state changes, similar to a full page refresh. React organizes everything that needs to be displayed using Components.

- [React Official Site](https://reactjs.org)   
- [React Documentation](https://reactjs.org/docs/getting-started.html)  

## What is JSX?
JSX is a syntax extension to JavaScript and is intended to be a straightforward way of describing the UI for React applications. Each JSX element is just syntactic sugar for calling [React.createElement()](https://reactjs.org/docs/react-without-jsx.html). In some ways, JSX looks like HTML with a little JavaScript sprinkled in, but you should think of it as a JavaScript expression that will be evaluated and output HTML. JSX may remind you of a template language, but it comes with the full power of JavaScript.

The following section will outline the most important details about JSX. To read more about the power of JSX, read the [JSX Docs](https://facebook.github.io/react/docs/introducing-jsx.html).

> NOTE: Since JSX is closer to JavaScript than HTML, React DOM uses camelCase property naming convention instead of HTML attribute names. For example, "class" is "className" in JSX, and "tabindex" is "tabIndex". This little change trips up a lot of beginners, so keep it in mind when defining props.

The following JSX expression includes a parent `div` element and a child `h1`. This means that whenever this variable is included in the application, it will always render those elements. 

```javascript
  const element = <div><h1>Hello, world!</h1></div>;
```
Curly braces `{}` allow us to embed and evaluate any JavaScript expression. That being said, `{}` can render *any* expression. 

The following code will display **5 + 5 = 10**: 
```javascript
  const element = <div>5 + 5 = {5 + 5}</div>;
```

The following code will display **Hello, Eric!**: 
```javascript
  const name = "Eric"
  const element = <div><h1>Hello, {name}!</h1></div>;
```

The point of this discussion is that nothing magical is happening within `{}`. Any JavaScript expression is valid.

JSX is optional when it comes to React. When using JSX you need to use a third party library like babel to compile the JSX into the appropriate [React.createElement()](https://reactjs.org/docs/react-without-jsx.html) calls. Although you can use React without JSX it is not common and JSX does provide some nice features. It can prevent injection attacks by escaping any values embedded in JSX before rendering them and it also allows React to show more useful error and warning messages.

Some basic rules to keep in mind

 * All JSX tags must be closed ```<div></div>```. 
 * If a tag would be empty or wouldn't have a closing tag, like ```<img>``` then you close it with ```/>```
 * You may only have one parent tag per JSX expression


 JSX is rendered to the screen using [ReactDOM.render()](https://reactjs.org/docs/react-dom.html#render). This Renders a React element (JSX) into the DOM in the specified container, in this case, some element with the "id" attribute of "root"

 ```javascript
    ReactDOM.render(
        <h1>Hello, world!</h1>,
        document.getElementById('root')
    );
```

This is the same code but with [React.createElement()](https://reactjs.org/docs/react-without-jsx.html)
```javascript
    ReactDOM.render(
        React.createElement('h1',{},'Hello, world!'),
        document.getElementById('root')
    );
```

### Example: Simple React application rendering a JSX expression
The following code is a bare minimum example that uses [ReactDOM.render()](https://reactjs.org/docs/react-dom.html#render) to render a simple JSX expression into the specified container on an HTML page.

index.html
```html

    <!DOCTYPE html>
    <html lang="en">

    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>Document</title>
    </head>

    <body>
        
        <!-- element where application will be rendered -->
        <div id="root"></div>
        
        <!-- include React and ReactDOM -->
        <script crossorigin src="https://unpkg.com/react@18/umd/react.development.js"></script>
        <script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>

        <!-- include Babel standalone so we can process JSX -->
        <script crossorigin src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
    
        
        <!-- Render a JSX expression into the <div> with id="root" -->
        <script type="text/babel">

            const root = ReactDOM.createRoot(document.getElementById('root'));
            
            root.render(
                <div>
                    <h1>Hello, world!</h1>
                </div>
            )
        </script>
    </body>

    </html>

```


## React Components
Components in React represent reusable UI components. Components take inputs called "props" and return react elements that describe what the user should see on in the browser. Components can be defined as Functions or as Classes and to React, there isn't much difference between how it treats either type. You do get some extra functionality with components defined as classes that you will want to leverage in some cases.

### Defining components as functions
Simple "pure" functions are the simplest way to create a component in React. By pure we mean that the function does not modify its inputs and always returns the same output for the given inputs. Consider the following example:

```javascript
  function Welcome(props) {
    return <h1>Hello, Eric!</h1>
  }
```
This function is a valid React component because it accepts a single property called "props" which is an object. These "function components" are literally just JavaScript functions.

### Class Components
Class components in react provide you with some additional features you don't get when components with simple functions without the use of hooks.Until hooks like `useEffect` and `useState` came about, use class components where the only way to gain access to some of the most powerful featurs in react components.

Features of Class components
* **State** - This is why functional components are were also called stateless before the `useState` hook gave us the ability to leverage statin in fumnctional components. Class components can maintain their own state. State is similar to props, but it is private and fully controlled by the component. State allows React components to change their output over time in response to user actions, network responses, and anything else, without having to modify props.
* **Lifecycle Hooks** - Lifecycle hooks are methods provided to you through extending the React.Component class. They allow you to run code at various points in the lifecycle of the application. [componentDidMount()](https://reactjs.org/docs/react-component.html#componentdidmount) and [componentWillUnmount()](https://reactjs.org/docs/react-component.html#componentwillunmount) are some commonly used lifecycle hooks. Please follow the links to learn more about those and the other Lifecycle Hooks.
We use the `useEffect` hook in function components in place of the lifecyle hooks available in class components.

Both examples below are considered the same in React. The Class component allows you to leverage state and lifecycle hooks.
```javascript
    //FUNCTIONAL COMPONENT
    function Potato(props) {
        return <h1>My favorite type of potato is, {props.type}</h1>;
    }

    //CLASS COMPONENT
    class Potato extends React.Component {
        render() {
            return <h1>My favorite type of potato is, {this.props.type}</h1>;
        }
    }
```
 
What changed?
1. We declared a Class called Potato instead of creating a function called Potato making sure to extend React.Component so we inherit what we need to work with State and Lifecycle Hooks.
2. We implemented the ```render()``` method and moved the body of the functional component into the ```render``` method of the stateful component

## Working with Props
Components accept arbitrary inputs (called “props”) and can use the props to help shape the output delivered to the UI. Props are passed in as JSX attributes to the component and treated as a single object inside the component. 

```javascript
    //functional component using props.*
    function OnePotato(props) {
        return <h1>{props.name} loves {props.type} potatos!</h1>;
    }

    //class component using this.props.*
    class TwoPotato extends React.Component {
        render() {
            return <h1>{this.props.name} loves {this.props.type} potatos!</h1>;
        }
    }

    //the attributes passed in when rendering the components become part of the props object inside the component
    ReactDOM.render(
        <div>
            <OnePotato name="Eric" type="Yukon Gold"/>
            <TwoPotato name="Susan" type="French Fried"/>
        </div>,
        document.getElementById('root')
    );

```

You can also pass ```objects```, ```functions```, and other types of data other than strings as the value for your props. You may pass something from the components state into a child component as a prop or even a callback function to facilitate child to parent communication. The [Passing Data Between React Components](https://medium.com/@ruthmpardee/passing-data-between-react-components-103ad82ebd17) article on medium does a good job of explaining this topic.

Take some time to ***Learn On Your Own!*** out the [Spread Operator ...](https://reactjs.org/docs/jsx-in-depth.html#spread-attributes) to learn more about how you can pass props into a component. 

> NOTE: A Component must never modify its own props. React is pretty flexible but it has a single strict rule: **All React components must act like pure functions with respect to their props.**

## Working with State
State is created and managed within a component and not passed in as attributes when rendered through JSX like props. You should think of State as private to a component. Perhaps the most special thing about State is that a change/update to state will cause the application to re-render.

[Further Reading](https://reactjs.org/docs/faq-state.html)
[useState hook documentation](https://react.dev/reference/react/useState) 

Putting data in the state of a component is usually needed when portions of your UI rely on values in state. This is done in the `constructor()` method of a class component or by using the `useState` hook in a function component.

The start of a simple counter
```javascript

function Counter (props) {

    /*
    using the useState hook to create our initial coung in state
    */
    const [count, setCount] = React.useState(0);

    //return JSX displaying the count
    return (
        <div>
            {count}
        </div>
    )

}

```

> NOTE: `useState` returns an array with 2 values. The first value is the current state which matches the `initialState` passed to `useState`. In this case `0`. The second value is a set function used to update the value in state. We use a feature called destructing assignment to assign the  returned values to their own variables.

If you review the comments in the code example above hopefully, you will come to the conclusion that this component will display ```0```. That's cool but it's not a counter. The point is we have a **State** with something in it called **count** and we are leveraging **count** in the JSX returned from the component.

What if we want the counter to change? We would need to update our state. Since the value that is displayed for the counter is in state, we need to update its value in state. When we update its value in state it will cause our application to re-render.

When updating state you must use set function returned `useState`. In this case we wille be using `setCount`

```javascript

    setCount(10);

```

But where and when do we call ```setCount()```? We usually change state in response to some type of event. 

## Event Handling
Events can be lots of things. User interaction can trigger all types of events from mouse clicks to button clicks. We handle these events with Event Handlers. Event Handlers are typically methods on your Class (Stateful) Component. 

[Further Reading](https://reactjs.org/docs/handling-events.html) on event handling.

Take a look at what an **Event Handler** would look like on our Counter Component to increment our **count** in state.

```javascript

function Counter (props) {

    //new increment handler to update state 
    //setting count to be 1 greater than it's previous value
    let incrementHandler = (event) => {
        setCount(count + 1);
    }

    return (
        <div>
            {count}
        </div>
    )
    

}

```

Now that we have a handler for an event let's create an onClick event. We want the user to click a button and ```onClick``` call the ```incrementHandler()```.

```javascript

function Counter (props) {

    let incrementHandler = (event) => {
        setCount(count + 1);
    }

    return (
        <div>
            {count}
            {/* button with onClick that calls the incrementHandler method on this class */}
            <button onClick={incrementHandler}>increment (+)</button>
        </div>
    )

}

```
* When the **increment (+)** button is clicked it will call the ```incrementHandler()``` method.
* The ```incrementHandler()``` is updating state using `setCount()` updating the value of **count** in state by adding 1 to its current value.
* Because state is updated the application will re-render and display the updated value of ```count``` to the user. 
* This process is repeated with every press of the **increment (+)** button.

# Class Exercise
Take some time to complete the following tasks.
* If you didn't build the counter during the lecture, go ahead and see if you can get the counter working
* Create a decerment button that decreases the counter everytime it is clicked
* Modify the functionality to not allow the counter to go below 0
* Modify the functionality to not allow the counter to go above 20
* Modify the functionality to change the color of the counter to red if it goes above 10
    * https://reactjs.org/docs/faq-styling.html
    * Make when it goes back below 10 it changes back to the original color
* Modify the functionality to allow an initial count to be passed in as a prop
    * if an initial count is not passed in, the count should start at 0
* Add a button to reset the counter to 0 or whatever the initial count was set to when passed in as a prop
* Only show this button if the counter has been modified from its original state.
