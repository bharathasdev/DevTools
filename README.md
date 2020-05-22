# DevTools - List of great tools that makes developers life easier
    This page will be updated with some interesting small tools for software developer to make their everyday job easier.
    
## To Master your read.md

https://guides.github.com/features/mastering-markdown/

## Javascript Snippets

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


## React Js

### Installing react in a simple way

Method 1:

npx create-react-app my-app

cd my-app

npm start


Method 2:

Hand coding and adding toplain htmlpage

https://reactjs.org/docs/add-react-to-a-website.html
