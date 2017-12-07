title: Node 8 functions
author: Emil Hein
tags:
  - Node 8
  - promisify
  - Callback
categories: []
date: 2017-12-07 20:44:00
---
In node 8 a handy little function is the utils.promisify

Its very simple. It wraps an "old" callback styled function into a promise function:

```js
const {promisify} = require('util');

const isPositive = (number, callback) => { 
    if (number > 0) return callback(null, number)
    else return callback('not positive')

}
const isPositivePromise = promisify(isPositive);

isPositivePromise(33) /*?.*/
    .then(ans => isPositivePromise(ans*-1))
    .then(no => console.log('should not be here'))
    .catch(err => {
        console.log('err: ', err)
    }) 


```

This chain will end up in the catch, because of the second request too isPositivePromise.