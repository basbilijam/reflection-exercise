# Reflection exercise

Explain programming concepts. Illustrate them with code

1. Variables, arrays and objects

Variables can have different datatypes, such as strings, booleans, numbers, objects, arrays.
An object is one datatype, that can have different properties and values.
An array can be best explained as a list.

```js

var exampleString = "Bas"
var exampleNumber = 20
var exampleBoolean = true
var exampleObject = {name: "Bas", age: 33}
var exampleArray = [1,2,3,4]

```

\2. Functions

Functions are blocks of code that are designed to perform a specific task. You can call it a set of instructions.
Functions can be declared and called as below:

```js

var exampleFunction = function (parameter) {
  return parameter * 3
}

exampleFunction(3)

```

Calling the above function with the parameter '3' will return '9'.

\3. Iteration loops (for and while)

Loops are a way to tell the computer to do something repeatedly.
Loops are good for repetitive iterations or other repetitive tasks, like searching though lists, arrays etc

A for loop tells the amount of times to do something.
With a for loop you can for example loop over the items in an array.


A for loop will run as long as the condition is true and we usually use a counter to make it run exactly the specified amount of times
```js

for (var i = 0; i < array.length; i++) {
  // do this action
}
```
A while loop loops while a certain condition is true.

```js

while (i < 100) {
    text += "The number is not 100 yet, it's: " + i;
    i++;
}

```

\4. Anonymous callback functions

A callback function is a function that is passed as a parameter to another function, and it is only called within that function,
after a certain event. Once the parent function is finished, the callback function is called.

An example of a callback function in jQuery:

```js

$("button").click(function(){
    $("p").hide("slow", function(){
        alert("The paragraph is now hidden");
    });
});

```

\5. Promises

Promises are used to time or postpone certain asynchronous events. In other words, they can be used to bring some structure in asynchronous code.
Promisified code is also easier to read/write, and using promises can avoid the 'christmas tree of doom'.

A promise declaration looks like this:

```js
new Promise(executor);
new Promise(function(resolve, reject) { ... });

```

It is also possible to use methods such as .then(), which initiates the action after the promise is fulfilled, and Promise.all, which triggers an action after all promises have been resolved.

\6. File system module

A native Node.js module, that allows the reading and writing of files.
Important methods within fs:
- readFile: to read files
- writeFile: to write data to files
- appendFile: add content to existing file

Some syntax:
```js

fs.readFile(fileName [,options], callback):
fs.readFile('TestFile.txt', function (err, data) {
    if (err) throw err;
  });

fs.writeFile('test.txt', 'Hello World!', function (err) {
    if (err)
      console.log(err);
    else
      console.log('Write operation complete.');
});

```

\7. Express

Express is a web application framework for Node.js that makes it easier to set up a web application, servers and manage http requests.

Below you find a code snippet that requires the express module, sets up an express app, sets a route to send 'hello world' to the browser, and sets up a server on port 3000.

```js

var express = require('express');
var app = express();

app.get('/', function (req, res) {
   res.send('Hello World');
})

app.listen(3000, (req, res) => {
  console.log('Server is running on port 3000')
})

```

\8. Body-parser

Is node.js middleware. This module parses information in forms in the browser, or json files.

After requiring it, set the app to use it, like so:

```js

app.use(bodyParser.urlencoded({ extended: false }))

app.use(bodyParser.json())

```

\9. HTML

The standard markup language for web pages. Stands for 'hyper text markup language'.

The building blocks of a website. The code looks like this:

```html

<!DOCTYPE html>
<html>
<head>
<title>Awesome page</title>
</head>
<body>

<h1>Awesome</h1>
<p>More awesomeness.</p>

</body>
</html>

```

 # HTML-markup is an Html template engine

 ```html

 #{set title,'MyPage' /}
 #{set menu,'home' /}
 #{extends '/model.html' /}
 <div>...</div>
 #{include '/menu-' + menu + '.html' /}
 <p>Bienvenue sur #{get title/}</p>

 ```

 ```js
 var markup = require('markup')
var express = require('express');
var app = express();

app.engine('html', markup.renderFile);
app.set('views', markup.directory); // specify the views directory
app.set('view engine', 'html'); // register the template engine

// What's on /dist folder is freely accessible
app.get('/dist', express.static(__dirname + '/dist'));
// For the rest, we use the engine
app.get('/', markup.lookFor)

app.listen(80);
```

\10. jQuery

jQuery is a JavaScript library that makes it easier to write JavaScript to make a webpage interactive.
To use jQuery, one needs to include the library in the page (link it in the HTML document).

jQuery code looks as follows:

```js

$(document).ready(function(){
    $("p").click(function(){
        $(this).hide();
    });
});

```

The dollar sign simply means we are using jQuery. The above code will hide an html paragraph('p') when it is clicked.

\11. Pug (discuss syntax and variables)

Pug is a view/template engine for node.js that makes it possible to render webpages on the server-side.
Templating engines make it possible to serve static template files in a web application. This makes it possible to work with variables in websites. The templates are compiled into html on the client-side. Working with templates makes it easier to design html pages.

Pug syntax in particular is a simplified form of html, in which indentation is extremely important.

Example:

```Pug

html
  head
    title= title
  body
    h1= message

```
In node, your view engine needs to be set to pug:

```js

app.set('view engine', 'pug')

```

\12. AJAX

AJAX stands for asynchronous JavaScript and XML. It is a concept that allows you to update a webpage without having to reload it, and to send data to the server in the background. This is a much used method nowadays. An example of its use is filling in information in a form, without the whole page reloading.

\13. Cookies

Cookies are small files that store information in the browser. They are used so the browser does not always have to reload all the information for a user, when it visits the same page again.

Make it quicker to load websites.
Store relevant user information.

```js
var express = require('express')
var cookieParser = require('cookie-parser')

var app = express()
app.use(cookieParser())
```

You can set cookies in both the front and backend. Mostly you do it in the front end in a script. You can include the js-cookie library to make this easier.

With this library you can easily set and get cookies like this:

```js
Cookies.set('name', 'value', { expires: 7 });

Cookies.get('name');

```

\14. Sequelize ORM

Sequelize is an ORM (object/relational mapper) module for Node. It makes it easier to work with SQL and Postgres databases through Node.js. Sequelize is promise based.

One can make database tables in Node.js through Sequelize.

The following code will make a 'beverages' database in postgres through a sequelize node object

```js

var db = new sequelize('beverages', 'bas', 'bas', {
  host: 'localhost',
  dialect: 'postgres'
} )

```

This will make a 'bottle' table within the database, with three keys (all strings).

```js

const Bottle = db.define ('bottle', {
  size: sequelize.STRING,
  color: sequelize.STRING,
  weight: sequelize.STRING
} )

```
The code below will make a first entry in the database. Sequelize will automatically give it a unique id and a 'createdate' value.

```js

Bottle.create( {
      size: "L",
      color: "green",
      weight: "heavy"
    }),
```
