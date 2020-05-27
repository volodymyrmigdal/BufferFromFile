
# BufferFromFile [![Build Status](https://github.com/Wandalen/BufferFromFile/workflows/Build%20&%20Test/badge.svg)](https://github.com/Wandalen/BufferFromFile/actions?query=workflow%3A%22Build+%26+Test%22)

Native module for Nodejs providing convenient means for using files as standard ArrayBuffer making mmap behind the scene.
BufferFromFile uses mmap to map file from hard drive to memory returning ArrayBuffer or TypedBuffer which can be manipulated just like ordinary buffer.
mmap() creates a new mapping in the virtual address space of the calling process.
During mmap operation all performance issues addressed operation system, so it's nearly fastest way to get data from / store on hard drive in Java Script. This method of data access do zero copy, unlike others.
Just like [native](http://man7.org/linux/man-pages/man2/mmap.2.html) version of the routine BufferFromFile accept ( protection ), ( flags ), ( offset ), ( size ) and even ( advise ) parameters each of which has default value so no need to pass the implicitly.

BufferFromFIle works on Windows, OSX, Linux and other Unix-like systems.
The module doesn't depend of module nan and does not support deprecated versions of Nodejs.
The module can convert a file to standard ArrayBuffer or any kind of TypedBuffer. Nonstandard Nodejs Buffer is supported also.

### Usage:

```
npm install
node sample/Sample.js
```


### Sample

```javascript

var buffer = BufferFromFile( filePath ).Uint8Array();

// let's edit the first byte

buffer[ 0 ] = 48 + Math.round( Math.random()*9 );

// print the buffer

console.log( 'buffer.length :', buffer.length );
console.log( 'buffer.toString :', buffer.toString() );

// unmap file

BufferFromFile.unmap( buffer );

```
