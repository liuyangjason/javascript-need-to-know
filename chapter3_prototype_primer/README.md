# Javascript Prototype
in chapter2, we mentions the basic concept of javascript object. before jumping deeply into object, the __prototype__ concept must be understood clearly.

Notes: I will not introduce whole concept of __prototype__ in this chapter. I just mention the basic information of __prototype__ related to javascript object. __Prototype__ is heavily used in javascript function. In this chapter, i will not mention it. see latter chapter.

Every object in javascript has a prototype, when a message is sent to an object, javascript will attempt to find a property in the object firstly, if it can not find it then it will send this message to the object's prototype.


## __proto__ 
to understand prototype chain in javascript, the easest way is to see __ __proto__ __ property.
``` javascript
var alien = {
    kind: 'alien'
}

var humanity = {
    kind: 'humanity'
}

var json = {};

jason.__proto__ = alien; //assign alien as the prototype of jason
console.log(jason.kind); // alien
console.log(alien.isPrototypeOf(jason)); // true

jason.__proto__ = humanity; //assign humanity as the prototype of jason
console.log(jason.kind); // humanity
console.log(alien.isPrototypeOf(jason)); // false
```

notes: do not use __proto__ directly in production code. for test purpose, it is straightforward to use it.

## Object.create
In production code, we can use prototype in this manner.
``` javascript
var person = {
    kind: 'person'
}

var jason = Object.create(person);
console.log(jason.kind);

//we can also add new properties to the new object
var fisher = Object.create(person, {sex: {value: 'Male'}});
```

## Object.getPrototype
```javascript
var person = {
    kind: 'person'
}

var jason = Object.create(person);
Object.getPrototypeOf(jason); // person
```

