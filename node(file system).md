
# NodeJs

## **Table of Content**

1. **what is node js**
2. **why do you use node js**
3. **install node js**
4. **Hello World Example**
5. **Core Modules**
6. **HTTP Module**
7. **File System Module**
8. **(NPM)Node Package Manager**
9. **Synchronous** **vs** **Asynchronous** 
10. **Open** **a** **File**
11. **Syntax**
12. **Parameters**
13. **Get** **File** **information**
14.  **path**
15. **flags**
16. **mode**
17. **callback**
18. **Writing** **File**
19. **Reading** **File**
20. **Delete** **File**
21. **Closing** **File**
22. **Truncate** **File**
23. **Create** **Directory**
24. **Read** **Directory**
25. **Remove** **Directory**
26. **Methods** **Reference**
27.  **Conclusion**

## Wnat is NodeJs ?

_Node.js is a free, open-source, cross-platform JavaScript runtime environment that lets developers create servers, web apps, command line tools and scripts._

## why do you use node js

Node.js is a popular JavaScript runtime built on Chrome’s V8 JavaScript engine that allows developers to create scalable and high-performance server-side applications. Here are some reasons why we use Node.js:

1. Fast and Scalable: Node.js is designed to handle high-traffic and high-concurrency applications, making it an excellent choice for real-time web applications, such as chatbots, gaming, and live updates.

2. Event-Driven, Non-Blocking I/O: Node.js uses an event-driven, non-blocking I/O model, which allows developers to write asynchronous code that can handle multiple requests simultaneously, improving performance and responsiveness.

3. Cross-Platform: Node.js is a cross-platform runtime, meaning it can run on multiple operating systems, including Windows, macOS, and Linux.

4. Large Ecosystem: Node.js has a massive ecosystem of packages and modules available through npm (Node Package Manager), making it easy to find and integrate libraries and tools for various tasks.

5. JavaScript Everywhere: Node.js allows developers to use JavaScript on both the client-side (browser) and server-side, making it a consistent and efficient choice for full-stack development.

6. Real-Time Capabilities: Node.js is well-suited for real-time applications that require immediate updates, such as live updates, live streaming, and real-time analytics.

7. Easy to Learn: Node.js is built on JavaScript, which is a widely known and popular programming language, making it relatively easy for developers to learn and adapt.

8. High Performance: Node.js is designed to handle high-performance applications, making it an excellent choice for applications that require fast response times and high throughput.

9. Cost-Effective: Node.js is an open-source technology, which means it is free to use and distribute, reducing costs and making it an attractive choice for startups and enterprises alike.

10. Wide Adoption: Node.js is widely adopted by many popular companies, including LinkedIn, Netflix, Uber, and Walmart, making it a reliable and well-established technology.

In summary, Node.js is a powerful and versatile technology that offers many benefits, including fast and scalable performance, cross-platform compatibility, a large ecosystem, and ease of use, making it an excellent choice for a wide range of applications.

## node js installation ##

sudo apt install curl

curl -fsSL https://deb.nodesource.com/setup_14.x | sudo -E bash -

sudo apt-get install -y node js

node --version

To install Node.js, follow these steps:

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

## **Hello World Example** 

Let's create a simple "Hello World" HTTP server using Node.js.

Create a new file named app.js.
Add the following code:
   ```js
   const http = require('http');
   
   const hostname = '127.0.0.1';
   const port = 3000;
   
   const server = http.createServer((req, res) =  {
     res.statusCode = 200;
     res.setHeader('Content-Type', 'text/plain');
     res.end('Hello, World!\n');
   });
   
   server.listen(port, hostname, () => {
     console.log(`Server running at http://${hostname}:${port}/`);
   });
   
   ```
Run the server:

node app.js
Open your web browser and navigate to http://127.0.0.1:3000. You should see "Hello, World!".

## **Core Modules**

Node.js includes several core modules. Here are a couple of examples:

HTTP Module
The HTTP module allows Node.js to transfer data over the Hyper Text Transfer Protocol (HTTP).

Example usage:

  ```js
  const http = require('http');
  
  http.createServer((req, res) => {
    res.writeHead(200, {'Content-Type': 'text/html'});
    res.end('Hello, World!');
  }).listen(8080);
  ```

console.log('Server running at http://127.0.0.1:8080/');

## **File System Module** ##

The File System (fs) module allows you to work with the file system on your computer.

Example usage:

 ```js
 const fs = require('fs');
 
 // Read file
 fs.readFile('example.txt', 'utf8', (err, data) => {
   if (err) throw err;
   console.log(data);
 });
 
 // Write file
 fs.writeFile('example.txt', 'Hello Node.js', (err) => {
   if (err) throw err;
   console.log('File has been saved!');
 });
 ```
### **NPM (Node Package Manager)** ###

NPM is the default package manager for Node.js. It allows you to install and manage third-party packages.

Installing a Package
To install a package, use the npm install command:

npm install express
Using a Package
Once installed, you can use the package in your Node.js application:
 ```js
 
 const express = require('express');
 const app = express();
 
 app.get('/', (req, res) =  {
   res.send('Hello, World!');
 });
 
 app.listen(3000, () =  {
   console.log('Server is running on port 3000');
 });
 
 ```

## **Synchronous** **vs** **Asynchronous**

Every method in fs module have synchronous as well as asynchronous form.
Asynchronous methods takes a lastparameter as completion function
callback and firstparameter of the callback function is error. Itis
preferred to use asynchronous method instead of synchronous method as
former never block the program execution where as the second one does.

**Example**

Create a textfile named **input.txt** having following content

 Letus create a js file named **main.js**having the following code.
 ```js
 var fs = require("fs");
 
 // Asynchronous read
 
  fs.readFile('input.txt', function (err, data) { if (err) {
 
  return console.error(err); }
 
  console.log("Asynchronous read: " + data.toString()); });
 
 // Synchronous read
 
  var data = fs.readFileSync('input.txt'); console.log("Synchronous
 read: " + data.toString());
 
  console.log("Program Ended");
 ```

Now run the main.js to see the result:
```js
node main.js
```

Verify the Output



  Program Ended
 

Following section will give good examples on major File I/O methods.

## **Open** **a** **File**

**Syntax**

Following is the syntax of the method to open a file in asynchronous
mode:

  fs.open(path, flags\[, mode\], callback)

### **Parameters**

Here is the description of the parameters used:

  **path** - This is string having file name including path.
 
  **flags**- Flag tells the behavior of the file to be opened. All
  possible values have been mentioned below.
 
  **mode**- This sets the file mode *permissionandstickybits*, butonly
  if the file was created. Itdefaults to 0666, readable and writeable.
 
  **callback**- This is the callback function which gets two arguments
  *err*, *fd*.

**Flags**

Flags for read/write operations are:

**Example**

Letus create a js file named **main.js**having the following code to
open a file input.txtfor reading and writing.
 
  ```js
   var fs = require("fs");
  
   // Asynchronous - Opening File console.log("Going to open file!");
   fs.open('input.txt', 'r+', function(err, fd) {
  
   if (err) {
  
   return console.error(err); }
  
   console.log("File opened successfully!");
   });
 ```

Now run the main.js to see the result:

  \$ node main.js

Verify the Output

  Going to open file!
 
  File opened successfully!

## **Get** **File** **information**

**Syntax**

Following is the syntax of the method to getthe information abouta file:

  fs.stat(path, callback)

## **Parameters**

Here is the description of the parameters used:

  **path** - This is string having file name including path.
 
  **callback**- This is the callback function which gets two arguments
  *err*, *stats* where **stats**is an objectof fs.Stats type which is
  printed below in the example.

Apartfrom the importantattributes which are printed below in the
example, there are number of useful methods available in
**fs.Stats**class which can be used to check file type. These methods
are given in the following table.

## **Example**

Letus create a js file named **main.js**having the following code:
 ```js
 var fs = require("fs");
 
  console.log("Going to get file info!"); fs.stat('input.txt', function
 (err, stats) {
 
 if (err) {
 
  return console.error(err); }
 
  console.log(stats);
 
 console.log("Got file info successfully!");

 // Check file type
 
 console.log("isFile ? " + stats.isFile());
 
  console.log("isDirectory ? " + stats.isDirectory()); });
 ```

Now run the main.js to see the result:

  \$ node main.js

Verify the Output

  Going to get file info! { dev: 1792,
 
  mode: 33188, nlink: 1, uid: 48, gid: 48, rdev: 0,
 
  blksize: 4096, ino: 4318127, size: 97, blocks: 8,
 
  
 
  Got file info successfully! isFile ? true

 isDirectory ? false

## **Writing** **File**

**Syntax**

Following is the syntax of one of the methods to write into a file:

  fs.writeFile(filename, data\[, options\], callback)

This method will over-write the file if file already exists. If you
wantto write into an existing file then you should use another method
available.

**Parameters**

Here is the description of the parameters used:

 **path** - This is string having file name including path.

 **data**- This is the String or Buffer to be written into the file.

 **options**- The third parameter is an objectwhich will hold
 {encoding, mode, flag}. By default encoding is utf8, mode is octal
 value 0666 and flag is 'w'

  **callback**- This is the callback function which gets a single
  parameter err and used to to return error in case of any writing
  error.

**Example**

Letus create a js file named **main.js**having the following code:
 ```js
  var fs = require("fs");
 
 console.log("Going to write into existing file");
  fs.writeFile('input.txt', 'Simply Easy Learning!', function(err) {
 
 if (err) {
 
 return console.error(err); }
 
 console.log("Data written successfully!");
 
  console.log("Let's read newly written data"); fs.readFile('input.txt',
  function (err, data) {
 
 if (err) {
 
 return console.error(err); }
 
  console.log("Asynchronous read: " + data.toString()); });
 
  });
 ```

Now run the main.js to see the result:

  \$ node main.js

Verify the Output

  Going to write into existing file Data written successfully!
 
  Let's read newly written data Asynchronous read: Simply Easy Learning!

## **Reading** **File**

**Syntax**

Following is the syntax of one of the methods to read from a file:

  fs.read(fd, buffer, offset, length, position, callback)

This method will use file descriptor to read the file, if you wantto
read file using file name directly then you should use another method
available.

**Parameters**

Here is the description of the parameters used:

  **fd** - This is the file descriptor returned by file fs.open method.
 
  **buffer** - This is the buffer thatthe data will be written to.
 
  **offset** - This is the offsetin the buffer to startwriting at.
 
  **length** - This is an integer specifying the number of bytes to
  read.
 
  **position** - This is an integer specifying where to begin reading
  from in the file. If position is null, data will be read from the
  currentfile position.
 
  **callback**- This is the callback function which gets the three
  arguments, *err*, *bytesRead*, *buffer*.

**Example**

Letus create a js file named **main.js**having the following code:

  ```js
   var fs = require("fs");
  
  var buf = new Buffer(1024);
  
   console.log("Going to open an existing file"); fs.open('input.txt',
   'r+', function(err, fd) {
  
  if (err) {
  
  return console.error(err); }
  
   console.log("File opened successfully!"); console.log("Going to read
   the file");
  
   fs.read(fd, buf, 0, buf.length, 0, function(err, bytes){ if (err){
  
   console.log(err);
  
   }
  
   console.log(bytes + " bytes read");
  
   // Print only read bytes to avoid junk. if(bytes \  0){
  
   console.log(buf.slice(0, bytes).toString()); }
  
  }); });
 ```

Now run the main.js to see the result:

  \$ node main.js

Verify the Output

 Going to open an existing file File opened successfully! Going to read
the file

97 bytes read

Tutorials Point is giving self learning content to teach the world in
 simple and easy way!!!!!

## **Closing** **File**

**Syntax**

Following is the syntax of one of the methods to close an opened file:

 fs.close(fd, callback)

**Parameters**

Here is the description of the parameters used:

 **fd** - This is the file descriptor returned by file fs.open method.

**callback**- This is the callback function which gets no arguments
other than a possible exception are given to the completion callback.

**Example**

Letus create a js file named **main.js**having the following code:
 ```js
  var fs = require("fs");
 
 var buf = new Buffer(1024);
 
  console.log("Going to open an existing file"); fs.open('input.txt',
  'r+', function(err, fd) {
 
  if (err) {
 
 return console.error(err); }
 
  console.log("File opened successfully!"); console.log("Going to read
  the file");
 
  fs.read(fd, buf, 0, buf.length, 0, function(err, bytes){ if (err){
 
 console.log(err); }
 
  // Print only read bytes to avoid junk. if(bytes \  0){
 
  console.log(buf.slice(0, bytes).toString()); }
 
  // Close the opened file.
 
  fs.close(fd, function(err){ if (err){
 
  console.log(err); }
 
 console.log("File closed successfully."); });
 
  }); });
```

Now run the main.js to see the result:

  \$ node main.js

Verify the Output

  Going to open an existing file File opened successfully! Going to read
  the file
 
  Tutorials Point is giving self learning content to teach the world in
  simple and easy way!!!!!
 
  File closed successfully.

## **Truncate** **File**

**Syntax**

Following is the syntax of the method to truncate an opened file:

  fs.ftruncate(fd, len, callback)

**Parameters**

Here is the description of the parameters used:

 **fd** - This is the file descriptor returned by file fs.open method.

 **len** - This is the length of the file after which file will be
 truncated.

 **callback**- This is the callback function which gets no arguments
 other than a possible exception are given to the completion callback.

**Example**

 Letus create a js file named **main.js**having the following code:
 ```js
  var fs = require("fs");
 
 var buf = new Buffer(1024);
 
  console.log("Going to open an existing file"); fs.open('input.txt',
  'r+', function(err, fd) {
 
 if (err) {
 
  return console.error(err); }
 
 console.log("File opened successfully!"); console.log("Going to
  truncate the file after 10 bytes");

  // Truncate the opened file. fs.ftruncate(fd, 10, function(err){
 
  if (err){ console.log(err);
 
  }
 
  console.log("File truncated successfully."); console.log("Going to
  read the same file");
 
  fs.read(fd, buf, 0, buf.length, 0, function(err, bytes){
 
 if (err){ console.log(err);
 
  }
  
  // Print only read bytes to avoid junk. if(bytes \  0){
 
  console.log(buf.slice(0, bytes).toString()); }
 
  // Close the opened file. fs.close(fd, function(err){
 
 if (err){ console.log(err);
 
 }
 
 console.log("File closed successfully."); });
 
  }); });
 
 });
 ```

Now run the main.js to see the result:

  \$ node main.js

Verify the Output

  Going to open an existing file File opened successfully!
 
  Going to truncate the file after 10 bytes File truncated successfully.
 
  Going to read the same file Tutorials
 
  File closed successfully.

**Delete** **File**

**Syntax**

Following is the syntax of the method to delete a file:

  fs.unlink(path, callback)

**Parameters**

Here is the description of the parameters used:

  **path** - This is the file name including path.
 
  **callback**- This is the callback function which gets no arguments
  other than a possible exception are given to the completion callback.

**Example**

Letus create a js file named **main.js**having the following code:
 ```js
  var fs = require("fs");
 
 console.log("Going to delete an existing file");
  fs.unlink('input.txt', function(err) {
 
  if (err) {
 
  return console.error(err); }
 
  console.log("File deleted successfully!");
  });
  ```

Now run the main.js to see the result:

\$ node main.js

Verify the Output

  Going to delete an existing file File deleted successfully!

**Create** **Directory**

**Syntax**

Following is the syntax of the method to create a directory:

  fs.mkdir(path\[, mode\], callback)

**Parameters**

Here is the description of the parameters used:

  **path** - This is the directory name including path.
 
  **mode**- This is the directory permission to be set. Defaults to
  0777.
 
  **callback**- This is the callback function which gets no arguments
  other than a possible exception are given to the completion callback.

**Example**

Letus create a js file named **main.js**having the following code:
 ```js
  var fs = require("fs");
 
  console.log("Going to create directory /tmp/test");
  fs.mkdir('/tmp/test',function(err){
 
  if (err) {
 
  return console.error(err); }
 
 console.log("Directory created successfully!"); 
 });
 ```

Now run the main.js to see the result:

  \$ node main.js

Verify the Output

  Going to create directory /tmp/test Directory created successfully!

## **Read** **Directory**

**Syntax**

Following is the syntax of the method to read a directory:

  fs.readdir(path, callback)

**Parameters**

Here is the description of the parameters used:

  **path** - This is the directory name including path.
 
  **callback**- This is the callback function which gets two arguments
  *err*, *files* where files is an array of the names of the files in
  the directory excluding '.' and '..'.

**Example**

Letus create a js file named **main.js**having the following code:
 ```js
 var fs = require("fs");

 console.log("Going to read directory /tmp");
 fs.readdir("/tmp/",function(err, files){

 if (err) {

 return console.error(err); }

 files.forEach( function (file){ console.log( file );

 }); });
 ```

Now run the main.js to see the result:

  \$ node main.js

Verify the Output

  Going to read directory /tmp ccmzx99o.out
 
  ccyCSbkF.out employee.ser hsperfdata_apache test
 
  test.txt

## **Remove** **Directory**

**Syntax**

Following is the syntax of the method to remove a directory:

  fs.rmdir(path, callback)

**Parameters**

Here is the description of the parameters used:

  **path** - This is the directory name including path.
 
  **callback**- This is the callback function which gets no arguments
  other than a possible exception are given to the completion callback.

**Example**

Letus create a js file named **main.js**having the following code:
 ```js
 var fs = require("fs");

 console.log("Going to delete directory /tmp/test");
 fs.rmdir("/tmp/test",function(err){

if (err) {

return console.error(err);

}

 console.log("Going to read directory /tmp");
 fs.readdir("/tmp/",function(err, files){

 if (err) {

return console.error(err); }

 files.forEach( function (file){ console.log( file );

}); });

});
```

Now run the main.js to see the result:

  \$ node main.js

Verify the Output

  Going to read directory /tmp ccmzx99o.out
 
  ccyCSbkF.out employee.ser hsperfdata_apache
  
## **Conclusion**

Node.js is a powerful platform for building server-side applications using JavaScript. With its non-blocking I/O and event-driven architecture, it is ideal for building scalable and efficient applications.


 
