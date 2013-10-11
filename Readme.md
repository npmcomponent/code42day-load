
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

````javascript
var load = require('load');
load('//topic.disqus.com/count.js');
````

Please note that scripts added to the DOM are `async` by default (see this [article][1] on script
loading) which means that they will start executing as soon as they load in pretty much random
order.

You can force async to `false` but some browsers will ignore it.

````javascript
load('//topic.disqus.com/count.js', false);
````

## License

  MIT

[1]: http://www.html5rocks.com/en/tutorials/speed/script-loading/
