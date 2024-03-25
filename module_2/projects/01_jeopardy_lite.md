# React Jeopardy Lab
In this project, you will a simple Jeopardy game by consuming the [jService](http://jservice.xyz/) API. You are going to add this game as a new component to your application from the lecture in class.

To get started you need to get a few things set up so we are able to communicate to the jService API.

## Setup

* Create a **Jeopardy** component in **src/components/jeopardy/**.

**src/components/jeopardy/Jeopardy.js**
```javascript
import { useEffect, useState } from "react";

function Jeopardy(props) {

  let [score, setScore] = useState(0);
  let [jeopardyData, setJeopardyData] = useState({});

  //when the component mounts, get a the first question
  useEffect(()=> {
    getNewQuestion();
  },[])

  //get a new random question from the API and add it to the data object in state
  let getNewQuestion = () => {
    //use fetch to make an API call and get a random Jeopardy question (returns a promise)
    fetch(`https://jservice.xyz/api/random-clue`)
        //on success of the fetch request, turn the response that came back into JSON
        .then((response) => response.json())
        //on success of turnig the response into JSON (data we can work with), lets add that data to state
        .then((data) => {
            
            //put the data in the console just so we can see it
            console.log("data from the api", data);

            //update state with the data from the API causing the page to re-render
            setJeopardyData(data);
        })
        //handle any errors/failures with getting data from the API
        .catch((error) => {
            console.log(error)
        });
  }

    //present the results to the user
    return (
      <div>
        {/* Displaying the question to help you get started */}
        Question: {jeopardyData.question}
      </div>
    );
}

export default Jeopardy;
```

## Normal Mode
Let's start building our game

* Update the navigation and router of your application to display the new component
* Display the question, category title (harder than it seems), and point value returned from the API
* Keep track of the user's score in state and display it
* Provide a way for the user to submit an answer to the question using controlled components or a ref
* If the answer is correct then add the point value of the question to the user's score. 
* If the answer is wrong, subtract the point value from the user's score.
* After the user answers a question display another random question from the API

## Medium Mode 

* Create a display component for the Jeopardy game that handles the display of the game
* Update the Jeopardy component to only render the new display component
* Pass the needed props from the Jeopardy component to the display component so it has all the data it needs to display the game data and submit the user's answer

## Hard Mode
* Instead of displaying a single random question, display 3 categories. 
* Once a user selects a category, display the question for the category selected
* The rest of the application should work the same