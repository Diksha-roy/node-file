NODE.JS - FILE 

**Table of Content**

**Synchronous** **vs** **Asynchronous**
**Example**
**Open** **a** **File**
**Syntax**
**Parameters**
**Get** **File** **information**
**path**
**flags**
**mode**
**callback**
**Writing** **File**
**Reading** **File**
**Delete** **File**
**Closing** **File**
**Truncate** **File**
**Create** **Directory**
**Read** **Directory**
**Remove** **Directory**
**Example**
**Methods** **Reference**

Node implements File I/O using simple wrappers around standard POSIX
functions. Node File System *fs* module can be imported using following
syntax:

> var fs = require("fs")

**Synchronous** **vs** **Asynchronous**

Every method in fs module have synchronous as well as asynchronous form.
Asynchronous methods takes a lastparameter as completion function
callback and firstparameter of the callback function is error. Itis
preferred to use asynchronous method instead of synchronous method as
former never block the program execution where as the second one does.

**Example**

Create a textfile named **input.txt** having following content

> Tutorials Point is giving self learning content to teach the world in
> simple and easy way!!!!!

Letus create a js file named **main.js**having the following code.

> var fs = require("fs");
>
> // Asynchronous read
>
> fs.readFile('input.txt', function (err, data) { if (err) {
>
> return console.error(err); }
>
> console.log("Asynchronous read: " + data.toString()); });
>
> // Synchronous read
>
> var data = fs.readFileSync('input.txt'); console.log("Synchronous
> read: " + data.toString());
>
> console.log("Program Ended");

Now run the main.js to see the result:

> \$ node main.js

Verify the Output

> Synchronous read: Tutorials Point is giving self learning content to
> teach the world in simple and easy way!!!!!
>
> Program Ended
>
> Asynchronous read: Tutorials Point is giving self learning content to
> teach the world in simple and easy way!!!!!

Following section will give good examples on major File I/O methods.

**Open** **a** **File**

**Syntax**

Following is the syntax of the method to open a file in asynchronous
mode:

> fs.open(path, flags\[, mode\], callback)

**Parameters**

Here is the description of the parameters used:

> **path** - This is string having file name including path.
>
> **flags**- Flag tells the behavior of the file to be opened. All
> possible values have been mentioned below.
>
> **mode**- This sets the file mode *permissionandstickybits*, butonly
> if the file was created. Itdefaults to 0666, readable and writeable.
>
> **callback**- This is the callback function which gets two arguments
> *err*, *fd*.

**Flags**

Flags for read/write operations are:

||
||
||
||
||
||
||
||
||
||
||
||
||
||
||

**Example**

Letus create a js file named **main.js**having the following code to
open a file input.txtfor reading and writing.

> var fs = require("fs");
>
> // Asynchronous - Opening File console.log("Going to open file!");
> fs.open('input.txt', 'r+', function(err, fd) {
>
> if (err) {
>
> return console.error(err); }
>
> console.log("File opened successfully!"); });

Now run the main.js to see the result:

> \$ node main.js

Verify the Output

> Going to open file!
>
> File opened successfully!

**Get** **File** **information**

**Syntax**

Following is the syntax of the method to getthe information abouta file:

> fs.stat(path, callback)

**Parameters**

Here is the description of the parameters used:

> **path** - This is string having file name including path.
>
> **callback**- This is the callback function which gets two arguments
> *err*, *stats* where **stats**is an objectof fs.Stats type which is
> printed below in the example.

Apartfrom the importantattributes which are printed below in the
example, there are number of useful methods available in
**fs.Stats**class which can be used to check file type. These methods
are given in the following table.

||
||
||
||
||
||
||
||
||
||

**Example**

Letus create a js file named **main.js**having the following code:

> var fs = require("fs");
>
> console.log("Going to get file info!"); fs.stat('input.txt', function
> (err, stats) {
>
> if (err) {
>
> return console.error(err); }
>
> console.log(stats);
>
> console.log("Got file info successfully!");
>
> // Check file type
>
> console.log("isFile ? " + stats.isFile());
>
> console.log("isDirectory ? " + stats.isDirectory()); });

Now run the main.js to see the result:

> \$ node main.js

Verify the Output

> Going to get file info! { dev: 1792,
>
> mode: 33188, nlink: 1, uid: 48, gid: 48, rdev: 0,
>
> blksize: 4096, ino: 4318127, size: 97, blocks: 8,
>
> atime: Sun Mar 22 2015 13:40:00 GMT-0500 (CDT), mtime: Sun Mar 22 2015
> 13:40:57 GMT-0500 (CDT), ctime: Sun Mar 22 2015 13:40:57 GMT-0500
> (CDT) }
>
> Got file info successfully! isFile ? true
>
> isDirectory ? false

**Writing** **File**

**Syntax**

Following is the syntax of one of the methods to write into a file:

> fs.writeFile(filename, data\[, options\], callback)

This method will over-write the file if file already exists. If you
wantto write into an existing file then you should use another method
available.

**Parameters**

Here is the description of the parameters used:

> **path** - This is string having file name including path.
>
> **data**- This is the String or Buffer to be written into the file.
>
> **options**- The third parameter is an objectwhich will hold
> {encoding, mode, flag}. By default encoding is utf8, mode is octal
> value 0666 and flag is 'w'
>
> **callback**- This is the callback function which gets a single
> parameter err and used to to return error in case of any writing
> error.

**Example**

Letus create a js file named **main.js**having the following code:

> var fs = require("fs");
>
> console.log("Going to write into existing file");
> fs.writeFile('input.txt', 'Simply Easy Learning!', function(err) {
>
> if (err) {
>
> return console.error(err); }
>
> console.log("Data written successfully!");
>
> console.log("Let's read newly written data"); fs.readFile('input.txt',
> function (err, data) {
>
> if (err) {
>
> return console.error(err); }
>
> console.log("Asynchronous read: " + data.toString()); });
>
> });

Now run the main.js to see the result:

> \$ node main.js

Verify the Output

> Going to write into existing file Data written successfully!
>
> Let's read newly written data Asynchronous read: Simply Easy Learning!

**Reading** **File**

**Syntax**

Following is the syntax of one of the methods to read from a file:

> fs.read(fd, buffer, offset, length, position, callback)

This method will use file descriptor to read the file, if you wantto
read file using file name directly then you should use another method
available.

**Parameters**

Here is the description of the parameters used:

> **fd** - This is the file descriptor returned by file fs.open method.
>
> **buffer** - This is the buffer thatthe data will be written to.
>
> **offset** - This is the offsetin the buffer to startwriting at.
>
> **length** - This is an integer specifying the number of bytes to
> read.
>
> **position** - This is an integer specifying where to begin reading
> from in the file. If position is null, data will be read from the
> currentfile position.
>
> **callback**- This is the callback function which gets the three
> arguments, *err*, *bytesRead*, *buffer*.

**Example**

Letus create a js file named **main.js**having the following code:

> var fs = require("fs");
>
> var buf = new Buffer(1024);
>
> console.log("Going to open an existing file"); fs.open('input.txt',
> 'r+', function(err, fd) {
>
> if (err) {
>
> return console.error(err); }
>
> console.log("File opened successfully!"); console.log("Going to read
> the file");
>
> fs.read(fd, buf, 0, buf.length, 0, function(err, bytes){ if (err){
>
> console.log(err);
>
> }
>
> console.log(bytes + " bytes read");
>
> // Print only read bytes to avoid junk. if(bytes \> 0){
>
> console.log(buf.slice(0, bytes).toString()); }
>
> }); });

Now run the main.js to see the result:

> \$ node main.js

Verify the Output

> Going to open an existing file File opened successfully! Going to read
> the file
>
> 97 bytes read
>
> Tutorials Point is giving self learning content to teach the world in
> simple and easy way!!!!!

**Closing** **File**

**Syntax**

Following is the syntax of one of the methods to close an opened file:

> fs.close(fd, callback)

**Parameters**

Here is the description of the parameters used:

> **fd** - This is the file descriptor returned by file fs.open method.
>
> **callback**- This is the callback function which gets no arguments
> other than a possible exception are given to the completion callback.

**Example**

Letus create a js file named **main.js**having the following code:

> var fs = require("fs");
>
> var buf = new Buffer(1024);
>
> console.log("Going to open an existing file"); fs.open('input.txt',
> 'r+', function(err, fd) {
>
> if (err) {
>
> return console.error(err); }
>
> console.log("File opened successfully!"); console.log("Going to read
> the file");
>
> fs.read(fd, buf, 0, buf.length, 0, function(err, bytes){ if (err){
>
> console.log(err); }
>
> // Print only read bytes to avoid junk. if(bytes \> 0){
>
> console.log(buf.slice(0, bytes).toString()); }
>
> // Close the opened file.
>
> fs.close(fd, function(err){ if (err){
>
> console.log(err); }
>
> console.log("File closed successfully."); });
>
> }); });

Now run the main.js to see the result:

> \$ node main.js

Verify the Output

> Going to open an existing file File opened successfully! Going to read
> the file
>
> Tutorials Point is giving self learning content to teach the world in
> simple and easy way!!!!!
>
> File closed successfully.

**Truncate** **File**

**Syntax**

Following is the syntax of the method to truncate an opened file:

> fs.ftruncate(fd, len, callback)

**Parameters**

Here is the description of the parameters used:

> **fd** - This is the file descriptor returned by file fs.open method.
>
> **len** - This is the length of the file after which file will be
> truncated.
>
> **callback**- This is the callback function which gets no arguments
> other than a possible exception are given to the completion callback.

**Example**

Letus create a js file named **main.js**having the following code:

> var fs = require("fs");
>
> var buf = new Buffer(1024);
>
> console.log("Going to open an existing file"); fs.open('input.txt',
> 'r+', function(err, fd) {
>
> if (err) {
>
> return console.error(err); }
>
> console.log("File opened successfully!"); console.log("Going to
> truncate the file after 10 bytes");
>
> // Truncate the opened file. fs.ftruncate(fd, 10, function(err){
>
> if (err){ console.log(err);
>
> }
>
> console.log("File truncated successfully."); console.log("Going to
> read the same file");
>
> fs.read(fd, buf, 0, buf.length, 0, function(err, bytes){
>
> if (err){ console.log(err);
>
> }
>
> // Print only read bytes to avoid junk. if(bytes \> 0){
>
> console.log(buf.slice(0, bytes).toString()); }
>
> // Close the opened file. fs.close(fd, function(err){
>
> if (err){ console.log(err);
>
> }
>
> console.log("File closed successfully."); });
>
> }); });
>
> });

Now run the main.js to see the result:

> \$ node main.js

Verify the Output

> Going to open an existing file File opened successfully!
>
> Going to truncate the file after 10 bytes File truncated successfully.
>
> Going to read the same file Tutorials
>
> File closed successfully.

**Delete** **File**

**Syntax**

Following is the syntax of the method to delete a file:

> fs.unlink(path, callback)

**Parameters**

Here is the description of the parameters used:

> **path** - This is the file name including path.
>
> **callback**- This is the callback function which gets no arguments
> other than a possible exception are given to the completion callback.

**Example**

Letus create a js file named **main.js**having the following code:

> var fs = require("fs");
>
> console.log("Going to delete an existing file");
> fs.unlink('input.txt', function(err) {
>
> if (err) {
>
> return console.error(err); }
>
> console.log("File deleted successfully!"); });

Now run the main.js to see the result:

> \$ node main.js

Verify the Output

> Going to delete an existing file File deleted successfully!

**Create** **Directory**

**Syntax**

Following is the syntax of the method to create a directory:

> fs.mkdir(path\[, mode\], callback)

**Parameters**

Here is the description of the parameters used:

> **path** - This is the directory name including path.
>
> **mode**- This is the directory permission to be set. Defaults to
> 0777.
>
> **callback**- This is the callback function which gets no arguments
> other than a possible exception are given to the completion callback.

**Example**

Letus create a js file named **main.js**having the following code:

> var fs = require("fs");
>
> console.log("Going to create directory /tmp/test");
> fs.mkdir('/tmp/test',function(err){
>
> if (err) {
>
> return console.error(err); }
>
> console.log("Directory created successfully!"); });

Now run the main.js to see the result:

> \$ node main.js

Verify the Output

> Going to create directory /tmp/test Directory created successfully!

**Read** **Directory**

**Syntax**

Following is the syntax of the method to read a directory:

> fs.readdir(path, callback)

**Parameters**

Here is the description of the parameters used:

> **path** - This is the directory name including path.
>
> **callback**- This is the callback function which gets two arguments
> *err*, *files* where files is an array of the names of the files in
> the directory excluding '.' and '..'.

**Example**

Letus create a js file named **main.js**having the following code:

> var fs = require("fs");
>
> console.log("Going to read directory /tmp");
> fs.readdir("/tmp/",function(err, files){
>
> if (err) {
>
> return console.error(err); }
>
> files.forEach( function (file){ console.log( file );
>
> }); });

Now run the main.js to see the result:

> \$ node main.js

Verify the Output

> Going to read directory /tmp ccmzx99o.out
>
> ccyCSbkF.out employee.ser hsperfdata_apache test
>
> test.txt

**Remove** **Directory**

**Syntax**

Following is the syntax of the method to remove a directory:

> fs.rmdir(path, callback)

**Parameters**

Here is the description of the parameters used:

> **path** - This is the directory name including path.
>
> **callback**- This is the callback function which gets no arguments
> other than a possible exception are given to the completion callback.

**Example**

Letus create a js file named **main.js**having the following code:

> var fs = require("fs");
>
> console.log("Going to delete directory /tmp/test");
> fs.rmdir("/tmp/test",function(err){
>
> if (err) {
>
> return console.error(err);
>
> }
>
> console.log("Going to read directory /tmp");
> fs.readdir("/tmp/",function(err, files){
>
> if (err) {
>
> return console.error(err); }
>
> files.forEach( function (file){ console.log( file );
>
> }); });
>
> });

Now run the main.js to see the result:

> \$ node main.js

Verify the Output

> Going to read directory /tmp ccmzx99o.out
>
> ccyCSbkF.out employee.ser hsperfdata_apache test.txt

**Methods** **Reference**

Following is a reference of File System module available in Node.js. For
a further detail you can refer to official documentation.

||
||
||
||
||
||
||
||
||
||
||
||
||

||
||
||
||
||
||
||
||
||
||
||
||
||
||
||
||
||
||
||
||

||
||
||
||
||
||
||
||
||
||
||
||
||
||
||
||
||
||
||
||
||
||

||
||
||
||
||
||
||
||
||
||
||
||
||
||
||
||
||
||
||
||
||
||

||
||
||
||
||
||
||
||

> Processing math: 100%
