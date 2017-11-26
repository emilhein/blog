title: ES6 promises
tags:
  - Promises
  - ES6
  - node.js
  - js
categories: []
date: 2017-01-16 21:32:00
---
## Promise all

Promises are the savior for async requests. Previously you would have to use some sort of library (Bluebird or Q), but now with ES6 they are build in.

Now with a simple promise function looking like the following 

```javascript
const PromiseToSaveFile = (file) => {
    return new Promise((resolve, reject) => {
        return resolve('File saved with success')
    })
}

```

This is most basic promise function you could do. But now there are lots of cool stuff that you can do to control the flow of these async requests.
If you want them to run sequnece, you can do as following:
```javascript
const promiseToRetireveFile = (location, fileName) => {
    return new Promise((resolve, reject) => {
        return reject('Could not retrieve file')
    })
}


const PromiseToSaveFile = (file) => {
    return new Promise((resolve, reject) => {
        return resolve('File saved with success')
    })
}


promiseToRetireveFile('someDb', 'mylog.txt')
.then(PromiseToSaveFile('mylog.txt'))
.then(console.log)
.catch(err => {
    console.log(err) //Could not retrieve file
})

```

If you want a lot of promises to run in parrallel, or you dont care if some of them doesn't complete. You can use the build in Promise.all(), that takes an array of promises:
```javascript
let allMyPromises = []
allMyPromises.push(promiseToRetireveFile('someDb', 'mylog.txt'))
allMyPromises.push(PromiseToSaveFile('mylog.txt'))
Promise.all(allMyPromises)
.then(console.log) // => would end here if all promises are resolved
.catch(err => {
    console.log(err) // ends here as on of the promises failes
})

```
