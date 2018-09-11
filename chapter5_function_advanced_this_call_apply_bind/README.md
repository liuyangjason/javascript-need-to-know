After finishing the previous 4 chapters, it is time to start understanding the most important 3 features related to function and object.
1. __this__
2. __call__
3. __apply__
4. __bind__

It is no exaggeration to say that above 4 concepts are the cornerstone of mastering javascript.

# __this__
if you are from java ecosystem, you would be confused by the meaning of __this__ in javascript ecosystem.

In java ecosystem, __this__ is simple and it always point to the object instance. in other words, __this__ always points to itself. it is neat concept.

In javascript ecosystem, __this__ refers to the subject of the executing code. In other words, __this__ ALWAYS points to the object who is executing code. This statement sounds very vage. Let us go through it by example.

```javascript
console.log(this === window); // true. this is invoked in global scope. And the instance of global scope is window. so it is true.


(function test() {
    console.log(this === window);
})(); //true. this is inside one fuction, but the function is executed in global scope. so it is true.
```

Above 2 examples shows that the code snippet is executed in global scoping. so __this__ ALWAYS points to the executor __window__.

As we know, besides global scoping, there is functional scoping. what is __this__ when it comes to functional scoping? Let us go through it by example.

```javascript
function Person(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;

    this.displayFullName = function() {
        return this.firstName + ' ' + this.lastName;
    }
}

var person1 = new Person('Jason', 'Liu');
person1.displayFullName(); //the displayFullName function is invoked by the executor person1. So this refers to the executor person1.

var person2 = {
    firstName: 'Jason2',
    lastName: 'Liu2',
    checkExecutor: function() {
        console.log(this === window);
    }
}
person2.checkExecutor(); //false. the checkExecutor function is invoked by executor person2, rather than global object (window)
```

# __this__ inside __bind__ __call__  __apply__
__bind__ , __call__ , __apply__ are 3 special methods belong to Function.prototype. 

As previous mentions, every function is executed with one executor. (we use execution context to replace the term executor. Most developers are using execution context.)

when one execution context wants to borrow something from other execution context, it has to use __bind__  __call__  __apply__.

Let us see one example about how to borrow somehting from other execution context.
``` javascript
var x = 9;
var module = {
  x: 81,
  getX: function() { console.log(this.x); }
};

module.getX(); // the executor(execution context) is module. so the value is 81.

var retrieveX = module.getX;
retrieveX(); //oh, the executor(execution context) is global object window. so the value is 9.

var boundGetX = retrieveX.bind(module); //tell the retrieveX that switch the execution context to be module. 
boundGetX();// so the value is 81.
```

Ok, let us go through some most useful scenarios about __bind__  __call__  __apply__

# __bind__

## Use Case: set the value of 'this' to an specific object.
``` javascript
var Button = function(content) {
    this.content = content;
};

Button.prototype.click = function() {
    console.log(this.content + ' clicked');
}

var myButton = new Button('OK');
myButton.click(); // OK clicked

var looseClick = myButton.click;
looseClick(); // looseClick belongs to global execution context. 

var boundClick = myButton.click.bind(myButton);
boundClick(); // Although boundClick belongs to global execution context, yet it borrows 'this' from myButton.
```

## Use Case: reuse methods 
```javascript
//utility function to calculate remaining month fee for all of club members
function getMonthlyFee(fee) {
    var remaining = this.total - fee;
    this.total = remaining;
    return this.name + ' remaining balance:' + remaining;
}

var rachel = { name: 'Rachel', total: 500 };
var getRachelFee = getMonthlyFee.bind(rachel, 100); //reuse the method for michelle
getRachelFee(); //deduct 100  for rachel

var michelle = { name: 'Michelle', total: 300 };
var getMichelleFee = getMonthlyFee.bind(michelle, 100); //reuse the method for michelle
getMichelleFee(); //deduct 100 for michelle
```

## Use Case: curry method
``` javascript
function converter(toUnit, factor, offset, input) {
    offset = offset || 0;
    return [((offset+input)*factor).toFixed(2), toUnit].join(" ");
}
 
var milesToKm = converter.bind(undefined, 'km', 1.60936, 0);
var poundsToKg = converter.bind(undefined, 'kg', 0.45460, 0);
var farenheitToCelsius = converter.bind(undefined, 'degrees C',0.5556, -32);
 
milesToKm(10);            // returns "16.09 km"
poundsToKg(2.5);          // returns "1.14 kg"
farenheitToCelsius(98);   // returns "36.67 degrees C"
```

