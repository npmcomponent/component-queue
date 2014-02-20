*This repository is a mirror of the [component](http://component.io) module [component/queue](http://github.com/component/queue). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/component-queue`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*

# queue

  Task (function) queue with concurrency / timeout control.

## Installation

    $ component install component/queue

## Example

```js

var request = require('superagent');
var Queue = require('queue');
var q = new Queue({ concurrency: 3, timeout: 3000 });

var urls = [
  'http://google.com',
  'http://yahoo.com',
  'http://ign.com',
  'http://msn.com',
  'http://hotmail.com',
  'http://cloudup.com',
  'http://learnboost.com'
];

urls.forEach(function(url){
  q.push(function(fn){
    console.log('%s', url);
    request.get(url, function(res){
      console.log('%s -> %s', url, res.status);
      fn();
    });
  });
});
```

## License

  MIT
