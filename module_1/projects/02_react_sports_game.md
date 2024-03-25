In this activity, you will build a simple sports game. This activity will exercise your comfort level with JSX, both stateful and stateless ReactJS components, working with props, and leveraging local state within a stateful component. 

To get started you need to get everything set up so we are able to run our React application. This includes creating an HTML page to display our application, importing React and other scripts, and leveraging these scripts to render an application to our HTML page.

## Setup
* Setup an HTML page that will present our application to our users.
* Setup a default component for our App that ```ReactDOM.render()``` renders to our HTML page. This can be a stateless component
    * **App** is a common name used for this default component. Many components can make up our **App** but we render this default component to display the entire application.
    * ```ReactDOM.render()``` should only ever render this component.
    * All other components will render through this component either referenced directly in this component or as children of components referenced directly in this component.


    >The code in [this repo](https://github.com/erics273/react-basics-lab-sportsgame) represents the activity up to **this**</strong> point (at the end of "Setup"). You're welcome to use this code as a starter or as a reference to help you get going.


## Normal Mode
Let's start building our game

### The Team Component
In order to play this game, you are going to need to create teams so they can compete for the win. Below is an outline of the functionality that our team component should include.

* Create a stateful **Team** component that accepts a **name** and a path to a **logo** for the team as a prop
* This component should display the team name and the logo provided through props
* The Team component should also display some stats about the team.
    * It should display the number of **Shots Taken**
    * It should display the **Score** for the team
* The Team component should have a **Shoot** button. We don't score every time we shoot so let's discuss the shoot buttons functionality.
    * When a shot is taken the **Shots Taken** count should always increase
    * There should be a random chance that the **Score** counter increases.
* Make sure to render and test your **Team** component functionality as you add new features.

### Setup our battle of the sports teams
Now that we have a Default component that represents our Application and we have created our **Team** component, we can start assembling the game.

* Update the default App component you created to display 2 teams, the home team, and the visiting team.
* Use your knowledge of HTML and CSS to make the page look more like a game where two teams, home, and visiting, are facing off in competition
* Verify both teams are displayed and keeping track of their stats

## Medium Mode
Let's add some extra functionality to our sports game.

* Add functionality to make a sound play when a team shoots and a different sound when a team scores. The resources below should help accomplish this.
    * [HTML audio element on MDN](https://developer.mozilla.org/en-US/docs/Web/API/HTMLAudioElement)
    * [Free sound effects](https://www.freesoundeffects.com/free-sounds/sports-10098/)
* Let's add an additional statistic to our teams. Let's display a **Shot Percentage** metric. This should be shots scored divided by shots attempted.
    * This metric should only display if a shot has been taken. This should not be visible if the team has not attempted to make a shot.
* Create a **Game Component** that accepts a **venue** name as a prop.
* Update your default component that is currently displaying your teams to display the **Game** component instead. And move everything the default component was displaying into the **Game** component
* Update the **Game** component to display "Welcome to" followed by the name of the **venue** passed in as a prop.
* Your app should still render the default component with ```ReactDOM.render()```, commonly named **App**. 
    * The default **App** component should only render the **Game** component instead of rendering the **Team** components as before. 
    * The Game component should display the venue name for the game and the **Team** components that were previously displayed in the default **App** component.
    * Each team should function as before but now conditionally display a **Shot Percentage** metric if a shot has been taken by the team.
* Think about what would happen if we added another **Game** component to our App. We could change the **Venue** name but we can only create new games with the same teams. What could we modify in the **Game** and **Team** components to allow us to have unique teams for each game we include in our default App component?

## Hard Mode
This section is not required and is to challenge you on concepts related to state. Let's modify the **Game** component to be the source of the truth for the game's state. The **Game** component should keep track of how the game is played and its progress. Currently, most of this is tracked in our **Team** component. Our game component will manage 2 teams, home and visiting, and their stats during the game. To accomplish this we will be converting our **Team** component to a stateless functional component and having the stateful **Game** component pass the data to the teams as props. This is concept is called [Lifting State Up](https://reactjs.org/docs/lifting-state-up.html). We are sharing state with all the components concerned by moving it up to the closest common ancestor of the components that rely on it.

* Convert the **Team** component to a functional stateless component. 
    * Everything that relied on state before inside the **Team** component should now rely on passed in props from the **Game** component.
* Update the **Game** component to keep track of the home and visiting team stats and pass that data to the **Team** component as props.
* Since all the game data will be tracked by the **Game** components state, the method used when clicking the shoot button for a team should also be passed in as a prop. This method needs to affect state in the right component.
* Add a **Reset Game** button to the **Game** and a counter displaying the number of resets.
    * When the reset button is pressed the team stats should reset and the reset counter should increase by 1

## Hard Mode Extra Credit
Create a Scoreboard component that displays the HOME and VISITING team scores.
