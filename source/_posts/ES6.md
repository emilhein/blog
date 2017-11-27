title: ES6 methods
date: 2017-11-16 23:08:32
---
I would like to learn more ES6 features, and therefore I will post my findings here. It's just for fun and for my self to lookup.

# Quick into

## Let it be const

oh!. The let and the const declaration of variables. Most likely 94 % of all js declarations uses the classic

```javascript
var example = "this is a string";
```

This is all fine and good, but sometimes this gets confusing when dealing with scopes and duplicate declarations with the same name. For this purpose the word LET, comes to the rescue. look at the following pieces of code:

```javascript
var Animal = "Panda";

while(true){
  var Animal = "Rhino";
  console.log(Animal);  // -> Rhino
}

console.log(Animal);    // -> Rhino
```

and

```javascript
let Animal = "Panda";

while(true){
  let Animal = "Rhino";
  console.log(Animal);  // -> Rhino
}

console.log(Animal);    // -> Panda
```

This is due to the scoping of "let", which will only be in scope of the next bracket. In the case of "var", javascript uses something called Hoisting, which in short means that the code gets transformed into something like this:

```javascript
var Animal;

Animal = "Panda";

while(true){
  Animal = "Rhino";
  console.log(Animal);  // -> Rhino
}

console.log(Animal);    // -> Rhino
```

## Decunstruction

This is awesome for handling optional values to a method
```javascript
// default values in the method signature and descrructuring
// default values in the method signature and descrructuring
const deconstruc = ({land,size, price, address = "unknown"}) => {
    return `your house is: ${size} squarefeet, costs: ${price} and the address is ${address}`
}

var house = {
    'size': 123,
    'land': 2234,
    'address': 'Fifth avenue 2',
    'price': 1250000
};
var house2 = {
    'size': 123,
    'land': 2234,
    'price': 1250000

};
let house1Deconstruction = deconstruc(house);
let house2Deconstruction = deconstruc(house2);

console.log(house1Deconstruction); // Your house is: 123 squarefeet, costs: 1250000 and the address is Fifth avenue 2
console.log(house2Deconstruction); // Your house is: 123 squarefeet, costs: 1250000 and the address is unknown
```
## The spread or rest operator

These two new function are super cool opposites, that can be used in many way. Let me example: 

```javascript
let arrayOfValues = [1,2,3,4, 'five', 'six', {seven: 'eigth'}]

const restFunction = (...rest) => { // this is the rest 
    //as the rest is used, its an array for all parameters
    rest.map(value => console.log(`___ ${value}`))
}
restFunction('monkey')
restFunction(-2,-1,0)
restFunction(...arrayOfValues) // This is the spread
```