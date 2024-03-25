# A Simple JavaScript Counter
Let's build a simple application with HTML and JavaScript that counts up and down with some rules!

## Create your project structure

1. Create the following directory structure

```
    js_counter/
    ├── index.html
    └── assets/
        └── javascript/
            └── counter.js

```

## Setup your files

2. Add a basic HTML structure to index.html.
3. Give your page a title of "A simple counter application".
4. Add the following code to your `<body>` tag:

```html
  <!-- Create a increment button, decrement button, and a counter -->
  <button id="decrement">-</button> <span id="counter">0</span>
  <button id="increment">+</button>
```

5. Link your JavaScript file right above your closing `</body>` tag, using the `<script>` tag:

```html



    <!-- Link your JS file using the script tag: -->
    <script src="assets/javascript/counter.js"></script>
  </body>
</html>
```

## JavaScript Instructions

### Getting Started
- First, let's open counter.js and create some variables that represent the elements in the HTML Tree (or, "DOM") we need to work with:

```javascript
// The best-practice is to pull all the elements into variables, in order to avoid
// searching the HTML tree for these elements more than once:
let incrementButton = document.querySelector("#increment"); 
let decrementButton = document.querySelector("#decrement"); 
let counter = document.querySelector("#counter"); 
```

### Increment Button

- Let's work with the `incrementButton`. We know that when it is clicked, something needs to happen. Let's focus on that first. This code goes below the variables created in the previous step.

```javascript
// This line says, "I want to listen for someone to CLICK my
// incrementButton, and any time I 'hear' that event occur,
// I want some code to run.
incrementButton.addEventListener("click", (event) => {

  // Any code you write in here, will run every time incrementButton
  // is clicked.

  // Run the console.log function to display some text in the console:
  console.log("+ button clicked");

}) // We have to close the curly braces and parentheses we opened above.
```

- Now that we have proven that we have "attached" the click event to `incrementButton`, let's make the counter go up when we click the button
  - Start by creating a variable that gets the current value and increments it:

```javascript
incrementButton.addEventListener("click", (event) => {
  console.log("+ button clicked");

  // Calculate the new value for our counter:
  let newCounterValue = Number(counter.innerHTML) + 1;
})
```

- Now we need to update the counter in the HTML tree ("DOM") with our `newCounterValue`:

```javascript
incrementButton.addEventListener("click", (event) => {
  console.log("+ button clicked");

  // Calculate the new value for our counter:
  let newCounterValue = Number(counter.innerHTML) + 1;

  // Calculate the new value for our counter:
  counter.innerHTML = newCounterValue;
})
```

- Refresh your page and check to make sure your counter increases. If it is not working, use your console to see out what error messages you may have.

- Make the counter turn red if the counter value is >= 10:

```javascript
incrementButton.addEventListener("click", (event) => {
  console.log("+ button clicked");

  // Calculate the new value for our counter:
  let newCounterValue = Number(counter.innerHTML) + 1;

  // If the counter is >= 10 then change the text color to red:
  if(newCounterValue >= 10) {         // WHAT IS THIS? Check out "IF Statements" in the Useful Resources section.
    counter.style.color = "red";
  }

  // Calculate the new value for our counter:
  counter.innerHTML = newCounterValue;
})
```

- Refresh your page and check to make sure your counter turns red at 10 or greater. If it is not working, use your console to figure out what errors you have

### Decrement Button

- Let's work with the `decrementButton`. We know when it's clicked something needs to happen. Let's focus on that first. This code goes below the code for the `incrementButton` event listener from the previous steps.

```javascript
// This is the "event listener" for clicking the button.
// Use the console.log function to display some text in the console when the button is clicked:
decrementButton.addEventListener("click", (event) => {
  console.log("- button clicked");
})
```

- Now that we have proven that we have attached the click event to the `decrementButton`, let's make the counter go down when we click the button
  - Start by creating a variable that gets the current value and decrements it:

```javascript
decrementButton.addEventListener("click", (event) => {
  console.log("- button clicked");

  // Calculate the new value for our counter (note the subtraction operator):
  let newCounterValue = Number(counter.innerHTML) - 1;
})
```

- Now we need to update the counter in the HTML tree ("DOM") with our `newCounterValue`:

```javascript
decrementButton.addEventListener("click", (event) => {
  console.log("- button clicked");

  // Calculate the new value for our counter:
  let newCounterValue = Number(counter.innerHTML) - 1;

  // Update the counter in the HTML tree:
  counter.innerHTML = newCounterValue;
})
```

- Refresh your page and check to make sure your counter decreases. If it is not working, use your console to figure out what errors you have.

- Let's make sure the counter cannot go below 0:

```javascript
decrementButton.addEventListener("click", (event) => {
  console.log("- button clicked");

  // Calculate the new value for our counter:
  let newCounterValue = Number(counter.innerHTML) - 1;

  // Only update the counter value on the screen if the counter is > 0:
  if (counter.innerHTML > 0) {
    counter.innerHTML = newCounterValue;
  }
})
```

- Refresh your page and check to make sure your counter won't drop below 0. If it is not working, use your console to debug.

- Let's make sure the counter turns back to black once it drops below 10:

```javascript
decrementButton.addEventListener("click", (event) => {
  console.log("- button clicked");

  // Calculate the new value for our counter:
  let newCounterValue = Number(counter.innerHTML) - 1;

  // If the counter drops below 10, change the text color to black:
  if(newCounterValue < 10){
    counter.style.color = "black";
  }

  // Only update the counter value on the screen if the counter is > 0:
  if (counter.innerHTML > 0) {
    counter.innerHTML = newCounterValue;
  }
})
```

---

**_Remember to use your Developer Tools to troubleshoot any issues you may run into. [Chrome Developer Tool Documentation](https://developers.google.com/web/tools/chrome-devtools/)_**

**_Useful Resources_**  
- [IF Statements](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/JavaScript_basics#Conditionals)
- [JS Basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/JavaScript_basics)
- [querySelector](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector)  
- [addEventListener](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)
- [innerHTML](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML)
- [style](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/style)
- [Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number#Convert_numeric_strings_and_null_to_numbers)