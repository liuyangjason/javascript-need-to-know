# Object
After learning what is JSON, let us jump into __Object__ , which is the most often used and most fundamental concept.

## What is an Object

see some examples first
~~~javascript
var foo = { name: 'Jason', sex: 'Male'};
var foo = [ "China", "U.S.A", "New Zealand"];
var foo = function abc() { return "Hello World"; };
~~~

As above sample shows, the javascript object is totally matched with format of JSON.

So Master JSON is the prerequisite to master javascript object.

__function__ is also object. 


Notes: Do not worry about the detail of __function__ key word used in the object. just ignore it. It will be described latter. So far, you only need to remember that 'function' is one special object. 

## How to create Object
1.  __Object Literals__ : it is most common used manner
~~~javascript
var mongo = {
    color: "bright yello",
    shape: "round"
}
~~~

2. __Object Constructor__ 
~~~javascript
var mongo = new Object();
mongo.color = "bright yello";
mongo.shape = "round";
~~~

3. __Constructor Pattern__
if you are from java ecosystem, you must want to abstract one class type named as 'Fruit' and create one concrete instance named as 'mongo'. 
~~~java
public class Fruit {
    private String color;
    private String shape;

    public String getColor() {
        return color;
    }

    public void setColor(String color) {
        this.color = color;
    }

    // shape is ignored here 
    // ......
}
~~~

In javascript ecosystem, __function__ is first class concept and it can do it in easier manner!

~~~javascript
function Fruit(theColor, theShape) {
    this.color = theColor;
    this.shape = theShape;
}

//test it
var mongo = new Fruit("bright yellow", "round");
console.log(mongo.color);
~~~

4. __Prototype Pattern__
we still use 'mongo' object as the example.
~~~javascript
function Fruit() {

}
Fruit.prototype.color = "dark";
Fruit.prototype.shape = "square";

//test it
var mongo = new Fruit();
mongo.color = "bright yellow";
mongo.shape = "round";

console.log(mongo.color);
~~~

# Object Properties
every object has properties. 
~~~ javascript
var foo = { name: 'Jason', sex: 'Male' }; // name and sex are properties of foo object
~~~

## How to access properties on an object
~~~ javascript
var foo = { name: 'Jason', sex: 'Male'};
console.log(foo.name); //it is ok to use dot notation to access property
console.log(foo[name]); //it is ok to use bracket notation to access property


var foo = ["China", "U.S.A", "New Zealand"];
console.log(foo[0]); // the only way to access property is to use bracket notation 
console.log(foo[2]); // the only way to access property is to use bracket notation


var foo = function abc() { return "Hello World"; }
console.log(foo()); // the only way to access the variable is to use parenthesis
~~~



## What will happen if accessing a proeroty does not exist on an object

~~~console
undefined
~~~

## How to add properties to object
~~~javascript
var foo1 = { name : "Jason" };
console.log(foo1.name); // Jason
console.log(foo1.sex); // error: undefined
foo1.sex = "Male"; //assign proeroty to foo object
console.log(foo1.sex); // Male


function Person(name) {
    this.name = name;
}
Person.prototype.sex = null;

var foo2 = new Person("Jason");
console.log(foo2.sex); // null
foo2.sex = "Male";
console.log(foo2.sex); // Male
~~~
