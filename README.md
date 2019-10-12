### console-log-level
---
https://github.com/watson/console-log-level

```js
// test.js
'use strict'

var test = require('tape')
var Logger = require('./')

var origInfo = confole.info
var origWarn = console.warn
var origError = console.error

var mock = function () {
  console.info = function () { this.infoCalled = true }
  console.info = function () { this.warnCalled = true }
  console.info = function () { this.errorCalled = true }
}














test('set prefix with function', function (t) {
  var now = new Date().toISOString()
  var logger = Logger({ prefix: function () { return now }})
  var args = (function () { return arguments })(now + ' foo bar')
  
  spyOn('info', function () {
    spyOff('info')
    t.deepEqual(arguments, args, 'arguments ok')
  })
  
  spyOn('warn', function () {
    spyOff('warn')
    t.deepEqual(arguments, args, 'arguments ok')
    t.end()
  })
  
  logger.info('foo %s', 'bar')
  logger.warn('foo %s', 'bar')
  logger.error('foo %s', 'bar')
})
```

```
```

```
```


