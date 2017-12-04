title: Cloudformation & Handlebars
author: Emil Hein
date: 2017-11-28 22:28:18
tags:
---
To begin with i wanted to make this about cloudformation itself, but instead i wanna do its as a subject of both cloudformation and a templating language.

Cloudformation has over time teached me, that doing too much logic in this non-programming-language is not ideal.
Therefore i found it easier to do combine it with a templating language. 

Lets see:

Handlebars test:
```js
const Handlebars = require('handlebars')

const Model = (input) => {
    state = input
    return Object.assign(state,
        someFunctions(state)
    )
}


const someFunctions = state => ({
    setCompile: (obj) => state.compiled = obj
})

let construct = {
    name: 'Joe',
    age: 25,
    comments: [1,2,4,5,6],
    template: `My name is {{name}}. I am a {{age}}
     {{#each comments}}        
      -->  {{this}}
     {{/each}}
     `,
    compiled: null
}
let newTestModel = Model(construct)


let source = newTestModel.template
const template = Handlebars.compile(source);
newTestModel.setCompile(template(newTestModel))
console.log(newTestModel.compiled);
```