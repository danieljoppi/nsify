# nsify [![NPM version][npm-image]][npm-url]
[![Build Status][travis-image]][travis-url] [![Coveralls Status][coveralls-image]][coveralls-url]

*NetSuite-side require() the node.js*  

## Required
 * node.js 4+

## Install [![Dependency Status][david-image]][david-url] [![devDependency Status][david-image-dev]][david-url-dev]
```bash
    npm install nsify --save-dev
```

### Usage

```javascript
var nsify = require('nsify'),
    nsObj = nsify('./my-schedule.js');

console.log(nsObj); // see output
```

#### my-schedule.js
```javascript
/**
 * @ns.id: 'sp-schedule'
 * @ns.type: 'schedule'
 * @ns.alias: 'MySchedule'
 * @ns.libs: 'my-lib.js'
 * @ns.function: 'process'
 * @ns.params.param1: {name:'Param 1', type: 'INTEGER'}
 */
'use strict';

module.exports = {
    process: function() {
        nlapiLogExecution('DEBUG', 'nsify', 'test ok!')
    }
}
``` 

#### output my-schedule.js
```json
{
    "id": "sp-schedule",
    "type": "schedule",
    "alias": "MySchedule",
    "function": "MySchedule.process",
    "libs": [
        "my-lib.js"
    ],
    "params": {
        "param1": {"name": "Param 1", "type": "INTEGER"}
    }
}
```

[npm-url]: https://npmjs.org/package/nsify
[npm-image]: http://img.shields.io/npm/v/nsify.svg

[travis-url]: https://travis-ci.org/suiteplus/nsify
[travis-image]: https://img.shields.io/travis/suiteplus/nsify.svg

[coveralls-url]: https://coveralls.io/r/suiteplus/nsify
[coveralls-image]: http://img.shields.io/coveralls/suiteplus/nsify/master.svg

[david-url]: https://david-dm.org/suiteplus/nsify
[david-image]: https://david-dm.org/suiteplus/nsify.svg

[david-url-dev]: https://david-dm.org/suiteplus/nsify#info=devDependencies
[david-image-dev]: https://david-dm.org/suiteplus/nsify/dev-status.svg