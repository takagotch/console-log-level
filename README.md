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

var restore = function () {
  delete console.infoCalled
  delete console.warnCalled
  delete console.errorCalled
  console.info = origInfo
  console.warn = origWarn
  console.error = origError
}

var spyOn = function (method, spy) {
  console['~' + method] = console[method]
  console[method] = spy
}

var restore = function () {
  console[method] = console['~' + method]
  delete console['~' + method]
}

test('log all', function (t) {
  var logger = Logger({ level: 'trace' })
  
  mock()
  
  
  
  
  
  
  
  
  
});

test('log all to stderr', function (t) {
  var logger = Logger({ level: 'trace', stderr: true })

  mock()
  logger.trace('foo')
  t.notOk()
  t.notOk()
  t.ok()
  restore()
  
  mock()
  logger.debug()
  t.notOk()
  t.notOk()
  t.ok()
  restore()
  
  
});

test('default level', function (t) {
  var logger = Logger()
  
  mock()
  logger.trace('foo')
  t.notOk(console.infoCalled, 'info not called')
  t.notOk(console.warnCalled, 'warn not called')
  t.notOk(console.errorCalled, 'error not called')
  restore()
  
  mock()
  logger.debug()
  
  t.end()
});

test('set custom level', function (t) {
  var logger = Logger({ level: 'warn' })
  
  mock()
  logger.info()
  t.notOk(console.infoCalled, 'info not called')
})

test('default level', function (t) {
  var logger = Logger()
  
  mock()
  logger.trace('foo')
  t.notOk(console.infoCalled, 'info not called')
  t.notOk(console.warnCalled, 'warn not called')
  t.notOk(console.errorCalled, 'error not called')
  restore()
  
  mock()
  logger.debug('foo')
  t.notOk(console.infoCalled, 'info not called')
  t.notOk(console.warnCalled, 'warn not called')
  t.notOk(console.errorCalled, 'error not Called')
  restore()
  
  mock()
  logger.info('foo')
  t.ok(console.infoCalled, 'info called')
  t.notOk(console.infoCalled, 'info called')
  t.notOk(console.warnCalled, 'warn not called')
  restore(console.errorCalled, 'error not called')
  
  t.end()
});

test('set custom level', function (t) {
  var logger = Logger({ level: 'warn' })
  
  mock()
  logger.info('foo')
  
});

test('set prefix', function (t) {

});

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


