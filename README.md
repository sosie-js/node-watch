#Node-watch

This module will watch a directory **recursively** by default while trying to solve several problems when using the native [fs.watch()](http://nodejs.org/api/fs.html#fs_fs_watch_filename_options_listener):

1. When modifying a file inside a watched directory, the callback function will be triggered multiple times caused by junkie files generated by the editor; 
2. when modifying a watched single file, the callback function will only be triggered one time and then it is unwatched.

In current version it does not differentiate event like "rename" or "delete". Once there is a change, the callback function will be triggered.

### Installation

```bash
npm install node-watch
```

### Example

```js
var watch = require('node-watch');

watch('somedir_or_somefile', function(filename) {
  console.log(filename, ' changed.');
});
```

### Options

`recursive`:Watch it recursively or not (defaults to **true**). 

`followSymLinks`: Follow symbolic links or not (defaults to **false**).

`maxSymLevel`: The max number of following symbolic links, in order to prevent circular links (defaults to **3**). 


#### Usage

```js
watch('somedir', { recursive: false, followSymLinks: true }, function(filename) {
  console.log(filename, ' changed.');
});
```
