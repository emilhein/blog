title: Composing functions
author: Emil Hein
date: 2018-02-09 23:10:33
tags:
---
Hi there,

Earlier in the post about classes vs composition i mention some of the same ideas briefly.

The basic idea with a **compose** or a **pipe** function is, that it takes an arbitrary number of functions and passes the return values from one to the next. **compose** does it from rigth to left and **pipe** does it from left to rigth.

First example without composing is:
```js
const function1 = input => `${input} m^2`
const function2 = input => `I would like a house that is more than ${input} big`

console.log(function2(function1(2))) // I would like a house that is more than 2 m^2 big

```

Already with one function passed into the other it looks a bit silly. If you image having more input functions, it quickly becomes very unreadable. 

The same exmpla with a compose function:
```js
const function1 = input => `${input} m^2`
const function2 = input => `I would like a house that is more than ${input} big`

const compose = (...fns) =>
    fns.reverse().reduce((prevFn, nextFn) =>
        value => nextFn(prevFn(value)),
        value => value
    );
const example = compose(
    function2,
    function1
);    
console.log(example(2)); // I would like a house that is more than 2 m^2 big
```

Now that was a lot more code, to do the same thing, but.
If you already have the compose function you can start building easy to read function flows, that passes output from function as input to the next function.

Finally.. Lodash also has a version of compose that can make the whole thing a lot more smooth:

```js
import * as _ from 'lodash'

const function1 = input => `${input} m^2`
const function2 = input => `I would like a house that is more than ${input} big`

const lodashWay = _.flowRight(function2, function1);


console.log(lodashWay(2)) // I would like a house that is more than 2 m^2 big

```

Nothing left to say!
