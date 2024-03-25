# Welcome to JavaScript
JavaScript is an object-oriented computer programming language commonly used to create interactive effects within web browsers.

## Useful Resources
[JavaScript Basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/JavaScript_basics)  

***PRO TIP***  
*https://mdn.io/YOUR_METHOD_HERE - Replacing YOUR_METHOD_HERE with something like 'getElementByID', 'getElementsByClass', or any other method you can think of should bring you to documentation on that specific method* 

## Variables

In programming, it's imperative that you have a way to store information. In most programming languages, these are called **variables**. A **variable** is a way for us to store a piece of data that can be used over and over throughout our program. It helps us write way less code and still accomplish our goals.


### Declaring and Assigning

When talking about variables, there are two concepts one must understand. The first is the declaration of a variable. The second is the assignment of a value to that variable.

Think of it as a filing cabinet. You know you'll need to store your paperwork, but before you do so, you actually need to go out and get a place to store it. The filing cabinet is the _declaration_ or creation of a place to hold your paperwork. Once you have that, you can now decide what paperwork to put in the cabinet, thus _assigning_ it.

Let's look at the keywords we can use to declare and assign variables.

### Let Keyword

The `let` keyword is the most common one you will be using. Let's look at how it works.

```js
let firstName; // declaration
```

There, we've just _declared_ a new variable named `firstName`. Now let's assign something to it.

```js
let firstName; // declaration
firstName = 'Bill'; // assignment
```

We've now taken our `firstName` variable and _assigned_ a value called `'Bill'` to it. You can also do your _declaration_ and _assignment_ at the same time, by doing the following:

```js
let firstName = 'Bill'; // declaration & assignment
```

### Const Keyword

The `const` keyword stands for **constant**. We should use it when creating a variable that will never change. For instance, in the above examples, we used `firstName`. That could easily change in your program from `'Bill'` to maybe `'Julie'` and so on. However, let's say that you wanted to keep track of something that will never change in your entire program. That's when you would create the variable using `const`.

```js
const pi = 3.14; // won't ever change
```

```js
// Let's define our favorite color, then change it.
let favoriteColor = 'green';
favoriteColor = 'blue';
```

While the above works just as you'd expect, the following will throw an error:

```js
const favoriteColor = 'green';
favoriteColor = 'blue'; // ERROR: Can't reassign "favoriteColor"
```

### Var Keyword

The `var` keyword is short for **variable** and is the original way to create and store variables. In fact, for a long time, it was the only way to do so.

```js
var firstName = 'Bill';
```

In the current version of JavaScript, the `let` keyword seeks to fully replace `var`. The reasoning is due to a concept called **scoping**. This is beyond the scope of this lesson. For now it's just important to understand that you should use `let` instead of `var` to store standard variables.

Do note that `var` is still completely valid. You'll likely see it only in tutorials, or other developers you work with might still use it. There is nothing wrong with `var`, but the JavaScript community is moving away from using it. Learning the current way of assigning a variable is important.

### Variable Rules

When declaring and naming a variable, there are a few rules that you should take into consideration.

- They can only **begin** with letters, `$` or `_`
- They can only **contain** letters, `$`, `_` and numbers.
- They are case sensitive (`firstName` is not the same as `firstname`)
- You can't use any reserved words ([see list](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords))
- You can only use camelCase or snake_case
  - The standard convention in JS is to use camelCase

## JavaScript Primitive Data Types

JavaScript includes two categories of data types: Primitives and Objects. Objects are a complex subject that we will cover at a later date. Primitives act as simple values that can be passed around and referenced directly. In this lesson, we'll discuss Primitives.

JavaScript provides five primitive types:

Type | Syntax
:--- | :---
String | `"hello there!"`, `'hello there!'`
Number | `1`, `200`, `3.14159`
Boolean | `true`, `false`
Undefined | `undefined`
Null | `null`


> Technically there are six types, but [Symbol](https://developer.mozilla.org/en-US/docs/Glossary/Symbol) is new and fairly uncommon. We won't cover it here.


### String

A `string` is a sequence of characters surrounded by quotation marks. You can use either `'hello there'` or `"hello there"` when writing a string. This convention varies widely between developers. In the JavaScript world, you'll find it more common to use the single quote since it's easier to type. Also, note that if you need to use an apostrophe inside of a string you either have to escape it or use double quotes. Take a look at these examples below.

```js
'The cat isn\'t in the barn' // Escaped
"The cat isn't in the barn" // Using Double Quotes
```


> In JavaScript, the `\` has a special purpose when dealing with strings. Combining it with another character enables that character to be represented in a string. This is called an `escape sequence`. It allows you to 'escape' from the normal string interpretation. When writing a string wrapped in single quotes, it would be impossible to write an apostrophe.  Using an escape sequence makes this possible. For example:

```js
 `'I\'m always right. I can\'t be wrong.'`
```

> See references for a complete list of escape sequences.


### Number

A `number` represents any numeric value. Some languages split numbers into multiple types depending on whether or not they contain decimals. JavaScript only has one `number` type.

```js
24 // Number
-5 // Number
3.15 // Number
0.0001 // Number
```

### Boolean

A `boolean` can only have two possible values: `true` or `false`. Booleans are standard across many languages. In JavaScript, they are used in control structures, like in a conditional statement.

```js
true // Boolean
false // Boolean
```

### Undefined

`undefined` is the default value for any variable that has been declared, but **has not been assigned a value.**

```js runnable
var newVar;

console.log( newVar );
```

### Null

`null` is a representation of the **intentional absence of any object value**. It is often used to indicate that a variable should hold a value and doesn't.

```js
null // null
```

## Statements and Expressions

### Statements
A statement is an action, and programs are made up of many statements.

```js
let name = "Tim";
console.log('Hi, my name is ' + name);
```

### Expressions

An expression is an operation that simplifies down to a value. We can substitute an expression for an actual value anywhere that we can use an actual value. For example:

```js
let age = 2016 - 1983;
let greeting = 'My name is Tim and I am ' + age + ' years old';

// or
let greeting = 'My name is Tim and I am 33 years old';

// or
let greeting = 'My name is Tim and I am ' + (2016 - 1983) + ' years old';
```

## Loose Typing

Changing the type of a variable is *allowed* in Javascript, but be careful! It can be very confusing. Generally I avoid it but its worth being aware of!

```js
// You can change me!
let x;     // x is undefined
x = 31;    // x is a number
x = 'Tim'; // x is a string
```

## Comments

```js
let name = 'Tim'; // Single Line Comment

/*
  Multi Line
  Comment
*/
let a = 1;
let b = 2;
let c = a + b;
```

## Truthy Vs. Falsey

A previous reading described the idea of types in JavaScript. One of those types was the boolean type, which has only two values: `true` and `false`. An interesting JavaScript feature is that you can use any type where a boolean is expected. The language will treat that value like a boolean. The terms `truthy` and `falsey` are commonly used to describe this phenomenon.

Unfortunately, this can be a bit confusing. If anything can be a boolean, how do we know if it will be `truthy` or `falsey`? This lesson will explain some of the rules for which values will be either `truthy` or `falsey`.

Unfortunately, `truthy` and `falsey` are not a black or white comparison when we look at the rules for variable comparison.

However, even though you have `true` and `false`, it's not that easy. Sometimes when looking at certain types of values, they could actually be `true`/`false` or rather `truthy`/`falsey`.

### Falsey Rules

There are certain values that are *always* `falsey` in JavaScript, these are:

```js
undefined
null
0
"" // empty string
NaN // Not a Number
false
```

### Truthy Rules

In JavaScript, anything not false is `truthy`. It is important to note that when we refer to something as being `truthy`, it does not just mean that the value is true. It means that the value coerces to `true` when evaluated in a boolean context.

```js
1 // Truthy
true // Truthy
"a" // Truthy
```

This might seem a little weird to you, but it's important to keep in mind when writing conditional statements. If a conditional statement doesn't boil down to one of the `falsey` values, then it's considered `truthy` and thus `true`.

```js
5 - 5 // 0 -> false
let x; // undefined -> false
x = ""; // empty string -> false
x = "a"; // non-empty string -> true
5 - 6; // -1 -> true
```

## Logical Operators

Logical operators are used to evaluate an expression and return either a `true` or `false` value. As a developer, you will use logical operators and expressions to solve logical problems. In this lesson, you will learn how to use each operator and how their order of operation affects evaluations.

Here are some you might see:

-  `&&` - and
-  `||` - or
-  `!` - not
- `===` - equal
- `!==` - not equal
- `>` - greater than
- `<` - less than

Note: Often, you'll see both `===` and just `==` used when testing equality. You can read more about that [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness), but it's _extremely_ rare for there ever to be a use case for using `==`. Therefore, you should ALWAYS use `===` when testing for equality.

### Logical Operators in the Real World

In the English language, logical operators are used with the words **_and_**, **_or_**, and **_not_**. For example:

> You will do the dishes `IF` you have no clean plates `AND` your kitchen smells.

For you to clean your dishes, two components must be true:

- You have no clean plates
- Your kitchen smells

This real world example of using logical operators to evaluate an expression is like using JavaScript's logical operators.

### If Statement

Before we jump into these three operators, let's take a quick look at the `if` statement.

An `if` statement is comprised of a few different parts. First, we must evaluate a condition.

```js
if (condition) {
  // Run this code
}
```

In the sample above, the code inside the `if` statement will _only_ run if the value of `condition` is true or "truthy", otherwise it will be skipped entirely. We can also add in the keyword `else` and chain them together as much as we'd like.

```js runnable
if (5 > 3) {
  console.log('5 is greater than 3');
} else {
  console.log('5 is not greater than 3');
}
```

### And Operator

The `&&` operator is used to evaluate an expression that has two or more components. For the entire logical expression to return true, all components that connect the `&&` operator must also be true. Using the real world example above, let's see how we write that in JavaScript:

```js
var hasCleanPlates = false; // We don't have clean dishes
var doesKitchenSmell = true; // The kitchen smells

if (hasCleanPlates === false && doesKitchenSmell === true) {
  console.log('We should clean our dishes');
} else {
  console.log('Nah, we will wait till next time');
}
```

In this example, the `&&` operator requires that both expressions return a `true` boolean. The first expression, `hasCleanPlates === false` is true and the second expression, `doesKitchenSmell === true` also returns true.

### Or Operator

The  `||` operator is used to evaluate an expression that has two or more components. It will return true if either component of the logical expression are true.

Let's say that you have a roommate, and your roommate is much more strict with their home upkeep. They aren't as lenient as you when it comes to dishes and will clean the dishes if there are no clean plates **OR** the kitchen smells.

```js runable
let hasCleanPlates = false; // We don't have clean dishes
let doesKitchenSmell = false; // The kitchen doesn't smell (yet)

if (hasCleanPlates === false || doesKitchenSmell === true) {
  console.log('We should clean our dishes');
} else {
  console.log('Nah, we will wait till next time');
}
```

In this example, we will print out "We should clean our dishes" whenever the kitchen smells OR we have no clean plates.

#### The `NOT` Operator

Syntax: `!`

The `!` operator is used to invert the desired expression evaluation to the opposite returned boolean. This means that when we use the `!` operator placed in front of an expression, we are asking the expression to return true if a specific expression already equates to false.

Let's refactor our example to accept this new operator.

```js
let hasCleanPlates = false;
let doesKitchenSmell = false;

if (!hasCleanPlates || doesKitchenSmell) {
    cleanDishes();
}
```

Did you notice we didn't use the `==` operator? This is because `hasCleanPlates` and `doesKitchenSmell` already returns a boolean, so our `if` statement will still work as intended. So `doesKitchenSmell` is equal to `doesKitchenSmell === true`.

As for `hasCleanPlates`, we placed the `!` right before to declare we are inverting the boolean. This means if `hasCleanPlates` is equal to **FALSE**, return `true`.

If this concept is difficult for you to grasp, try thinking of it in English.

> You will do the dishes `IF` you do `NOT` have clean plates `OR` your kitchen smells.

The JavaScript syntax `!` represents the English word `NOT` in this example.

### Order of Operations

You might remember in math class that arithmetic operators have an order of operations. The same is true for our JavaScript logical operators.

1. `()` - parenthesis
2. `!` - not
3. `&&` - and
4. `||` - or

Let's take a look at a complex logical expression and use the order of operations to break it down:

```javascript runnable
// milks
let milk = true;
let cream = false;
let soyMilk = false;

// expressos
let caffeinatedEspresso = true;
let decaffeinatedEspresso = false;

// chocolates
let darkChocolate = false;
let lightChocolate = false;

// this is a latte!

var isLatte =
        (milk || cream || soyMilk)
    &&
        (caffeinatedEspresso || decaffeinatedEspresso)
    &&
        !(darkChocolate || lightChocolate)
    ;

// print if this is a latte
console.log(isLatte);
```
Let's walk through this using the correct order of operations. First we will need to evaluate everything that is within `()`.

```js
        (milk || cream || soyMilk) // (true || false || false)
    &&
        (caffeinatedEspresso || decaffeinatedEspresso) // (true || false)
    &&
        !(darkChocolate || lightChocolate) // !(false || false)
    ;
```

Moving left to right, JavaScript will simplify this boolean value expressions within the `()` into a single boolean by reading each `()` as a single boolean value.

```js
        (true) // Returns true since an inside boolean was true.
    &&
        (true) // Returns true since an inside boolean was true.
    &&
        !(false) // Returns false since no inside boolean was true.
    ;
```

Before continuing our quest to solve this complex logical expression, we must first address `!` which is next up for our order of operations. Since `!(false)` will invert the boolean within the `()`, the returning boolean value will be `true`.

Now it's time for the `&&` operator to take its turn. We are left will a simple expression that looks like this:

```js
    (true && true && true) // This will return true!
```

This means that when we run this code, we will console log `true`!

## Including JavaScript in HTML

You've already worked with HTML. Before we dive into writing JavaScript, let's talk about how we can link it to our `index.html` file. This way we can make use of it on the front-end.

The best way to add a JavaScript file to your HTML is to use the `<script>` tag. Here's what it might look like:

```html
<script src="main.js"></script>
```

You'll notice that unlike the `<link>` tag we use to include CSS, this tag has both an open and close. We'll see why this is later. After creating the `<script>` tag, you need to add the `src` attribute. This attributes points to the location of your JavaScript file. Here are some examples:

```html
<!-- Located in the root, next to your index.html -->
<script src="main.js"></script>

<!-- Located inside of an `js` folder -->
<script src="js/main.js"></script>

<!-- Located up one level and inside of a `js` folder -->
<script src="../js/main.js"></script>
```

## Script Tag Location

Where you place the `<script>` tag does matter. It's not uncommon to see it called in the `<head>` tags, like so:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Cool Website</title>
    <!-- Not Recommended -->
    <script src="main.js"></script>
  </head>
  <body>
  </body>
</html>
```

While this _could_ work, it's a best practice to include your script tags as the last elements in the `<body>` tags, like so:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Cool Website</title>
  </head>
  <body>

    <!-- Recommended -->
    <script src="main.js"></script>
  </body>
</html>
```

This way, the script won't be called until after all your HTML has loaded. While this might not matter much now, it will matter soon. When your JavaScript interacts with the elements on your page, you will be glad for this placement.


> There are ways of including JavaScript in your `<head>` tag and telling it to wait to execute. That is beyond the scope of this lesson.


## JavaScript in the Script Tag

While we recommend linking to an external JavaScript file, you can also write code in your HTML.  Just use the `<script>` tag to write the code directly onto the HTML.

```html
<script>
  let answer = 10 - 5;
  console.log("The answer is " + answer);
</script>
```

Don't worry about what the code is doing. Just notice that you don't need to use the `src` attribute, you can include JavaScript code right on the page. As you might have guessed, this is why the `<script>` tag has an open and close.

## Linking Dependencies

Since HTML parses from top to bottom, we should include `<script>` tags at the lower part of the document. The same top down approach applies for adding multiple JavaScript files. Take the following as an example:

```html
<script src="js/parents.js"></script>
<script src="js/siblings.js"></script>
<script src="js/family.js"></script>
```

The ordering of these JavaScript inclusions is important. When the browser reads the files, it will do so in the order provided. In the above case, `parent.js` is read first, then `sibling.js`, and finally `family.js`. So long as the files included first don't reference code loaded later, all is well.

For instance, `family.js` can reference code in `parent.js` without creating errors. `parent.js` is already loaded by the time that `family.js` references it.

However, the opposite isn't true. If `parent.js` references code in `family.js`, the interpreter will throw an error. If `parent.js` tries to run code in `family.js`, it will do so before `family.js` is loaded and will throw an error.

## Control Flow

When you write a program, you are giving the computer a series of instructions to follow. Those instructions are often complex and can depend on many factors including user input, current data, or instructions written by other programmers. Most programming languages include a series of "control flow" features to manage this complexity.

- **"Control flow"** - The execution order in instructions.

- **Control flow statements** - The programming tools we use to define the order of execution, usually loops and conditional statements.

This lesson is not intended to give you a detailed breakdown of the syntax necessary to author control flow in your programs. Rather, this article outlines the general concept of control flow and why it is important.

### Managing Logic with Control Flow

As a programmer, you will spend your time implementing some logic in your programs. Logic is a _big_ topic, with lots of interesting branches into philosophy, math, and cognition. In this course, we will focus only on the concepts necessary to produce logically structured code. In essence, when we talk about flow control, we are talking about ways to tell our programs _when to run some code_ and _how many times to run it_.

Now, let's look at a scenario to demonstrate how flow control is used to determine when specific blocks of code can run. The following scenario is common: When the user clicks a button, we want to perform an action.

In this case, the action is to change the color of a square. In the real world, the button might be opening and closing a dropdown to show content or a thousand other things.

Here is where control flow is significant: _the new color of the square depends on its current color_. If the square is red, we change it to blue and vice-versa. Review the following three lines of logic.

```
- If the user clicks the button, change the color of the rectangle.
- If the rectangle is blue, change it to red.
- If the rectangle is red, change it to blue.
```

Now, let's look at a program that follows this logic.

> The following program uses JavaScript that you haven't seen yet. Don't get bogged down in the code; the point of this little program is to _show the logic in action_, not to explain the details of the JavaScript syntax.

```html hostable group:colored_square name:index.html
<!doctype html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>Colored Square</title>
        <link rel="stylesheet" href="style.css">
    </head>
    <body>
        <div class="wrapper">
            <div id="square" class="red"></div>
            <a href="#" id="button">Change Color</a>
        </div>
        <script src="script.js"></script>
    </body>
</html>
```
```css hostable group:colored_square name:style.css
body{
    margin: 10px 0 0 0;
    background: #666;
    font-family: Helvetica, Arial, sans-serif;
}
.wrapper{
    width: 600px;
    background: white;
    margin: 0 auto;
    padding: 10px;
}
#square{
    height: 200px;
    margin-bottom: 10px;
}
#button{
    display: block;
    padding: 10px 15px;
    background: #ccccff;
    text-align: center;
    text-decoration: none;
    border-radius: 10px;
    width: 50%;
    margin: 0 auto;
}
#button:hover{
    background: #aaaaff;
}
.red{
    background: red;
}
.blue{
    background: blue;
}
```
```js hostable group:colored_square name:script.js
const square = document.getElementById( "square" );
const button = document.getElementById( "button" );

// When the button is clicked
button.addEventListener( "click", function(){

    let color = square.className;

    // Change the color of the square

    // if the color is red
    if( color === "red" ){
        // change it to blue
        square.className = "blue";
    }
    // if the color is blue
    else{
        // change it to red
        square.className = "red";
    }
} );
```

To see the above logic written as JavaScript, open the `script.js` file. Again, you won't understand all that you see in that file. However, read through the comments to follow the logic. The "colored rectangle" example uses a control structure called an `if/else` statement to determine the color of the rectangle. `if/else` statements are an example of control flow statements, of which JavaScript has several.

This example is intended only to give you a sense of how control flow works; we'll go over the details in following lessons.

### Types of Control Flow

Control flow statements fall into two broad categories: **Loops** and **Conditional Statements**.

- **Conditionals Statements define the criteria that must be met to allow a block of code to execute.** The idea of conditional statements is that some code need only run _some of the time_. For instance, if you see phrases like: "If 'x' is true, run 'y' code," then you should be using conditional statements. If 'x' is false, then 'y' won't run. 'y' only runs some of the time.

- **Loops specify how many times a block of code should run.** Use Loops to repeat an action more than once. You'll know that you need loops you see phrases like: "Run this code 'x' number of times," or "Run this code _until_ a condition is met." Whenever you need to do the same thing multiple times, use loops.

else if## Conditional Statements

Conditional statements dictate which parts of a program run, based on a "condition." They determine _if_, and _when_ a block of code should run. The condition is an expression that resolves to either `true` or `false`.

### The `If` Statement

The simplest conditional statement is called an `if` statement. The idea of an `if` statement is simple. It allows us to define a condition to determine if a block of code should run. If the condition resolves to `true`, then the code is run. If the condition resolves to `false`, then the code doesn't run.

The logic for an `if` statement is:

```
if the CONDITION is TRUE, perform an ACTION
otherwise, do nothing
```

The "otherwise, do nothing" line is necessary. It tells us that the code included in the if statement block will only run some of the time.

The syntax for an `if` statement requires a few items.

- The `if` keyword specifies that the statement is an `if` statement
- The parenthesis `()` contains the condition that is checked, and resolves to either `true` or `false`.
- The curly braces define the block of code (ACTION) that will run if the condition is `true`.

If the condition is `false`, then the action doesn't run. Nothing happens.

```js
if( /* CONDITION */ ){
  /* ACTION */
}
/* do nothing */
```

#### An `if` Statement with a True Condition

In this example, the conditional is `x > 0`. `x` holds the value 1. The expression evaluates to `true` because 1 is greater than 0, so `if` statement runs the block of code. You can read this example as: "If x is greater than 0, log the string 'This will log because the condition is true.'"

Because `x` is greater than 0, the string gets logged.

```js runnable
let x = 1;

// first if statement
if ( x > 0 ) {
    console.log( "This will log because the condition is true" );
}
```

#### An `if` Statement with a False Condition

This time, the conditional is `x < 0`. `x` is 1, so the expression evaluates to `false`. The `if` statement does _not_ run the block of code. You can read this example as: "If x is less than 0, log the string 'This will not log because the condition is false.'"

Because `x` is _not_ less than 0, the string is _not_ logged.

```js runnable
let x = 1;

// second if statement
if( x < 0 ){
  console.log( "This will not log because the condition is false" );
}
```

#### An `if` Statement that Compares Two Variables

This third example compares the values of two variables. You can read it as saying: "If `count` is greater than or equal to `minimum`, log the string 'We have enough. Good job.'"

Run the following code sample. You should see "Evaluation complete. Nothing printed to STOUT."
Because the condition is false, this message states that we did not log anything to the console.  The `count` is *not* greater than or equal to `minimum`.

```js runnable
let count = 10;
let minimum = 12;

if ( count >= minimum ) {
    console.log( "We have enough. Good job." );
}
```

Now, change `count` to the number 14 and rerun the code. When you run it this time, you should see a different message in the console: "We have enough. Good job.". Cool, this means that our condition is `true`. `count` is now 14, and `minimum` is 12. 14 _is_ greater than or equal to 12, so the block runs.

### The `if/else` Statement

`if/else` statements are slightly more complicated than `if` statements. Fortunately, they operate on the same basic concept. They contain an `if` condition that must be true for the first block of code to run. Besides the `if` block, the statement also includes an `else` block that will run if the condition is `false`.

The logic looks like this:

```
if the CONDITION is TRUE, perform the FIRST ACTION
if the CONDITION is FALSE, perform the SECOND ACTION
```

The syntax looks like this:

```js
if( /* CONDITION */ ){
  /* FIRST ACTION */
}
else{
  /* SECOND ACTION */
}
```

You can read `if else` statements as "If the condition is true, run the first block. If the condition is false, run the second block."

#### An `if/else` Statement Comparing Two Variables

Let's elaborate on one of our previous examples:

```js runnable
let count = 10;
let minimum = 12;

if ( count >= minimum ) {
    console.log( "We have enough. Good job." );
}
else{
    console.log( "Not enough. We need more." );
}
```

When we run this code, we no longer get the message: "Evaluation complete. Nothing printed to STOUT." because we are always printing something to the console regardless of the condition. If the condition is `true`, the first block prints. If the condition is `false`, the second block prints.

As long as `count` and `minimum` store numbers, this code will always produce some output to the console.

### The `else if` Statement

We can take the `if/else` statement a step further. We can define multiple conditions and multiple blocks to respond to those conditions. The `else if` statement allows us to add more than one conditional statement to determine the code to run.

The logic looks like this:

```
if the FIRST CONDITION is TRUE, perform the FIRST ACTION
else if the SECOND CONDITION is TRUE, perform the SECOND ACTION
if both CONDITIONS are FALSE, perform the THIRD ACTION
```

The syntax looks like this:

```js
if( /* FIRST CONDITION */ ){
  /* FIRST ACTION */
}
else if( /* SECOND CONDITION */ ){
  /* SECOND ACTION */
}
else{
  /* THIRD ACTION */
}
```

#### An `else/if` Statement Comparing Two Variables

```js runnable
let count = 10;
let minimum = 12;

if ( count > minimum ) {
    console.log( "We have more than enough. Good job." );
}
else if( count === minimum ){
    console.log( "Just right; the perfect number" );
}
else{
    console.log( "Not enough. We need more." );
}
```

Run the code, unchanged. You should see the message: "Not enough. We need more.". Makes sense, right? 10 is less than 12, so the condition `count > minimum` (read as "`count` is greater than `minimum`") is` false`. Likewise, `count === minimum` (read "`count` is exactly equal to `minimum`") is also `false`. If both of our conditions are `false`, then we are left only with the final `else` block, which runs.

Now, change the value of `count` to 14 and rerun the block. You should see the message: "We have more than enough. Good job." because the first condition in the `else if` statement evaluates to `true`. The rest of the statement gets ignored, so the second condition isn't even tested.

Now, change the value of `count` to 12 and rerun the block again. You should see the message: "Just right; the perfect number." In this case, the first conditional evaluated to false (`count` isn't greater than `minimum` because it holds the same value as `minimum`). Since the first condition is false, the first code block doesn't run. Then, the second condition gets evaluated. Sure enough, it resolves to `true` (`count` is 12, and `minimum` is 12, so they are equal). Because this second condition is `true`, the `else` block is ignored as well.


> Another powerful conditional statement is called a `Switch Statement`. We don't cover it in this lesson, but its behavior is somewhat similar to the `else if` statements. If you want to read about it go to [the MDN Switch article](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/switch). Theoretically, you may never use a switch statement, but its good to be familiar with the basic syntax.