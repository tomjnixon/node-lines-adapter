NAME
====
lines-adapter - an evented, line-oriented I/O library for node.js

SYNOPSIS
========
<pre>
   var lines=require("lines-adapter");

   lines(stream, 'utf8')
    .on(
        'data',
        function(line) {
            // invoked for each line of input
        }
    )
    .end(
        'end',
        function(end) {
            // invoked at the end of stream
        }
    );
</pre>

DESCRIPTION
===========
Adapts a readable byte stream to produce a stream of lines.

Constructor
-----------
The lines-adapter module is a function which constructs line streams from byte streams and an optional
encoding argument. The supported encodings are those supported by Buffer.toString(). If no
encoding is specified, 'utf8' is assumed.

Event: 'data'
-------------
The 'data' event emits a string for each line of input in the adapted byte stream. The emitted
line does not contain a trailing \\n. A single trailing \\r will be removed, if present.

Event: 'end'
------------
Emitted when the stream has received an EOF. Indicates that no more 'data' events will happen.

EXAMPLES
========
Two examples are provided in the examples/ directory: count-lines and copy-lines.

<pre>
 $> echo foobar | node examples/count-lines.js
 0

 $> echo foobar | node exmaples/copy-lines.js
 foobar
</pre>

SIMILAR PACKAGES
================
Floby's [node-lines](https://github.com/Floby/node-lines) package provides similar functionality to this
library although it has a different philosophy. In particular node-lines emits 'line' events whereas 
node-lines-adapter emits 'data' events.



