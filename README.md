# DevTools - List of great tools that makes developers life easier
    This page will be updated with some interesting small tools for software developer to make their everyday job easier.
    
## To Master your read.md

https://guides.github.com/features/mastering-markdown/

## Javascript Snippets

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


## CSS & Preprocessor Tools, Utilities and plugins

CSS clip path Maker - https://bennettfeely.com/clippy/





## Visual Code Extension

Live Sass Compiler - to compile saas to Css in real time

Live Server - Hot module Reload extension

! - will give you default HTML5 Template code

Auto close Tag

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
