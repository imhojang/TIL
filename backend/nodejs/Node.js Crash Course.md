# Node.js Crash Course

Node.js and Express are different

> Node.js is a runtime.
>
> Express is a framework that is often used with Node.js

Heroku : app hosting platform

---

## What is Node.js?

- Javascript Runtime (NOT a language or a framework)

- Built on the V8 Javascript engine (Same as Google Chrome)
- Written in C++
- Essentially allows us to <u>run Javascript code on the server</u>

## What you should know first

- JavaScript Fundamentals (Object, Arrays, Conditionals, etc)

<u>It may help to learn these first</u>

- HTTP (status codes, headers, etc)
- JSON
- Arrow functions
- Promises
- MVC Pattern

## Why use node?

- Fast, efficient, and highly scalabe
- Event driven, non-blocking I/O model
- Popular in the industry
- same language on the front and back end (JS)

## Non-blocking i/oj

- Works on a single thread using non-blocking I/O calls
- Supports tens of thousands concurrent connections
- Optimizes throughput & scalability in apps with many I/O operations
- All of this makes Node.js apps very fast & efficient

## NPM - Node package Manager

- Install 3rd party packages (frameworks, library, tools, etc)
- packages get stored in the "node_modules" folder
- All dependencies are listend in a "package.json" file
- NPM scripts can be created to run certain taks such as a run server.

`npm init` generates a package.json file

`npm install express` installs a package locally

`npm install -g nodemon` installs a package globally

## Node modules

- Node core modules (path, fs, http, etc)
- 3rd party modules/packages installed via NPM
- custom modules (files)

cost path = require('path');

const myFile = require('./myFile');

---

## Jumping RIght into some coding

Set up: Download Node.js from nodejs.org

1. create a `package.json` file by running `npm init`. 

2. running this command will ask you to do some initial set up.
3. default settings are good (hit enter for all)
4. this in turn creates a package.json with all the stuff in it.

One of the main purpose of package.json is to store all of the dependencies.

- If the application uses somethign you install from NPM then it needs to be listed here because if you move to another computer, another server. Running npm install thats gonna install  all the packages that are listed.

---

`npm install uuid`

small module, running this command will create an item under `dependencies` in package.json

##### `dev dependencies` : dependencies that are needed just for development

`nodemon` whcih will make it so that we dont have to keep restarting our server and i want to install that as a dev dependency

=>`npm install -D nodemon` === `npm installl --save-dev nodemon`

Running this will add nodemon as `devDependencies`.

---

#### Package-lock.json

This just tracks all of our dependencies with the versions and everything that we install comes from the NPM js .org repository, or website. That's where everything is stored in that registry. 

---

##### Module Wrapper Function

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  
  greeting() {
    console.log(`My name is ${this.name} and I am ${this.age}`);
  }
}

module.exports = Person;

---
  
// when you include a module like above, it's wrapped in what's called module wrapper function 

(function (exports, require, module, __filename, __dirname) {
  
 class Person {
    constructor(name, age) {
      this.name = name;
      this.age = age;
    }

greeting() {
      console.log(`My name is ${this.name} and I am ${this.age}`);
    }
  }

  module.exports = Person;
  
})
```

---

#### Why use "const Person = require('./person');"  instead of "import Person from './person';" to import?

node hasn't implemented this yet. 

if you want to be able to use this syntax, you actually have to implement Babel to compile it to ES6. THis is the last feature of ES6 that hasn't been perfected in node yet.

const Person = require('./person'); : **common JS**

import Person from './person' : **ES6** :: **unexpected identifier** error



---

## Node's core modules

### ... 