# Create a Simple Application using create-react-app
In this guided exercise, we will build a simple application with 4 components. We will have the default App component provided by create-react-app as well as a Welcome, Clock, and Contact component. The Welcome component will be stateless and deal with a single prop. The Clock component will be stateful and leverage lifecycle hooks. The Contact component will work with user input.

## Scaffold project with create-react-app
First, we will need to scaffold our project using create-react

* Open your terminal to a directory you want to create your project in and run the following command:

```bash
  $ npx create-react-app react-demo-app
```

* Then open the react-demo-app project folder created in VSCode or your editor of choice

## Create A Welcome Component
The following example demonstrates how to create a simple component that relies on 1 "prop" and then how to include that component in our application.

> Always start component names with a capital letter.
For example, `<div />` represents a DOM tag, but `<Welcome />` represents a component in JSX.

1. Within the *src* directory, create a new directory called *components*
2. Within *src/components*, create a directory called *welcome*.
3. Within *src/components/welcome*, create *Welcome.js*

### Welcome.js

```javascript

function Welcome(props) {

    return (
        <div>
            <h1>Hello, {props.name}!</h1>
        </div>
    );
}

export default Welcome;
```

- To create the `Welcome` component, we create a simple JavaScript function that takes "props" as its argument. Whenever a component is rendered, the application will render the returned JSX expression.
- Notice the line that includes **{props.name}**? That will be replaced with the value of the "name" prop passed into the component.

## Including the Welcome Component in the main component, App.js
We want to use our welcome component to greet our visitors. Let's include our component in the App.js where we would like it to display

1. Import the Welcome component at the top of `App.js`
  ```javascript
  import Welcome from './components/welcome/Welcome';
  ```

2. Add the Welcome component where we want it to show up and then set the name property. The Welcome component consumes the name property and then outputs the name using **{props.name}**. 
  
  ```javascript
  <Welcome name="Eric" />
  ```

3. Review App.js to make sure that you've imported the Welcome component and that the Component has been added to the render function.

  Your code should look similar to the following after removing the demo content and adding the Welcome component
  ```javascript
  import Welcome from './components/welcome/Welcome';

  function App() {
    return (
      <div className="App">
        <Welcome name="eric" />
      </div>
    );
  }

  export default App;
  ```

## Create A Clock Component
The following example will show how to make a clock component that leverages state. In order to have a stateful component the component has to be created as a class and the class must extend the base React.Component class. The class must also include a render method.

State is similar to props, but it is private and fully controlled by the component. To demonstrate this behavior we will steal an example from the React documentation and add a clock to our website. To begin, we'll add the files necessary for a Clock component.

1. Within *src/components*, create a directory called *clock*.
2. Within *src/components/clock*, create *Clock.js*.

**Add the following code to clock.js**

```javascript
import { useEffect, useState } from "react";

function Clock(props){

    let [date, setDate] = useState(new Date());

    useEffect(()=>{
        let timerID = setInterval( () => tick(), 1000 );
        
        return () => {
            clearInterval(timerID);
        }
    },[])

    let tick = () => {
        setDate(new Date());
    }

    return (
        <div>
          <h2>It is {date.toLocaleTimeString()}.</h2>
        </div>
      );

}

export default Clock;
```

Now, let's walk through our new Clock component and discuss all of the class methods we've added.

- `useState()` - By overriding the `useState` hook, we are now able to set the initial date for our component and have a function that allows us to update its value.

- `useEffect()` -  This hook allows us to run code when the component renders or mounts in the DOM. This makes it a perfect spot to kick off the timer. If the Clock component is ever removed from the DOM, React calls the cleanup function returned by the `useEffect` hook, which stops the timer.

- `tick()` - This method updates the date stored in `date` using `setDate` and is run by `setInterval()` to get a new date every second. 

### Include the Clock component in App.js

Add `<Clock />` to include our stateful clock component. App.js should now look similar to the following code sample:

```javascript

import Welcome from './components/welcome/Welcome';

//import the new clock component
import Clock from './components/clock/Clock'

function App() {
  return (
    <div className="App">
      <Welcome name="eric" />
      <Clock/>
    </div>
  );
}

export default App;
```

## Create The Contact Component
The following example will show how to make a component that deals with user input. We will set up the form using "controlled components". Form elements such as `<input>`, `<textarea>`, and `<select>` maintain their own state and update it based on user input. An example of this is that they can remember what is entered by the user.

We would want React state to be the “single source of truth” instead of having to grab what was entered directly from the form. An input form element whose value is controlled by React in this way is called a “controlled component”.

Using controlled components is optional. Read the following for more information:
[Uncontrolled Components](https://reactjs.org/docs/uncontrolled-components.html )
[When To Use Refs](https://reactjs.org/docs/refs-and-the-dom.html)

1. Within *src/components*, create a directory called *contact*.
2. Within *src/components/contact*, create *Contact.js*.

**Add the following code to contact.js**

```javascript
import { useState } from "react";

function Contact () {

    let [submitted, setSubmitted] = useState(false);

    let [formData, setFormData] = useState({
        firstName: "",
        lastName: ""
    })

    let handleChange = (event) => {
        formData[event.target.name] = event.target.value;
        setFormData({...formData});
    }

    let handleSubmit = (event) => {
        event.preventDefault();
        setSubmitted(true);
    }

    let resetForm = (event) => {
        setFormData({
            firstName: "",
            lastName: ""
        })
	setSubmitted(false);
    }


    //show the thank you message if the form has been submitted
    if(submitted){
        return (
            <div>
                Thank you, {formData.firstName}, for submitting the form <br/>
                <button onClick={resetForm}>Reset Form</button>
            </div>
        )
    }
    return (
        <div>
            <form onSubmit={handleSubmit}>
                <div>
                    <label>First Name:</label>
                    <input onChange={handleChange} type="text" name="firstName" value={formData.firstName} />
                </div>
                <div>
                    <label>Last Name:</label>
                    <input onChange={handleChange} type="text" name="lastName" value={formData.lastName} />
                </div>
                <button>Submit Form</button> <br/>

                <hr />
                {JSON.stringify(formData)}
            </form>
        </div>
    );
}
export default Contact;
```

Now, let's walk through our new Contact component and discuss what is happening.

- **The initial state** -  here we are setting submitted to false which will be used for conditional rendering of the thank you page. We also set formData to an object that will be the source of truth for the data in the form.
  ```javascript
    let [submitted, setSubmitted] = useState(false);

    let [formData, setFormData] = useState({
        firstName: "",
        lastName: ""
    })
  ```

- `handleChange` - This method is responsible for keeping the form in sync with the formData object in state. It is called when the **onChange** event is triggered on the input fields.
```javascript

   let handleChange = (event) => {
	//update the value of this changed form field in the formData object
        formData[event.target.name] = event.target.value;

	//destructure formData into a new object and update formData in state with the new object
        setFormData({...formData});
    }

```

- `handleSubmit` - This method is responsible for what happens when the form is submitted. It is run when the **onSubmit** event is triggered on the form. We use the `preventDefault()` method to prevent the form from refreshing the page when submitted.
```javascript

   let handleSubmit = (event) => {
	//prevent the default behavior of a form to prevent the page from refreshing
        event.preventDefault();
	//update submitted to true to trigger rendering of the thank you message
        setSubmitted(true);
    }

```

- `resetForm` - This method clears our form by resetting the values in state. It is run when the **onClick** event is triggered on the reset button
```javascript

   let resetForm = (event) => {
        setFormData({
            firstName: "",
            lastName: ""
        })
	setSubmitted(false);
    }

```

### Include the Contact component in App.js

Import our Contact component. App.js should now look similar to the following code sample:

```javascript

import Welcome from './components/welcome/Welcome';
import Clock from './components/clock/Clock'
import Contact from './components/contact/Contact';

function App() {
  return (
    <div className="App">
      <Welcome name="eric" />
      <Clock/>
      <Contact/>
    </div>
  );
}

export default App;
```
