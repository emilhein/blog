title: Compoisition
author: Emil Hein
date: 2017-11-23 18:02:00
tags:
---
Recetly iv'e beginning to like the following pattern instead of usual class inheritance.

Instead i like the following

``` js
const factory = name => {
    let state = {
        name,
        type: 'building'
    };
    // If you wanna include state ill let it be your choice
    return Object.assign(
        // state,
        {},
        factoryMethods(state)
    );
};


// could have one or many methods inside
const factoryMethods = state => ({
    getFactoryName: () => {
        return state.name
    },
    setFactoryName: (name) => {
        state.name = name
    }
});
```

Which with Quokka, could give you this
![Quokka showing you](/images/factory.png)