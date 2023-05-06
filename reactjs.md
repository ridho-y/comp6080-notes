---
title: ReactJS
---

## React
* React allows you to build isolated UI components in a simple, declarative way.
* When the state of your application changes, affected components will react accordingly by re-rendering to reflect the new state change.
* A React application is defined as a tree structure and is made up of components.
* React is most commonly used for web development, but can also be used for creating mobile applications, desktop applications and even terminal applications.

## Getting Started
* Create a React app: `npx create-react-app <name>`
* Initiate React app (once): `yarn install` or `yarn`
* Start React app: `yarn start`

## JSX
* JSX (JavaScript XML) is an extension of JavaScript.
* It allows you to treat HTML markup like any other JS object or variable.
* Take a look at `App.js`

```js
// You can store JSX within a variable.
const hello = <h1>Hello, JSX!</h1>;

// You can use them with standard javascript logic.
const even = isEven(num) ? <h1>Even</h1> : <h1>Odd</h1>;

// You can even embed other variables within your JSX.
const odd = <h1>Even: {isOdd(num)}</h1>;
```

## Styling using React + CSS
* Use braces `{ }` to place variables in your JSX.
* Examples:

```js
function App() {
   const date = new Date(Date.now());
   return (
        <div style={{ color: 'red' }}>
            {date.toLocaleString()}
        </div>
    ); 
}
```

* Note that to write styles the items are listed as a JS object (dictionary) `{ color: 'red' }`

## useState Hook
* <a href="https://react.dev/reference/react/useState" target="_blank">useState</a> allows you to add a state variable to your component
* Re-renders when the state is changed and the state is in the DOM
```js
import { useState } from 'react';

const [stateVariable, setStateFn] = React.useState(initialState);
```

* Example: 

```js
import { useState } from 'react';

export default function Counter() {
  const [age, setAge] = useState(42);

  function increment() {
    setAge(a => a + 1); // important to get the value first then increment!
    // setAge(a + 1); will only increase the age by one if +3 is clicked since it uses prev state
  }

  return (
    <>
      <h1>Your age: {age}</h1>
      <button onClick={() => {
        increment();
        increment();
        increment();
      }}>+3</button>
      <button onClick={() => {
        increment();
      }}>+1</button>
    </>
  );
}

```

## useEffect Hook
* <a href="https://react.dev/reference/react/useEffect#useeffect" target="_blank">useEffect</a>reacts to changes in our component and is triggered if certain conditions are met within the component
* The function is performed AFTER the render
* Typically used alongside `useState`

```js
React.useEffect(reactingFn, dependencies)
```

* `reactingFn` is the function that runs when anything is changed in the dependencies
    * You can return a cleanup function that is performed with old values before the `reactingFn` function everytime it re-renders
    * 
* `dependencies` is optional
    * If empty: `reactingFn` is re-rerun after every re-render of the component
    * If empty list: `reactingFn` is run only the first time
    * If list with dependencies: `reactingFn` is run every time one of the dependencies (e.g. variables) is changed 
* Example:

```js
const [seconds, setSeconds] = React.useState (0);
React.useEffect(() => {
    const interval = window.setInterval(() => {
        setSeconds(s => s + 1);
    }, 1000);

    return () => clearInterval(interval);
    }, 
    [1]
    );
```

## useContext Hook
* <a href="https://react.dev/reference/react/useContext" target="_blank">useContext</a> is a way to manage state globally, allowing certain elements have the state
* Wrap children that need the state with `<UserContext.Provider>`:

```js
import { useState, createContext } from "react";
import ReactDOM from "react-dom/client";

const UserContext = createContext() // Can carry a default value

function Component1() {
  const [user, setUser] = useState("Jesse Hall"); // Allows for changing of context

  return (

    // Provide the value of the UserContext
    <UserContext.Provider value={user}>
      <h1>{`Hello ${user}!`}</h1>
      <Component2 user={user} />
    </UserContext.Provider>
  );
}

function Component2() {
  return (
    <>
      <h1>Component 2</h1>
      <Component3 />
    </>
  );
}

function Component3() {
  return (
    <>
      <h1>Component 3</h1>
      <Component4 />
    </>
  );
}

function Component4() {
  return (
    <>
      <h1>Component 4</h1>
      <Component5 />
    </>
  );
}

// Now it can be accessed
function Component5() {
  const user = useContext(UserContext);

  return (
    <>
      <h1>Component 5</h1>
      <h2>{`Hello ${user} again!`}</h2>
    </>
  );
}
```

* To use the 


## Routing & SPAs
* Single Page Applications (SPAs) are a kind of web application that only downloads one HTML file, e.g. Facebook.
* The content is updated via JavaScript and content is downloaded using APIs such as Fetch.
* Use `React Router DOM` to implement the different pages
  * `yarn install react-router-dom`
* Example:

```js
import { BrowserRouter, Routes, Route } from 'react-router-dom';

export default function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />}>
        <Route path="blogs/:id" element={<Blogs />} />
        <Route path="contact" element={<Contact />} />
        <Route path="*" element={<NoPage />} />
      </Routes>
    </BrowserRouter>
  );
}
```

* `useParams()`: Returns parameters as a object (dictionary) in the components, such as `<Blogs />`
* `useLocation()`: Returns an object for `pathname`, `search`, `hash`
* `redirect(<path>)`: Go to somewhere else instead Link 

## Links and Outlets
* Links provide a link to display the path
* Outlets will display the children

```js
import { Outlet, Link } from "react-router-dom";

const Layout = () => {
  return (
    <>
      <nav>
        <ul>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/blogs">Blogs</Link>
          </li>
          <li>
            <Link to="/contact">Contact</Link>
          </li>
        </ul>
      </nav>

      <Outlet />
    </>
  )
};

```

## Material UI
* <a href='https://mui.com/material-ui/getting-started/overview/'>Material UI</a> is an React framework that implement's Google's Material Design
* `yarn add @mui/material @emotion/react @emotion/styled @mui/icons-material`