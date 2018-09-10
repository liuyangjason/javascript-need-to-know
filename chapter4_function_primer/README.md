# Function
Functions are one of the fundamental building blocks in javascript.

Function is special object. I can say that you can not understand javascript clearly without understanding function concept.

## Syntax of Javascript Function
A javascript function is defined with 'function' keyword, followed by a name, followed by parentheses().  
```javascript
var myFunction= function [name](param1[, param2[,....paramN]]){ statement }; 
```

## function 'parameters' 
function parameters are the names listed in the parentheses.
## function 'arguments' 
function arguments are the real values received by the function when it is invoked.
## function expression 
function expression is a function expression is to store the function into a variable and then the variable is to be used as a function.  
```javascript
var x = function(a, b) { return a*b };  
```

## named function expression
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
```
