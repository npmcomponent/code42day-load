*This repository is a mirror of the [component](http://component.io) module [code42day/load](http://github.com/code42day/load). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/code42day-load`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*
# load

Basic script loader.

The simplest and fastest way of loading scripts in modern browser is simply [listing them at the
end of the body element][1].

Use load only if for some reason you need to load your scripts dynamically - useful when
integrating various 3rd party widgets and snippets (google analytics, disqus, twitter API etc.) on
your page.

## Installation

Install with [component(1)](http://component.io):

    $ component install code42day/load

## API

```javascript
var load = require('load');
load('//topic.disqus.com/count.js');
```

Please note that scripts added to the DOM are `async` by default (see this [article][1] on script
loading) which means that they will start executing as soon as they load in pretty much random
order.

You can force async to `false` but some browsers will ignore it.

```javascript
load('//topic.disqus.com/count.js', false);
```

`load` returns [script element](https://developer.mozilla.org/en-US/docs/Web/API/HTMLScriptElement) - you can register `onerror` and `onload` callbacks

```javascript
load('//cdn/script.js').onload =  function () {
  console.log('my script loaded');
});
```

and:

```javascript
load('//cdn/script.js').onerror =  function (err) {
  console.log('cannot load script', err);
});
```

If you your callback work with IE use [segmentio/script-onload](https://github.com/segmentio/script-onload)

```javascript
var load  = require('load');
var onload = require('script-onload');

onload(load('//cdn/script.js'), function(err) {
  if (err) {
    console.log('Cannot load script', err);
  } else {
    console.log('Script loaded');
  }
});
```

## License

  MIT

[1]: http://www.html5rocks.com/en/tutorials/speed/script-loading/
