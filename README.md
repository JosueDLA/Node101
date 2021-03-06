# Learning Node.js 

Node.js is a cross-platform, open-source, runtime environment for the server layer. Based on the JavaScript programming language; is frequently used for building back-end services such as APIs (Application Programming Interfaces), Node is ideal for building real-time, scalable and data-intensive applications.

Node.js has an event-driven architecture, based on the Google V8 engine.

## Node Module System

### Modules

In Node every file is treated as a module. The local variables of each module are private unless they are explicitly exported.

Using export in Node

```js
const url = 'http://www.example.com/';

function log(){
    console.log('test');
}

module.exports.log = log;
module.exports.url = url;
```

Loading a module

```js
const myModule = require('./module');
```

### Events Module

Events are actions performed on the application, such as:

- Click on a button.
- Drag an icon.
- Key press.
- Write on a TextArea

Each event needs a listener funciton, which will be called when the event ocurs.

A callback is a function that is sent as an argument to another function. 

```js
const EventEmitter = require('events');
const emitter = new EventEmitter();

//Register a listener
emitter.emit('messageLogged', function(){
    console.log('Listener called');
});

//Raise an event
emitter.emit('messageLogged');
```

## Node Package Manager

GOTO [npm-demo](./npm-demo/README.md)

## Express

Express.js is a back-end framework for Node.js.

Install Express

```bash
> npm i express
```

### Express Demo

Basic RESTful API with Express and data validation using Joi.

Install Joi

```bash
> npm i joi
```

#### EndPoints

__GET:__ /api/courses
__GET:__ /api/courses/:id
__POST:__ /api/courses
__PUT:__ /api/courses/1
__DELETE:__ /api/courses/:id

### Environments

We can use the global object `process` to define and detect in what kind on environment we are running. To achieve this, we will need to use environment variables.

#### Environment Variables
Environment variables, as the name implies, are variables that descrive your environment; this variables are stored on your system.

In order to set an environment variable we need to use the export command.

```bash
> export KEY=value
```

#### NODE_ENV
NODE_ENV is a environment variable made popular by the Express web server framework, when a node application is run, it can check the value of the environment variable and do different things based on the value.

Print NODE_ENV value:
```js
// Option #1
console.log(`NODE_ENV: ${process.env.NODE_ENV}` );

// Option #2
// If undefined, it will return development.
console.log(app.get('env'));
```

### Configuration

Node-config organizes hierarchical configurations for your app deployments.

Install node-config

```bash
npm i config
```

Node-config allows us to create configuration files and override them depending on the environment we are running.

Configuration file sample

```js
{
    "name": "My App",
    "mail": {
        "host": "dev-mail"
    }
}
```

Access configuration data

```js
console.log('Application name: ' + config.get('name'));
console.log('Mail Server: ' + config.get('mail.host'));
```

#### Sensitive Information

Sensitive information should NOT be included in the configuration files. You can use environment variables instead.

```bash
> export app_password = 123
```

We use the custom-environment-variables.json file to map our environment variables to our properties.

> (New as of 1.1.0) Some deployment situations rely heavily on environment variables to configure secrets and settings best left out of a codebase. NODE_CONFIG lets you use a JSON string to deal with this, but sometimes simpler, flatter environment variables are better suited.

> To enable custom environment variables, create a configuration file, config/custom-environment-variables.json (or .yaml or .js or coffee) mapping the environment variable names into your configuration structure. For example:

```js
{
    "mail": {
        "password": "app_password"
    }
}
```

### Debugging

> Debug is a tiny debugging utility modelled after Node.js core's debugging technique.

```bash
> npm i debug
```

Set global variable
```bash
> export DEBUG=app:startup
```

> debug exposes a function; simply pass this function the name of your module, and it will return a decorated version of console.error for you to pass debug statements to. This will allow you to toggle the debug output for different parts of your module as well as the module as a whole.

```js
const startupDebugger = require('debug')('app:startup');
const dbDebugger = require('debug')('app:db');

// Testing degub app:db
dbDebugger('This is a dbDebugger log');

// Testing debug app:startup
startupDebugger('Startup Test...')
```

### Template Engine

A template engine is a specific type of module that allows us to return HTML.

> Pug is a high performance template engine heavily influenced by Haml and implemented with JavaScript for Node.js and browsers. For bug reports, feature requests and questions, open an issue. For discussion join the chat room.

```bash
> npm i pug
```

> Pug is a clean, whitespace sensitive syntax for writing html. 

```pug
html
    head
        title= title
    body
        h1= message
```

```js
res.render('index', { title: 'My App', message: 'Hello World' });
```