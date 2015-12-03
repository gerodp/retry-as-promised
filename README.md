# retry-as-promised

```sh
$ npm install --save retry-as-promised
```

Retry a failed promise

```js
var retry = require('retry-as-promised');

// Will call the until max retries or the promise is resolved.
return retry(function () {
  return promise;
}, {
  max: 3, // maximum amount of tries
  timeout: 10000 // throw if no response or error within milisecnd timeout, default: undefined,
  match: [ // Must match error signature (ala bluebird catch) to continue
    Sequelize.ConnectionError,
    'SQLITE_BUSY'
  ],
  stepoffBase: 1000 // Initial backoff duration in ms. Default: 100,
  backoffExponent: 1.5 // Exponent to increase backoff each try. Default: 1.1
});
```

## Tested with

- Bluebird