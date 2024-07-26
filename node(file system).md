
## NodeJs ##

## **Table of Content**

1. **What is node js**
2. **why do you use node js**
3. **Install node js**
4. **NPM (Node Package Manager)**
5. **Node REPL**
6. **Hello World Example**
7. **Process in Node**
8. **Export in File**
9. **Export in Directories**
10. **Installing Package**
11. **Package.Json**
12. **Local v/s Global**
13. **Import Module**
14. **What is Express**
15. **Getting Started With Express**
16. **Handling Requests**
17. **Routing**
18. **Installing Nodemon**   
19.  **Conclusion**
20.  **Reference Link**
21.  
## What is NodeJs.

_Node.js is a free, open-source, cross-platform JavaScript runtime environment that lets developers create servers, web apps, command line tools and scripts._

## why do you use node js.

Node.js is a popular JavaScript runtime built on Chrome’s V8 JavaScript engine that allows developers to create scalable and high-performance server-side applications. Here are some reasons why we use Node.js:

1. Fast and Scalable: Node.js is designed to handle high-traffic and high-concurrency applications, making it an excellent choice for real-time web applications, such as chatbots, gaming, and live updates.

2. Cross-Platform: Node.js is a cross-platform runtime, meaning it can run on multiple operating systems, including Windows, macOS, and Linux.

3. Large Ecosystem: Node.js has a massive ecosystem of packages and modules available through npm (Node Package Manager), making it easy to find and integrate libraries and tools for various tasks.

4. JavaScript Everywhere: Node.js allows developers to use JavaScript on both the client-side (browser) and server-side, making it a consistent and efficient choice for full-stack development.

5. Real-Time Capabilities: Node.js is well-suited for real-time applications that require immediate updates, such as live updates, live streaming, and real-time analytics.

6. Easy to Learn: Node.js is built on JavaScript, which is a widely known and popular programming language, making it relatively easy for developers to learn and adapt.

7. High Performance: Node.js is designed to handle high-performance applications, making it an excellent choice for applications that require fast response times and high throughput.

8. Cost-Effective: Node.js is an open-source technology, which means it is free to use and distribute, reducing costs and making it an attractive choice for startups and enterprises alike.


In summary, Node.js is a powerful and versatile technology that offers many benefits, including fast and scalable performance, cross-platform compatibility, a large ecosystem, and ease of use, making it an excellent choice for a wide range of applications.

## node js installation ##

## Windows/MacOS ##
 
1. Visit the [official Node.js website](https://nodejs.org/).
2. Download the LTS (Long Term Support) version.
3. Run the installer and follow the prompts.

## Linux ##
Open your terminal and run the following commands:
```bash
sudo apt update
sudo apt install nodejs
sudo apt install npm
```

You can verify the installation by running:


node -v
npm -v
## **NPM (Node Package Manager)** ##

NPM is the default package manager for Node.js. It allows you to install and manage third-party packages.

Installing a Package
To install a package, use the npm install command:

npm install package
Using a Package
Once installed, you can use the package in your Node.js application:
 ```js
 
 const package = require ("package");

package("Hello World!!", function (err, data) {
  if (err) {
    console.log("Something went wrong...");
    console.dir(err);
    return;
  }
  console.log(data);
});
 
 ```


## **Node REPL** ##

Node.Js REPL or Read-Evaluate-Print Loop is an interactive shell for the Node.js environment which means we can write any valid Javascript code in it.
```bash
tanu@diksha:~$ node
```

 Welcome to Node.js v20.15.0.
 
 Type ".help" for more information.


## **Process** ##
Process-This object provides information about, and control over,the current Node.js process.
``` bash
tanu@diksha:~$ node
```

Welcome to Node.js v20.15.0.

Type ".help" for more information.


```bash
> process.version
```
'v20.15.0'
```bash
> process.release
```

{
  name: 'node',

  lts: 'Iron',

  sourceUrl: 'https://nodejs.org/download/release/v20.15.0/node-v20.15.0.tar.gz',

  headersUrl: 'https://nodejs.org/download/release/v20.15.0/node-v20.15.0-headers.tar.gz'

}


Process.argv-returns an array containing the command-line arguments passed when the Node.js process
was launched.
```bash
tanu@diksha:~$ node
```

Welcome to Node.js v20.15.0.

Type ".help" for more information.

```bash
> process.argv
```

[ '/home/tanu/.nvm/versions/node/v20.15.0/bin/node' ]

```js
console.log(process.argv) //print process.agv
```
run file name
```bash
node app.js
```

## node js installation ##

## Windows/MacOS ##
 
1. Visit the [official Node.js website](https://nodejs.org/).
2. Download the LTS (Long Term Support) version.
3. Run the installer and follow the prompts.

## Linux ##
Open your terminal and run the following commands:
```bash
sudo apt update
sudo apt install nodejs
sudo apt install npm
```

You can verify the installation by running:


node -v
npm -v
## **NPM (Node Package Manager)** ##

NPM is the default package manager for Node.js. It allows you to install and manage third-party packages.

Installing a Package
To install a package, use the npm install command:

npm install package
Using a Package
Once installed, you can use the package in your Node.js application:
 ```js
 
 const package = require ("package");

package("Hello World!!", function (err, data) {
  if (err) {
    console.log("Something went wrong...");
    console.dir(err);
    return;
  }
  console.log(data);
});
 
 ```


## **Node REPL** ##

Node.Js REPL or Read-Evaluate-Print Loop is an interactive shell for the Node.js environment which means we can write any valid Javascript code in it.
```bash
tanu@diksha:~$ node
```

 Welcome to Node.js v20.15.0.
 
 Type ".help" for more information.


## **Process** ##
Process-This object provides information about, and control over,the current Node.js process.
``` bash
tanu@diksha:~$ node
```

Welcome to Node.js v20.15.0.

Type ".help" for more information.


```bash
> process.version
```
'v20.15.0'
```bash
> process.release
```

{
  name: 'node',

  lts: 'Iron',

  sourceUrl: 'https://nodejs.org/download/release/v20.15.0/node-v20.15.0.tar.gz',

  headersUrl: 'https://nodejs.org/download/release/v20.15.0/node-v20.15.0-headers.tar.gz'

}


Process.argv-returns an array containing the command-line arguments passed when the Node.js process
was launched.
```bash
tanu@diksha:~$ node
```

Welcome to Node.js v20.15.0.

Type ".help" for more information.

```bash
> process.argv
```

[ '/home/tanu/.nvm/versions/node/v20.15.0/bin/node' ]

```js
console.log(process.argv) //print process.agv
```
run file name
```bash
node app.js
```
**output**
[
  '/home/tanu/.nvm/versions/node/v20.15.0/bin/node',
  
  '/home/tanu/Desktop/backend/app.js'
  
]

We run process.argv in our code, it returns two values, one of which is the user's version information and the other is the location of the file.
Process.argv // pass argument 

```bash
tanu@diksha:~/Desktop/backend$ node app.js hello bye bye
```
[
  '/home/tanu/.nvm/versions/node/v20.15.0/bin/node',
  
  '/home/tanu/Desktop/backend/app.js',
  
  'hello',
  
  'bye',
  
  'bye'
]


## **Hello World Example** 

Let's create a simple "Hello World" program using Node.js.

Create a new file named app.js.

Add the following code:


   ```app.js
   let n = 5;
   for(let i=0; i<n; i++){
   console.log("hello world");
   }
   ```
Run node file name aap.js:

Example:

```bash
node app.js
```


**output**

tanu@diksha:~/Desktop/backend$ node app.js

hello world 0

hello world 1

hello world 2

hello world 3

hello world 4

## **Export in File**
require() - a built-in function to include external modules that exist in separate file.

module.exports- a special object.

**example usage to export in file**

file name math.js
```js
const sum = (a,b) => a+b;
const mul = (a,b) => a*b;
const g = 9.8;
const PI = 3.14;
module.exports = 123; //to export information to another file.
```
file name app.js
```js
const somevalue = require("./math"); // same dir to require file
console.log(somevalue);
```

```bash
tanu@diksha:~/Desktop/backend$ node app.js
```
**output**

123

**example**

export value and usage function
```math.js
const sum = (a,b) => a + b;
const mul = (a,b) => a * b;
const g = 9.8;
const PI = 3.14;


let obj = {
    sum:sum,
    mul: mul,
    g:g,
    PI:PI
}

module.exports = obj; //to export information to another file.
```
```app.js

const math = require("./math"); // same dir to require file

console.log(math.sum (2,2));
```

```bash
tanu@diksha:~/Desktop/backend$ node app.js 
```
**output**
4

run node file name app.js and require value math.js.

## **Export in Directories**

**example usage export dir**

dir name- student information > student1
          student information > student2
 ```js
// student1
module.export = {
name: "Diksha",
Roll no: "123",
};        
```
```js
// student1
module.export = {
name: "Tanusha",
Roll no: "124",
};        
```

To import the information of a directory into a file, a file named index.js has to be created and the execution starts from the node server uss file and the information is exported there.

```js
//index.js
const student1 = require("./student1");
const student1 = require("./student2");
```
let info = [student1,student2];

module.export = info;
```js
// app.js
const info = require("./student information")
console.log(info);
```
run server app.js
## **Installing Package**
npm is the standard package manager for node.js

npm install <-package name->
## **package.json**
`

The package.json file contains descriptive and functional metadata about a project,such
as a name version and dependencies.
```bash
npm init
```


## **Local v/s Global**

npm install -g <-package name->

npm install <-package name->

## **import module**
import {sum} from "./math.js"
We can't selectively load only the pieces we need with require but import,we can 
selectively load only the pieces we need, which can save memory..
loading synchronous for ''require' ' but can be asynchronous for 'import'.
```js
//math.js
//
export const sum = (a,b) => a+b;
export const sum = (a,b) => a*b;
export const g = 9.8;
export const PI = 3.14;
```
```js
//app.js
import{sum, PI} from "./math.js";
console.log(1,2);
```
run server but given output error it  defines package.json type module.
## **What is Express**
A Node.js web application framework that helps us to make web application 
it is used for server side programming.

**express uses in server side program**

1.listen for incoming requests.
2.pass request.
3.match response with routes.
4.response sent.
```
 npm install express
```
**Getting Started With Express**
example usage in express
```js
const express = require("express");
const app = express();

let port = 8080;

app.listen(port, () => {
console.log(`app is listening on port $(port)`);

});
```
Port - port the logical endpoint of a network connection that is used to exchange
information between a web server and a web client.
##  **Handling requests**

Node. js is a powerful way to handle incoming requests and send responses to clients. We can handle different HTTP methods, set response status codes and status messages, write response headers and body, and end the response process with response. end().
**example usage in handling requests**

  app.use
  ```js
  app.use((req.res) => {
  console.log("new incoming request");
  });
 ```
  **Routing**
   It is the process of selecting a path for traffic in a network or between or across multiple networks..
  ```js
  app.get("apple",(req,res) => {
  res.send({
  name: "apple",
   colour: "red",
  }):
  });
 ```
 **Installing Nodemon**
 
 To automatically restart the server with code changes.
 ```
  npm  install  -g Nodemon // install globally
 ```
## **Conclusion**

Node.js is a powerful platform for building server-side applications using JavaScript. With its non-blocking I/O and event-driven architecture, it is ideal for building scalable and efficient applications.

## **Reference Link**

https://www.w3schools.com/nodejs/nodejs_get_started.asp


https://nodejs.org/en/learn/getting-started/an-introduction-to-the-npm-package-manager
