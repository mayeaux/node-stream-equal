# node-stream-equal

Test that two readable streams are equal to each other.

[![Dependency Status](https://david-dm.org/fent/node-stream-equal.svg)](https://david-dm.org/fent/node-stream-equal)
[![codecov](https://codecov.io/gh/fent/node-stream-equal/branch/master/graph/badge.svg)](https://codecov.io/gh/fent/node-stream-equal)

# Usage

```js
const streamEqual = require('stream-equal');
const fs = require('fs');

let readStream1 = fs.createReadStream(file);
let readStream2 = fs.createReadStream(file);
streamEqual(readStream1, readStream2, (err, equal) => {
  console.log(equal); // true
});
```


# Motive
Useful for testing. This method is faster and uses much less memory than buffering entire streams and comparing their content, specially for bigger files.

You could also get the hash sum of a stream to test it against another stream. But that would take up more CPU due to the hashing and would require a bit more data to be read if they are not equal.


# API
### streamEqual(readStream1, readStream2, [callback(err, equal)])

Will compare each `data` event on both streams, pausing when needed to keep them in sync. `equal` will be either `true` or `false` if there is no `err`. Returns a promise if callback is not given.


# Install

    npm install stream-equal


# Tests
Tests are written with [mocha](https://mochajs.org)

```bash
npm test
```
