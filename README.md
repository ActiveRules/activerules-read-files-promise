# read-files-promise

```javascript
const readFiles = require('read-files-promise');

readFiles([
  'path/to/file0', // 'apple'
  'path/to/file1', // 'orange'
], {encoding: 'utf8'})
.then(buffers => {
  buffers; //=> ['apple', 'orange']
});
```

## Installation

[Use npm.](https://docs.npmjs.com/cli/install)

```
npm install read-files-promise
```

## API

```javascript
const readFiles = require('read-files-promise');
```

### readFiles(*filenames* [, *options*])

*filenames*: `Array` of `String` (file paths)  
*options*: `Object` or `String` (same as [fs.readFile](https://nodejs.org/api/fs.html#fs_fs_readfile_filename_options_callback)'s second argument)  
Return: `Object` ([Promise][promise])

It reads the files specified in its first argument.

When it finish reading all the files, it will be [*fulfilled*](https://promisesaplus.com/#point-26) with an array of the contents as its first argument. The order of the contents depends on the order of file paths.

It won't reject unless it fails horribly. Finding zero files can be a success.

```javascript
const readFiles = require('read-files-promise');

readFiles([
  'path/to/file0' // 'a'
  'path/to/file1' // 'b'
  'path/to/file2' // 'c'
]).then(onFulfilled, onRejected);

function onFulfilled(buffers) {
  buffers; //=> [<Buffer 61>, <Buffer 62>, <Buffer 63>]
};

function onRejected(err) {
  console.log('Cannot read the file.');
};
```

## License

Copyright (c) 2017 [Brian Winkers](https://github.com/bwinkers)

Licensed under [the MIT License](./LICENSE).

[promise]: https://promisesaplus.com/
