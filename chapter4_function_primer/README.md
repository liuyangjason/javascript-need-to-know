# Function
Functions are one of the fundamental building blocks in javascript.

Function is special object. I can say that you can not understand javascript clearly without understanding function concept.

## Syntax of Javascript Function
A javascript function is defined with 'function' keyword, followed by a name, followed by parentheses().  
```javascript
var myFunction= function [name](param1[, param2[,....paramN]]){ statement }; 
```

### function 'parameters' 
function parameters are the names listed in the parentheses.
### function 'arguments' 
function arguments are the real values received by the function when it is invoked.
### function expression 
function expression is a function expression is to store the function into a variable and then the variable is to be used as a function.  
```javascript
var x = function(a, b) { return a*b };  
```

### named function expression
if you want to refer to this function inside the function body, you need to use named function expression. the name is then only local to the function body.
```javascript
var math = {
  'factorial': function factorial(n) {
    if (n <= 1)
      return 1;
    return n * factorial(n - 1);
  }
};
```

``` javascript
function myFunction(a, b) {
  return a * b;
}

console.log(myFunction(3, 2)); // 6

var funcExpression = function(a, b) {
  return a * b;
}

console.log(funcExpression(3, 2));
```
### Arrow function
```javascript
var elements = [
    'firstE',
    'secondE',
    'thirdE'
]
elements.map(element => console.log(element));//

var func1 = x => x * x; //concise body syntax, implied 'return'

var func2 = (x) => { return x * x; }; //with block body, explicit 'return' needed
```
if there is a single expression or statement in the function:
1.  using round bracket in the body is optional.
2.  using a return statement is optional.

#### Returning object literals in arrow function
```javascript
var func = () => { foo: 1 };
//calling func() returns undefined!

var func = () => ({ foo: 1 });
//calling func() returns object literal
```
## function use cases
### Use Case: method property of object
in the vast majority of cases, __function__ is used inside object as __method__. this is most common use case.
~~~javascript
var obj = {
    foo: function() {
        return 'bar';
    }
}
console.log(obj.foo()); //bar
~~~
### Use Case: Constructor Function

``` javascript
function Person(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
}
var p = new Person('Jason', 'Liu');
console.log(p.constructor == Person); //true
console.log(p instanceof Person); //true
```

### Use Case: Function as callback
calback function is also named as 'higher-order function'.

Let us run one classic callback function example in basic javascript

```javascript
var friends = ['Mike', 'Tom', 'Jason', 'Fisher'];

friends.forEach(function (eachName, index){
    console.log(index + 1 + '. ' + eachName);
});

friends.forEach((eachName, index) => {
    console.log(index + 1 + '. ' + eachName);
});
```
#### Why to use callback in javascript?
by callback function, we can run javascript in asynchronous manner.

Notes: as to closure and this related feature in callback, i will mention them in chapter on advanced function feature.

### Use Case: Immediately Invoked Function Expression aka IIFE
Let us now understand what an IIFE is and what problem does it solves

As the name implies, IIFE is the function that is executed by itself.

``` javascript
(function() {
    console.log("Hello IIFE");
})();
```
#### IIFE : when to use it
it can be used in scenarios where you need to run the function only once.

