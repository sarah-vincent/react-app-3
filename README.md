# react-app-3
React button with dismissible alert

From the video tutorial "React Tutorial for Beginners"
https://www.youtube.com/watch?v=SqcY0GlETPk

**Notes**

**Ticket 4a: Intro to React**

React Tutorial for Beginners

React is a javascript library for building dynamic and interactive user interfaces that was created by Facebook in 2011 to make updating the html in DOM more simple, and is currently (2024) the most widely used javascript library for frontend development.
Frontend developers must know how to confidently build an app with react.

Allows us to change the page content in response to user actions.
For example, use JavaScript to hide an element when a button is clicked.

A react application is a tree of components (parts like navBar, gameGrid, GameCard, etc.) with the app as the root bringing everything together

Components help us write reusable, modular, and better organized code. Allows us not to have to update DOM elements. 

TypeScript is a typed JavaScript superset that compiles to plain JavaScript.

Example

interface Props {
  age: number;
}

Setting Up the Development Environment 5:00

Download node.js latest version

In VS Code, Settings, Format on save - yes

Creating a React App

Create React APP (CRA)- official tool created by React team
Vite- another tool, used a lot now, much faster

To create an app in vite:
in command pallet, type: npm create vite@latest
(or instead of latest, in Mosh video, 4.1.0
(and a whole bunch of other things to create a file in command pallet and then open it in vs code)

Choose framework- React
Choose language- TypeScript

Next, install all the 3rd party dependencies and run it in our web server
In command prompt:
npm i
code . 
(launches the project in vs code)

to launch our web server:
npm run dev

npm, which stands for Node Package Manager, serves as a crucial component in the JavaScript ecosystem. Let’s delve into its key aspects:
Software Registry and Library:
npm is the world’s largest Software Registry, housing over 800,000 code packages.
Open-source developers utilize npm to share software, while organizations employ it to manage private development1.
Package Management:
The name npm originally stood for Node Package Manager when it was created as a package manager for Node.js.
All npm packages are defined in files called package.json.
A package.json file specifies essential information about a package, including its name, version, and other relevant details.
Dependencies for a project are also defined in package.json.
npm can manage dependencies by installing them with a single command1.

Project Structure 

See files in VS Code folder for react-app

Creating a React Component

Created a Message.tsx file for react components

Can use a javascript class or a function. Function-based components have become more popular because they’re more concise and easier to write.

Function-Based Components 12:00 in video

// PascalCasing: capitalize the first letter of every word
// JSX: JavaScript XML

babeljs.io/repl
How this code gets converted to JavaScript

  return <div><Message></Message></div>  // always close react components or get compilation error

or use self-closing syntax: return <div><Message /></div>;

How React Works 16:45

When our app starts, react takes our component tree (App and Message files) and builds a JavaScript structure called the Virtual DOM (different from the actual DOM of the browser)

(App is our root or top-level component)



a lightweight in-memory representation of our component tree where each node represents a component and its properties

When the state or the data of a component changes react updates the corresponding node in the virtual DOM to reflect the new state.

Then it compares the current version of virtual DOM with the previous version to update the nodes that need to be updated, and updates those nodes in the actual DOM

Technically, updating the DOM is not done by React itself, but by a companion library called react DOM


React Ecosystem 1:20

React is a JavaScript library for building user interfaces.
A library is like a tool (one tool) just like a framework is like a toolset (many tools).

Frameworks: Angular, Vue


React is a library or a tool for creating dynamic user interfaces 
In order to pick the right tool for the job, we often need different tools for other purposes in the app:


Building Components 21:06

Important for setting a good foundation for the app
Building components
Rendering markup with JSX
Managing state
Passing input via props

Creating a ListGroup Component

First, install Bootstrap to give our app a modern look and feel
getbootstrap.com
Very popular CSS library that gives us several CSS classes for styling our apps

Fragments
import { Fragment } from "react";
and wrap code in <Fragment></Fragment>
used to wrap code to make react happy. Import fragment component from react.

A better way to achieve wrapping in fragment tags is to use empty angle brackets instead- tells react the same things
<> </>


Frequently Used Shortcuts
ctrl + d			select other instances of same selection, edit with multiple cursors
escape			to exit from multi-cursor editing
ctrl + shift + p		open command prompt in vs code
ctrl + `			open terminal in vs code



Rendering Lists
Render a dynamic list instead of hard coding the list into html:

function ListGroup() {
  const items = ["New York", "San Francisco", "Tokyo", "London", "Paris"];


  items.map((item) => <li>{item}</li>);


  return (
    <>
      <h1>List</h1>
      <ul className="list-group">
        {items.map((item) => (
          <li key={item}>{item}</li>
        ))}
      </ul>
    </>
  );
}


export default ListGroup;


Conditional Rendering
When rendering different content based on conditions, use an if statement.

let items = []		use a variable
const items = []		use a constant
------------------------------------------------------------------
Render a list with the heading based on changing conditions:
function ListGroup() {
  let items = ["New York", "San Francisco", "Tokyo", "London", "Paris"];
  items = [];


  if (items.length === 0)
    return (
      <>
        <h1>List</h1>
        <p>No item found</p>
      </>
    );
----------------------------------------------------------------------
A different way to achieve the same result:
Eliminate the if statement and render conditionally inside our JSX expression.
Inside JSX expression, can only use html elements or other react compmonents, cannot use an if statement. Except with braces, we can render anything dynamically. 

 return (
    <>
      <h1>List</h1>
      {items.length === 0 ? <p>No item found</p> : null}
      <ul className="list-group">
        {items.map((item) => (
          <li key={item}>{item}</li>
        ))}
      </ul>
    </>
  );
}

A different way to write the code so it doesn’t look so complex is to declare a constant and move the statement out of the JSX markup, so the JSX markup looks a little bit cleaner.
function ListGroup() {
  let items = ["New York", "San Francisco", "Tokyo", "London", "Paris"];
  items = [];


  const message = items.length === 0 ? <p>No item found</p> : null;


  // items.map((item) => <li>{item}</li>);


  return (
    <>
      <h1>List</h1>
      {message}
      <ul className="list-group">
        {items.map((item) => (
          <li key={item}>{item}</li>
        ))}
      </ul>
    </>
  );
}







Logical && used in expression 
37:45 in video

These two expressions are the same but the second one is better because it doesn’t use null, and instead uses the logical && to achieve the same result.

{items.length === 0 ? <p>No item found</p> : null}
{items.length === 0 && <p>No item found</p>}


true && 1 == 1
true && ‘Mosh’ == ‘Mosh’
false && ‘Mosh’ == false

Handling Events 38:38

How to handle click events within a component

With react, we almost never have to interact with the DOM directly. We use components that have state. When the state of a component changes, react will update the DOM to match the state.
function ListGroup() {
  let items = ["New York", "San Francisco", "Tokyo", "London", "Paris"];
  let selectedIndex = 0;  // selectedIndex is a state variable
  // Hook
  const [selectedIndex, setSelectedIndex] = useState(-1);


//
const [name, setname] = useState("");
//

  --------------------------
Notice how properties (props) of the constant are formatted to a different line


return (
    <>
      <h1>List</h1>
      {items.length === 0 && <p>No item found</p>}
      <ul className="list-group">
        {items.map((item) => (
          <li
            className="list-group-item"
            key={item}
            onClick={() => console.log("Clicked")}
          >
            {item}
          </li>
        ))}
      </ul>
    </>
  );
}

40:00 map the onClick items to what happens after click
Synthetic base event 40:50 
A wrapper around a native event object
return (
    <>
      <h1>List</h1>
      {items.length === 0 && <p>No item found</p>}
      <ul className="list-group">
        {items.map((item, index) => (
          <li
            className="list-group-item"
            key={item}
            onClick={(event) => console.log(event)}
          >
            {item}
          </li>
        ))}
      </ul>
    </>
  );
}

Type annotation in typescript:
Ex:
(event: MouseEvent)

 // Event handler
  const handleClick = (event: MouseEvent) => console.log(event);


Managing State 44:46

Highlight an item when clicked using a css class in bootstrap called active

Ex
className="list-group-item active"
(inclued an additional classname called ‘active’)

This highlights all of the list items, so we need a variable to keep track of the items’ indexes so we can highlight a selected item only. Declare a variable and initialize to -1 (no item selected) or 0 (first item selected)

let selectedIndex = 0;


className=”” // render content
className={} // allows us to render content dynamically

className={selectedIndex === index ? 'list-group-item active' : 'list-group-item'}

Now the first item is selected. Next we need it to change the selected index when we click on an item. Use a simple error function:

onClick={() => {
              selectedIndex = index;
            }}

Then let react know that the selectedIndex is going to have data or state that changes over time.

useState function, a hook- tap into built-in features in react

  // Hook
  const arr = useState(-1);
  arr[0]; // variable (selectedIndex)
  arr[1]; // updater function

When the state of a component changes, react will update the dom to match the new component state.

This allows each item to be active when clicked, keeping track of index numbers. Tells react that the state in our component will change over time.

import { useState } from "react";


function ListGroup() {
  let items = ["New York", "San Francisco", "Tokyo", "London", "Paris"];
  const [selectedIndex, setSelectedIndex] = useState(-1);


  return (
    <>
      <h1>List</h1>
      {items.length === 0 && <p>No item found</p>}
      <ul className="list-group">
        {items.map((item, index) => (
          <li
            className={
              selectedIndex === index
                ? "list-group-item active"
                : "list-group-item"
            }
            key={item}
            onClick={() => {
              setSelectedIndex(index);
            }}
          >
            {item}
          </li>
        ))}
      </ul>
    </>
  );
}


Each component will have its own state.

Passing Data via Props 50:50

We are showing a list of cities here, but what if we want to make a different type of list, like names or colors? We don’t want to have to recreate different components for each list.

How can we make components reusable? By using props or properties.

Properties (Props): the inputs to our components

Instead of defining these items in the list, we should be able to pass them as an input to this component, just like how we can call a function and give an argument.

We should be able to pass an object with 2 properties: 
items: [ ], headings: string
Do this using a typescript feature called interface
Using an interface we can define the shape or interface of an object
Using type annotation to specify the type of various properties
interface Props {
  items: string[];
  heading: string;
}

Typescript compiler is reminding us that we have forgotten certain properties

import { useState } from "react";


interface Props {
  items: string[];
  heading: string;
}


function ListGroup({ items, heading }: Props) {
  const [selectedIndex, setSelectedIndex] = useState(-1);


  return (
    <>
      <h1>{heading}</h1>
      {items.length === 0 && <p>No item found</p>}
      <ul className="list-group">
        {items.map((item, index) => (
          <li
            className={
              selectedIndex === index
                ? "list-group-item active"
                : "list-group-item"
            }
            key={item}
            onClick={() => {
              setSelectedIndex(index);
            }}
          >
            {item}
          </li>
        ))}
      </ul>
    </>
  );
}


export default ListGroup;


Passing Functions via Props 54:45

How to make something happen when a list item is selected
Do one size fits all
Don’t want to implement logic inside list-group component because it won’t be a reusable component anymore
The parent is our app component. When item is selected, it should notify the parent.

In ListGroup.tsx:
interface Props {
  items: string[];
  heading: string;
  // (item: string) => void
  onSelectItem: (item: string) => void; // onClick
}


function ListGroup({ items, heading, onSelectItem }: Props) {
  const [selectedIndex, setSelectedIndex] = useState(-1);


…………
            key={item}
            onClick={() => {
              setSelectedIndex(index);
              onSelectItem(item);
            }}


In App.tsx (parent):

import ListGroup from "./components/ListGroup";


function App() {
  let items = ["New York", "San Francisco", "Tokyo", "London", "Paris"];


  const handleSelectItem = (item: string) => {
    console.log(item);
  };


  return (
    <div>
      <ListGroup
        items={items}
        heading="Cities"
        onSelectItem={handleSelectItem}
      />
    </div>
  );
}


export default App;


State vs. Props 58:30

Props
Input passed to a component
Similar to function argos
Immutable- unchangeable, read-only (for example, in our list-group component, we should not change any of the properties there in the function. We should not add a new value for heading or any other props. An anti-pattern in react. Not functional)

State
Data managed by a component
Similar to local variables
Mutable- data that can change over time

Any time either changes, react will re-render the component and update the DOM accordingly

Passing Children 1:00:03

How to create a component that can accept children

get className for alert from getbootstrap.com

Display Alert Text

App.tsx

import Alert from "./components/Alert";


function App() {
  return (
    <div>
      <Alert text="Hello World" />
    </div>
  );
}


export default App;

Alert.tsx (created new component file in component folder)

interface Props {
  text: string;
}


const Alert = ({ text }: Props) => {
  return <div className="alert alert-primary">{text}</div>;
};


export default Alert;


// function Alert() {}


// Search ES7+ React/Redux/React-Native sn extension and add extension

Listgroup.tsx

import { useState } from "react";


interface Props {
  items: string[];
  heading: string;
  // (item: string) => void
  onSelectItem: (item: string) => void; // onClick
}


function ListGroup({ items, heading, onSelectItem }: Props) {
  const [selectedIndex, setSelectedIndex] = useState(-1);


  return (
    <>
      <h1>{heading}</h1>
      {items.length === 0 && <p>No item found</p>}
      <ul className="list-group">
        {items.map((item, index) => (
          <li
            className={
              selectedIndex === index
                ? "list-group-item active"
                : "list-group-item"
            }
            key={item}
            onClick={() => {
              setSelectedIndex(index);
              onSelectItem(item);
            }}
          >
            {item}
          </li>
        ))}
      </ul>
    </>
  );
}


export default ListGroup;


What if we have a longer alert and want to pass html content? It would be better if we could pass text as a child to this component so we don’t make the code ugly (too long, too much information)

In App.tsx, instead of:
  return (
    <div>
      <Alert text="Hello World" />
    </div>
  );

This is better:
  return (
    <div>
      <Alert>
        Hello World
      <Alert/>
    </div>
  );

And we also need to go back to our component, Alert.tsx, and insert a prop that all components support called children.

In Alert.tsx
interface Props {
  children: string;
}

and change all references to text from ‘text’ to ‘children’

interface Props {
  children: string;
}


const Alert = ({ children }: Props) => {
  return <div className="alert alert-primary">{children}</div>;
};


export default Alert;

Change alert content to html text:

In Alert.tsx

Change the children type from string to ReactNode
import { ReactNode } from "react";


interface Props {
  children: ReactNode;
}


const Alert = ({ children }: Props) => {
  return <div className="alert alert-primary">{children}</div>;
};


export default Alert;


// function Alert() {}


// Search ES7+ React/Redux/React-Native sn extension and add extension


-end: using the children prop, we can pass children to a component.-


Inspecting Components with React Dev Tools 1:05:11

Download Google Chrome extension: React Developer Tools




Exercise: Building a Button Component 1:07:18

Create a new file in components folder called Button.tsx
In Button.tsx, type shortcut rafc to populate with code
Complete code in Button.tsx
	import React from "react";


const Button = () => {
  return <button className="btn btn-primary">Button</button>;
};


export default Button;

Add button to App.tsx
import Alert from "./components/Alert";
import Button from "./components/Button";


function App() {
  return (
    <div>
      <Button>
      </Button>
    </div>
  );
}


export default App;


Update Button.tsx:
 	import React from "react";


interface Props {
  children: string;
}


const Button = ({ children }: Props) => {
  return <button className="btn btn-primary" onClick={onClick}
>{children}</button>;
};


export default Button;

In Button.tsx, add a new prop called onClick to make the button reusable. It is a function with no parameters that returns void.
	interface Props {
  children: string;
  onClick: () => void;
}

Update App.tsx to give the command for what to do when button is clicked (onClick)

	import Alert from "./components/Alert";
import Button from "./components/Button";


function App() {
  return (
    <div>
      <Button onClick={() => console.log("Clicked")}>My Button</Button>
    </div>
  );
}


export default App;                                                                                

Specify color in Button.tsx
	import React from "react";


interface Props {
  children: string;
  color?: "primary";     // ? makes it optional to specify color when used
  onClick: () => void;
}


const Button = ({ children, onClick }: Props) => {
  return <button className="btn btn-primary " onClick={onClick}
>{children}</button>;
};


export default Button;


Exercise: Showing an Alert 1:14:18

Bootstrap alerts https://getbootstrap.com/docs/5.3/components/alerts/#examples
Dismissing https://getbootstrap.com/docs/5.3/components/alerts/#dismissing

To make an alert dismissible:
<div class="alert alert-warning alert-dismissible fade show" role="alert">
  <strong>Holy guacamole!</strong> You should check in on some of those fields below.
  <button type="button" class="btn-close" data-bs-dismiss="alert" aria-label="Close"></button>
</div>


1:16:50- button click
When the button is clicked, it will call the function and setAlertVisibility will be set to true. Then the DOM will be updated and the alert will appear in the app.


import { useState } from "react";
import Alert from "./components/Alert";
import Button from "./components/Button";


function App() {
  const [alertVisible, setAlertVisibility] = useState(false);


  return (
    <div>
      {alertVisible && <Alert>My alert</Alert>}
      <Button onClick={() => setAlertVisibility(true)}>My Button</Button>
    </div>
  );
}


export default App;


Add alert-dismissible

When the x is clicked on the alert, setAlertVisibility should be set to false and the alert will disappear.

Alert.tsx
import { ReactNode } from "react";


interface Props {
  children: ReactNode;
  onClose: () => void;
}


const Alert = ({ children, onClose }: Props) => {
  return (
    <div className="alert alert-primary alert-dismissible">
      {children}
      <button
        type="button"
        className="btn-close"
        onClick={onClose}
        data-bs-dismiss="alert"
        aria-label="Close"
      ></button>
    </div>
  );
};


export default Alert;

App.tsx
import { useState } from "react";
import Alert from "./components/Alert";
import Button from "./components/Button";


function App() {
  const [alertVisible, setAlertVisibility] = useState(false);


  return (
    <div>
      {alertVisible && (
        <Alert onClose={() => setAlertVisibility(false)}>My alert</Alert>
      )}
      <Button onClick={() => setAlertVisibility(true)}>My Button</Button>
    </div>
  );
}


export default App;
