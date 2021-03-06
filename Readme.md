# terminator

  SSL termination in node.js

## Installation

```
$ npm install terminator
```

## API

```js
var Terminator = require('terminator');
var terminator = new Terminator();
 
var fs = require('fs');
var options = {
  key: fs.readFileSync('/root/server.key'),
  cert: fs.readFileSync('/root/server.crt'),
  ciphers: [
    "ECDHE-RSA-AES128-SHA256",
    "DHE-RSA-AES128-SHA256",
    "AES128-GCM-SHA256",
    "!RC4", // RC4 be gone
    "HIGH",
    "!MD5",
    "!aNULL"
].join(':'),
honorCipherOrder: true
};
 
terminator
  .listen(443)
  .forward(80, 'localhost')
  //.hideErrors() 
  .hideLogs();
 
terminator.start(options, function() {
  console.log('SSL terminator started!');
});
```

## License

(The MIT License)

Copyright (c) 2012 GoInstant, Inc.

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
