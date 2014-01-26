# emitter-context

This is a "fork" of node's [Events](http://nodejs.org/api/events.html) module with support for specifying a context for the handler

## API

Everything is the same as [Events](http://nodejs.org/api/events.html) except:

### emitter.addListener(event, listener, [ context ])
### emitter.on(event, listener, [ context ])
### emitter.once(event, listener, [ context ])

If the context is not specified, `this` (the emitter) will be used as the context.

```javascript

var Emitter = require('emitter-context')
  , x = new Emitter()
;

var context = { foo: 'bar' };

x.on('baz', function () {
    console.log(this.foo);
}, context);

x.emit('baz');
// true - There are listeners for `baz`
// 'bar'

```