title: Js validation
author: Emil Hein
tags:
  - Validation
  - Js
  - node
  - Joi
  - types
categories: []
date: 2017-12-20 18:27:00
---
Hi. Validation in javascript can be kinda tricky, since its not a strongly typed language. So how do we get around this?
 - Glad you as!
 
 There are, as with all javascript patterns, a million ways of doin it. Here is one. I use Joi to validate my input parameters.

The example below is for a lambdafunction (See my post about lambda functions)

Lets start simple: 

`lambdaHandler.js`
```js 
let myModel = require('./myModel.js')
exports.handler = (event, context, callback) => {
    try {
        const body = JSON.parse(event.body);
    } catch (error) {
        let errorMsg = 'Could not parse input';
        callback(null, response.BadRequest(errorMsg));
    }
    const MyFirstModel = myModel(body)
};
```

`myModel.js`
```js
const myModel = input => {
    let state = {
        name: input.name,
        age: input.age,
        website: input.website
    };
    return Object.assign(state);
};

module.exports = {
	myModel
}
```
Now if we want to trust this model, we have to make sure that whatever we put into it, has the "type" or values that we want.