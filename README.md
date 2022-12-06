## DevTools - List of great tools that makes developers life easier
    This page will be updated with some interesting small tools for software developer to make their everyday job easier.
    
### To Master your read.md

https://guides.github.com/features/mastering-markdown/


## setup a github repo

### 1. Add an existing project folder to github repo


```javascript

git remote add origin https://github.com/bharathasdev/texto.git
git branch -M main
git push -u origin main

```
### 2. creating a new propject folder in local and pushing it to git hub

```javascript

echo "# texto" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/bharathasdev/texto.git
git push -u origin main

```

### 3. Mirroring / duplicating a repo with all branches and history

 ```javascript
 
 // from Original repo to New repo
 
 // 1. clone the original remote repository to local machine 
 // 2. Create a new remote repository
 // 3. From the local folder 
 	- cd original-repository(local)
	$ git push --mirror https://gitsite.com/yourusername/new-repository.git
	 where  https://gitsite.com/yourusername/new-repository.git is assumed as a new repository url
 
 ```
 Reference
 https://medium.com/cloud-native-the-gathering/how-to-mirror-copy-an-entire-existing-git-repository-into-a-new-one-3bb8faefad9e
 


#### 4. Basic Git Commands - Reference

git status

git diff

git add -p filename

commit message "Concise"

body - what is different from previous

git log

git clone

git branch branchname

git checkout branchname

git add filename

git commit -m "hdjhjh"

git push --set-upstream origin test


git merge branchname

git merge --abort

git rebase branch-B

## If you want a quick answer, here are the following commands to undo a git commit:

Undo the last commit and do not remove the changes:
git reset --soft HEAD~1

Undo the last commit and remove the changes (from disk):
git reset --hard HEAD~1

Undo a specific commit and do not remove the changes:
git reset --soft <commit-object-name>
	
Undo a specific commit and remove the changes (from disk):
git reset --hard <commit-object-name>
	
Once you have fixed the git index you can now fix the GitHub repository. Only one command is needed, and it is irrelevant which method you used to undo the original commit:

git push origin master --force

## Code to setup an Express - Server - 

```javascript

const express = require("express");
const bodyParser = require("body-parser");
const cors = require("cors");

const app = express();

var corsOptions = {
    origin: "http://localhost:8081"
};

app.use(cors(corsOptions));

// parse requests of content-type - application/json
app.use(bodyParser.json());

// parse requests of content-type - application/x-www-form-urlencoded
app.use(bodyParser.urlencoded({ extended: true }));

// simple route
app.get("/", (req, res) => {
    res.json({ message: "Welcome to bezkoder application." });
});

// set port, listen for requests
const PORT = process.env.PORT || 8080;
app.listen(PORT, () => {
    console.log(`Server is running on port ${PORT}.`);
});
	
## Nice Article to use Axios and JSON Server
	
https://zetcode.com/javascript/axios/

```

## Javascript Snippets

### Removing deuplicate from an Array

```Javascript


let arr = [1, 3, 5, 7, 3, 8, 1]

let result1 = [];
let result = [];

let len = arr.length;

// Method 1
arr.sort();

let lastval = ""

for(let j = 0; j < len; j++)
{
	
	if(arr[j] !== lastval){
 		result1.push(arr[j])
  }
  lastval = arr[j];

}

console.log("Method 1:" , result1)


// Method 2

for(let i = 0; i < len; i++)
{
		if(result.indexOf(arr[i]) === -1)
    {
    	result.push(arr[i])
    }
}
console.log("Method 2:" , result);


//  Method 3
let obj = {};

for(let i of arr)
{
	obj[i] = true;
}

let newArray = Object.keys(obj);

console.log("Method 3", newArray);


//  Method 4

let newArray2 = new Set(arr);

console.log("Method 4", [...newArray2])

```



#### Spread Operator
```javascript

const codeburst = 'CODEBURST'; // Line 1
const characters = [ ...codeburst ]; // Line 2
// [ 'C', 'O', 'D', 'E', 'B', 'U', 'R', 'S', 'T' ]

```

Creating copy of a new object

```javascript
const obj = { name: 'Foo', age: 22 };
const newObj = { ...obj }
console.log(newObj)
// { name: 'Foo', age: 22 }

```

Merging to objects with spread

```javascript

const obj1 = { name: ‘Granny Smith’, color: ‘green’, type:’Apple’};
const obj2 = { price: 0.20, origin: ‘France’ };
const merge = {…obj1, …obj2};
console.log(merge); 

Result:

{ 
  name: ‘Granny Smith’,
  color: ‘green’,
  type:’Apple’, 
  price: 0.20,
  origin:’France’ 
};

```

What happens if the objects to merge have common properties?

If you have common properties the priority will be right to left. The object the most at the right will have priority over the one at its left and so on.

```javascript
const obj1 = { name: ‘Granny Smith’, color: ‘green’ , type:’Apple’};
const obj2 = { name: ‘Golden Delicious’, price: 0.20, origin: ‘France’ }; 
const merge = {…obj1, …obj2}; 
console.log(merge); 
{ 
  name: ‘Golden Delicious’,
  color: ‘green’,
  type:’Apple’,
  price: 0.20,
  origin:’France’
}; */

```

#### Destructuring 

```javascript
const address = [221, 'Baker Street', 'London'];
const [ houseNo, , city ] = address;
console.log(houseNo, city)
// 221 'London'

```
#### Best way to round the number

Issue with normal toFixed(2)

Number((1.015).toFixed(2)); // wont give you the right results


```javascript
Object { given: "1.015", expected: "1.02", actual: "1.01" }
Object { given: "4.015", expected: "4.02", actual: "4.01" }
Object { given: "5.015", expected: "5.02", actual: "5.01" }
Object { given: "6.015", expected: "6.02", actual: "6.01" }
Object { given: "7.015", expected: "7.02", actual: "7.01" }
Object { given: "128.015", expected: "128.02", actual: "128.01" }
```
But,

With this below method you will get the correct results

Number(Math.round(1.005+'e2')+'e-2');

References:

https://www.sitepoint.com/number-tofixed-rounding-errors-broken-but-fixable/

https://modernweb.com/what-every-javascript-developer-should-know-about-floating-points/

https://www.jacklmoore.com/notes/rounding-in-javascript/


## Weird Javascript

The below article will explain the weird part 

https://github.com/denysdovhan/wtfjs#-motivation

https://www.smashingmagazine.com/2011/05/10-oddities-and-secrets-about-javascript/

## Synchronous vs Asynchronous

https://medium.com/linkit-intecs/what-is-synchronous-vs-asynchronous-in-node-js-4b45ee668e6f

## Node Plugins

#### To setup bootstrap for a project

Please run the below commands to install the relevant node packages

npm init -y

npm i gulp browser-sync gulp-sass --save -dev

npm i bootstrap jquery popper.js --save


##Important concepts of Javascript

### JavaScript prototypes

Every JavaScript function has a prototype property that is used to attach properties and methods. 
This property is not enumerable. It allows the developer to attach methods or member functions to its objects. JavaScript supports inheritance only through the prototype property. In case of an inherited object, the prototype property points to the object’s parent. A common approach to attach methods to a function is to use prototypes as shown below:

```Javascript

function Rectangle(x, y) {
     this._length = x;
     this._breadth = y;
}

Rectangle.prototype.getDimensions = function () {
     return { length : this._length, breadth : this._breadth };
};

Rectangle.prototype.setDimensions = function (len, bred) {
     this._length = len;
     this._breadth = bred;
};

```


### JavaScript private properties, using closures
JavaScript lets you define private properties by using the underscore prefix as shown in the above example. However, this does not prevent a user from directly accessing or modifying a property that is supposed to be private.
Defining private properties using closures will help you solve this problem. The member functions that need access to private properties should be defined on the object itself. You can make private properties using closures as shown below:

```Javascript
function Rectangle(_length, _breadth) {

     this.getDimensions = function () {
     return { length : _length, breadth : _breadth };
     };

     this.setDimension = function (len,bred) {
     _length = len;
     _breadth = bred
     };

}

```

### JavaScript currying

With a curried function, you can pass all of the arguments that the function is expecting and get the result, 
or you can pass only a subset of arguments and receive a function back that waits for the rest of the arguments. 
A simple example of a curry is given below:


```Javascript
var myFirstCurry = function(word) {
     return function(user) {
            return [word , ", " , user].join("");
     };
};

var HelloUser = myFirstCurry("Hello");
HelloUser("Rahul"); // Output: "Hello, Rahul"

// or

myFirstCurry("Hey, wassup!")("Rahul"); // Output: "Hey, wassup!, Rahul"

```
## JavaScript apply, call, and bind methods

### Call

```Javascript

var user = {
     name: "Rahul Mhatre",
     whatIsYourName: function() {
     console.log(this.name);
     }
};

user.whatIsYourName(); // Output: "Rahul Mhatre",
var user2 = {
     name: "Neha Sampat"
};

user.whatIsYourName.call(user2); // Output: "Neha Sampat"

```


### Apply


that apply is nearly the same as call. The only difference is that you pass arguments as an array and not separately. Arrays are easier to manipulate in JavaScript, opening a larger number of possibilities for working with functions. Here is an example using apply and call:

```Javascript

var user = {
     greet: "Hello!",
     greetUser: function(userName) {
     console.log(this.greet + " " + userName);
     }
};

var greet1 = {
     greet: "Hola"
};

user.greetUser.call(greet1,"Rahul") // Output: "Hola Rahul"
user.greetUser.apply(greet1,["Rahul"]) // Output: "Hola Rahul"

```


### Bind

The bind method allows you to pass arguments to a function without invoking it. 
A new function is returned with arguments bounded preceding any further arguments. Here is an example:

```Javascript

var user = {
     greet: "Hello!",
     greetUser: function(userName) {
     console.log(this.greet + " " + userName);
     }
};

var greetHola = user.greetUser.bind({greet: "Hola"});
var greetBonjour = user.greetUser.bind({greet: "Bonjour"});

greetHola("Rahul") // Output: "Hola Rahul"
greetBonjour("Rahul") // Output: "Bonjour Rahul"

```

	
## Promises and Callback
	
https://stackoverflow.com/questions/22519784/how-do-i-convert-an-existing-callback-api-to-promises

## CSS & Preprocessor Tools, Utilities and plugins

CSS clip path Maker - https://bennettfeely.com/clippy/





## Visual Code Extension

Live Sass Compiler - to compile saas to Css in real time

Live Server - Hot module Reload extension

! - will give you default HTML5 Template code

Auto close Tag

Auto Rename Tag

marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag

Better Comments

Bracket pair colorizer
css peek

ES7 react/ /redux Graphql/ GrapQL / React-Native snippets by dsznajder

ESlint

Es6 code snippet

Path Intellisense

Prettier Now

Pretty Json

Path Intellisense

code Time

Prettier - Code formatter

Material Icon Theme (Philipp Kief)

## React Native Extensions

React-Native/React/Redux snippets for es6/es7
EQuimper

React Native Tools (Microsoft)



## CSS Links and quick Reference

https://webdesign.tutsplus.com/tutorials/how-to-build-web-form-layouts-with-css-grid--cms-28776

## PIXI JS

Tutorial for using Spine with PIXI and webpack
https://medium.com/anvoevodin/lets-animate-your-pixijs-v5-game-with-spine-14dda65a0f41

## React Js

### Installing react in a simple way

Method 1:

npx create-react-app my-app

cd my-app

npm start


Method 2:

Hand coding and adding toplain htmlpage

https://reactjs.org/docs/add-react-to-a-website.html



### React functional component

```javascript
import React from 'react'
// es5
// function Greet() {
//   return <h1>Hello Vishwas</h1>
// }

// ES6 - Arrow function
const Greet = props => {
  return (
    <div>
      <h1>
        Hello {props.name} a.k.a {props.heroName}
      </h1>
      {props.children}
    </div>
  )
}

export default Greet

```
### React Class Component

```JavaScript

import React, { Component } from 'react'

class Welcome extends Component {
  render() {
    return <h1>Welcome {this.props.name} a.k.a {this.props.heroName}</h1>
  }
}

export default Welcome

```

### React class component and React portal example

ReactDOM.createPortal(
      this.props.children(jsx),
      targetDomOutOfReactDOMTree,
    );

```JavaScript

// These two containers are siblings in the DOM
const appRoot = document.getElementById('app-root');
const modalRoot = document.getElementById('modal-root');

class Modal extends React.Component {
  constructor(props) {
    super(props);
    this.el = document.createElement('div');
  }

  componentDidMount() {
    modalRoot.appendChild(this.el);
  }

  componentWillUnmount() {
    modalRoot.removeChild(this.el);
  }
  
  render() {
    return ReactDOM.createPortal(
      this.props.children,
      this.el,
    );
  }
}

class Parent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {clicks: 0};
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    // This will fire when the button in Child is clicked,
    // updating Parent's state, even though button
    // is not direct descendant in the DOM. 
    this.setState(prevState => ({
      clicks: prevState.clicks + 1
    }));
  }

  render() {
    return (
      <div onClick={this.handleClick}>
        <p>Number of clicks: {this.state.clicks}</p>
        <p>
          Open up the browser DevTools
          to observe that the button
          is not a child of the div
          with the onClick handler.
        </p>
        <Modal>
          <Child />
        </Modal>
      </div>
    );
  }
}

function Child() {
  // The click event on this button will bubble up to parent,
  // because there is no 'onClick' attribute defined
  return (
    <div className="modal">
      <button>Click</button>
    </div>
  );
}

ReactDOM.render(<Parent />, appRoot);


```

### Export default vs Named Export

## default Export

export default Greet; // (Greet.js)

While importing the export default as shown above, we can import with any name as shown below

import myGreet from "./Greet.js" // you can import with any name


## Named Export

export  Greet; // (Greet.js)

While importing the named export as shown above, we can import with only with exact name within curly braces as shown below

import {Greet} from "./Greet.js" // you can import with the same name between the curly braces



### React Class Component SetState, CallBack and PrevState

1. Always use setState method to update state. 
   Using the setState method will re-render the component
   
2. Any code that needs to be executed immediately after the SetState has to be sent as a Callback parameter(2nd Parameter)
3. If there are multiple SetState calls the React will call all at once. Multiple setState should use prevState property within an Arrow function.

Example shown below

```Javascript

import React, { Component } from 'react'

class Counter extends Component {

  constructor() {
    super()
    this.state = {
      count: 0
    }
  }

  increment() {
    this.setState((prevState) => ({
      count: prevState.count + 1
    }))
    // this.setState({
    //   count: this.state.count + 1
    // }, () => {
    //   console.log('Callback', this.state.count)
    // })
    // this.state.count = this.state.count + 1
    // console.log(this.state.count)
  }

  incrementFive() {
    console.log('Inside incrementFive')
    this.increment()
    this.increment()
    this.increment()
    this.increment()
    this.increment()
  }

  render() {
    return (
      <div>
        <div>Count - {this.state.count}</div>
        <button onClick={() => this.incrementFive()}>Increment</button>
      </div>
    )
  }
}

export default Counter

```


### Toggle
```javascript

const toggle = () => setOn(o => !o)

```

### prop drilling and Breaking a component into Multiple components

### Baseline

Prop drilling can be a good thing, and it can be a bad thing. Following some good practices as mentioned above, you can use it as a feature to make your application more maintainable. Good luck!

### What is prop drilling ?

Prop drilling (also called "threading") refers to the process you have to go through to get data to parts of the React Component tree. 
Let's look at a very simple example of a stateful component (yes, it's my favorite component example):

Case 1:

```javascript

function Toggle() {
  const [on, setOn] = React.useState(false)
  const toggle = () => setOn(o => !o)
  return (
    <div>
      <div>The button is {on ? 'on' : 'off'}</div>
      <button onClick={toggle}>Toggle</button>
    </div>
  )
}

```
Case 2: 
Above component split into 2 components

```javascript

function Toggle() {
  const [on, setOn] = React.useState(false)
  const toggle = () => setOn(o => !o)
  return (
    <Switch on ={on} onToggle = {toggle} />
  )
}


function Switch({on, onToggle}){

return (
    <div>
      <div>The button is {on ? 'on' : 'off'}</div>
      <button onClick={onToggle}>Toggle</button>
    </div>
    )
}

```


Case 3 - Splitting it into further more

```javascript

function SwitchMessage({on}){

return <div>The button is {on ? 'on' : 'off'}</div>
   
}

function SwitchButton({onToggle}){

return <button onClick={onToggle}>Toggle</button>
   
    
}

```

This is prop drilling. 
To get the on state and toggle handler to the right places, we have to drill (or thread) props through the Switch component. 
The Switch component itself doesn't actually need those values to function, but we have to accept and forward those props because its children need them.

Problems with property drilling.

This solves the problem of adding global variable erverywhere. everything stays in one place.
But it is easy if stays just few level deep. But it will become more hard to track and debug if the application grows bigger and it will become very hard to drill through many layers of the componenets. Removing the property or refactoring the data at the top might brake the child components and make it very hard to change and maintain


1. removing the unused property in the child rsults in passing unused data from top, if not removed
2. changing the property in the top, has to be updated throught the whole tree
3. renaming props will become difficult and neds updating all the children compoenents till the bottom.

example:

1. Refactor the shape of some data (ie: {user: {name: 'Joe West'}} -> {user: {firstName: 'Joe', lastName: 'West'}})

2. Renaming props halfway through (ie <Toggle on={on} /> renders <Switch toggleIsOn={on} />) making keeping track of that in your brain difficult.


Using a defaultProp for something that's actually required for the component to function properly is just hiding important errors and making things fail silently. 
So only use defaultProps for things that are not required.

Keep state as close to where it's relevant as possible to avoid prop drilling issues.

# Cheat Sheets - Quick Reference

### Javascript

https://websitesetup.org/javascript-cheat-sheet/

### CSS
https://websitesetup.org/wp-content/uploads/2019/11/wsu-css-cheat-sheet-gdocs.pdf

### BootStrap

https://websitesetup.org/bootstrap-cheat-sheet/

### 

https://websitesetup.org/python-cheat-sheet/


## Popular npm packages

1. moment js - npm install moment (https://momentjs.com/) 
   For formatting the date and time.
   

## Linux vs Windows commands
	
https://www.geeksforgeeks.org/linux-vs-windows-commands/#:~:text=Linux%20vs%20Windows%20Commands%20%20%20%20SNo.,Moving%20a%20file%20%2026%20more%20rows%20
   
   
## Node JS
	
https://blog.logrocket.com/reading-writing-json-files-nodejs-complete-tutorial/#:~:text=You%20can%20use%20the%20global%20require%20function%20to,be%20loaded%20again%20in%20the%20next%20server%20restart.
	
https://zellwk.com/blog/async-await-express/
https://masteringjs.io/tutorials/express/app-get

To list the node process thats running on particular port

``` Javascript

// On Windows

netstat -ano | findstr :3000
tskill typeyourPIDhere 

// on Linux or Mac

lsof -i tcp:3000

and to kill the process

kill -9 <process id>

```

## PM2 comands
``` Javascript
npm  i pm2

pm2 start app.js
pm2 restart app_name
pm2 reload app_name
pm2 stop app_name
pm2 delete app_name

pm2 [list|ls|status]

pm2 logs

pm2 monit


```
## Python - Setting virtual environment
```
pip install virtualenv

mkdir newproj
cd newproj
virtualenv venv

venv\scripts\activate

pip install Flask



```
	
### Python and node

###  How to call python script from node

	
https://medium.com/swlh/run-python-script-from-node-js-and-send-data-to-browser-15677fcf199f


