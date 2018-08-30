# Object
After learning what is JSON, let us jump into __Object__ , which is the most often used and most fundamental concept.

## What is an Object

see one example first
~~~javascript
var myFirstObject = { 
    firstName: "Jason", 
    age: 100,
    myFavoriateColor: function() {
        return ["red", "yellow"];
    }
};
~~~

As above sample shows, the javascript object is totally matched with format of JSON.

So Master JSON is the prerequisite to master javascript object.

Notes: Do not worry about the __function__ key word used in the object. just ignore it. It will be described latter. 


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

## How to access property of javascript object
see follow example
~~~javascript
console.log(myFirstObject.firstName); // it is Dot Notation
console.log(myFirstObject["firstName"]); // it is Bracket Notation
~~~
