# create-react-app

React can take some time to wire up from scratch. To alleviate some of the work of getting an application off the ground we'll use a command-line tool to carry the burden for us. `create-react-app` is a tool to scaffold out React applications quickly. It will set up a project structure and will also install and configure the most common development tools utilized in most React applications. 

Tools like `create-react-app` are the easiest way to get a new React project up and running without spending time on configuration.

## What you get
Scaffolding a project with **create-react-app** comes with a lot of opinions and should provide you with what you need to build a production-ready React application as well as provide a full-featured development environment. Here are the features included:

* React, JSX, ES6, TypeScript, and Flow syntax support.
* Language extras beyond ES6 like the object spread operator.  
      * [Further Reading](https://facebook.github.io/create-react-app/docs/supported-browsers-features#supported-language-features)
* Autoprefixed CSS, so you don’t need -webkit- or other prefixes.
* A fast interactive unit test runner with built-in support for coverage reporting.
* A live development server that warns about common mistakes.
* A build script to bundle JS, CSS, and images for production, with hashes and sourcemaps.
* An offline-first service worker and a web app manifest, meeting all the Progressive Web App criteria.

These many opinions mean that these tools are preconfigured to work in a specific way. If your project needs more customization, you can "eject" and customize it, but you will need to maintain this configuration. ```npm run eject``` will expose the configuration for you to customize. Once this is done,  all of the commands except eject will still work.

> Note: this is a one-way operation. Once you run ```npm run eject```, you can’t go back! The supplied configuration is good for most small and medium-sized deployments. Don't feel pressured to use this feature without a good reason.

- [Create React App Documentation](https://facebook.github.io/create-react-app/docs/getting-started)

1. Create a New React App with `create-react-app`. The project folder is called "my-app".
      ```bash
      $ npx create-react-app my-app
      ```

2. Start the Application
      ```bash
      $ cd my-app/
      $ npm start
      ```

Your browser should open to http://localhost:3000, and you should see the following output in your terminal.

```bash
You can now view my-app in the browser.

  Local:            http://localhost:3000/
  On Your Network:  http://10.10.103.200:3000/

Note that the development build is not optimized.
To create a production build, use npm run build.
```

The my-app directory should have the following file structure:

```
my-app
├── README.md
├── node_modules
├── package.json
├── package-lock.json
├── .gitignore
├── public
│   └── favicon.ico
│   └── index.html
│   └── manifest.json
│   └── robots.txt
│   └── logo192.png
│   └── logo512.png
└── src
    └── App.css
    └── App.js
    └── App.test.js
    └── index.css
    └── index.js
    └── logo.svg
    └── reportWebVitals.js
    └── setupTests.js
```

## For the project to build correctly, specific files must exist with *exact* filenames:  
- `public/index.html` is the page template 
- `src/index.js` is the JavaScript entry point

## Customizing your React App
Tools like `create-react-app` give us a common starting point that reduces the rub of getting a project started, but treat the output of `create-react-app` as a convenient *starting point*.

React applications can be endlessly customized, just like any JavaScript application. However, you should follow some basic rules to keep things moving smoothly. In the next couple of sections, we'll explore where to add additional resources like CSS and images to our application.

**The *public* directory**  
The public directory contains the part of your application that is publicly accessible. Typically, you shouldn't edit files in the public folder. For example, stylesheets are almost always added without touching the HTML. However, some circumstances will require that you break that rule. For a brief discussion of when you might want to get hands-on with your public folder, visit  [Using the Public Folder](https://facebook.github.io/create-react-app/docs/using-the-public-folder#when-to-use-the-public-folder).

- index.html:  
The main page template and the public entry point for your application. Once this file is set up, it shouldn't require much of your attention. You will still need to edit this file to include items like meta tags and to change the app title. 
  
**The *src* directory**  
Your application lives in the *src* directory and you will spend the vast majority of your time editing the components contained therein.

- index.js:  
  The javascript entry point to our application. This file loads the default **App** component, `App.js`.
  
- `App.js`: The default component. `create-react-app` creates this file as the default application component. When the application loads, this component will load first.
  
- `App.css`: Contains custom CSS for the App component (`App.js`).
`
- `App.test.js`: The default test script for the default app. By default, `create-react-app` uses the [Jest](https://facebook.github.io/jest/) testing library. 

## Working with CSS and Images
Webpack has extended the concept of using the **import** statement beyond just including JavaScript files. You can include CSS and Images specific to a component with import statements.

```javascript

// Tell Webpack that our counter component requires the following style sheet
import './counter.css'; 

// Tell Webpack that our counter component requires the following image
import logo from './logo.png';

function Counter(props) {
  return (
      <div>
        <img src={logo} alt="Logo" />
        <button>-</button>
        <span className="CLASS_FROM_CSS">{count}</span>
        <button>+</button>
      </div>
  );
}

```
> NOTE: To reduce the number of requests to the server, importing images that are less than 10,000 bytes returns a data URI instead of a path. This applies to the following file extensions: bmp, gif, jpg, jpeg, and png. SVG files are excluded. You can think of a data URI as embedding the image directly in the HTML so it doesn't have to make a request to a server to get it. This can lead to a performance increase in your app load times.
