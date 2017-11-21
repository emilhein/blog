title: Quokka
author: Emil Hein
tags: []
categories: []
date: 2017-11-19 13:30:00
---
## Quokka

I just fell over this extension to VS Code. The extension lets you "live" code with all the output and return values being printed. The is super awesome for prototyping or refactoring, as you can immediatly see if you solution returns what you expect.

Example

``` js
const someFunction = (myNumber) => {
    console.log(myNumber);
    return new Promise ((resolve, reject) => resolve(myNumber * 2))
}

someFunction(38)
.then(someFunction)
.then(someFunction)
.then(someFunction)
.then(someFunction)
.then(someFunction)
```

In VS Code this will look like this:
![VS Code view](/images/quokka.png)