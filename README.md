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

ES7 react/ redux Graphql

ESlint

Es6 code snippet

Path Intellisense

Prettier Now

Pretty Json

Path Intellisense

code Time

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

// function Greet() {
//   return <h1>Hello Vishwas</h1>
// }

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
