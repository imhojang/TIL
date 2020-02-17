# Express Crash Course

## Basic Server Syntax

```js
const express = require('express');

// Init express 
const app = express();

// Create your endpoints/route handlers
app.get('/', function(req,res) {
  res.send('Hello World!');
});

// Listen on a port
app.listen(5000);
```

## Basic Route Handling

```js
app.get('/', function (req, res) {
  // Fetch from database
  // Load pages
  // Return JSON
  // Full access to request & response
})
```

- Handling requests/routes is simple
- `app.get()`, `app.post()`, `app.put()`, `app.delete()`, etc
- Access to params, query strings, url parts, etc
- Express has a router so we can store routes in separate files and export
- We can parse incoming data with the Body parser

## Express Middleware

Middleware functions are functions that have access to the request and response object. Express has built in middleware but middleware also comes from 3rd party packages as well as custom middleware

- Execute any code
- make changes to the request/response objects
- end response cycle
- call next middleware in the stack

---

