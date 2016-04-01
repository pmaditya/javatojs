---
layout: post
title:  "Javascript Objects"
date:   2016-03-31 18:49:41 -0700
categories: javascript
---

Overview : 
what does object oriented programming do ? 
How to use objects in Javascript ? 
this keyword ? If not used what happens to that ? 
Javascript constructor ? 
How to use prototypes ? 
how to use static methods? 
How to access static methods without creating an object ? 

In Object oriented programming, objects behave as first class citizens. An object can hold some data and it allows to perform some actions using that data. 
`Data + Actions = Object`

Javascript support the OOP and let us see how we can create objects in Javascript. I want to create a Vehicle class and I want to maintain the `numberOfWheels` and `engineType` each vehicle has : 

Naive Apprach
{% highlight javascript %}
var vehicle = {
  "numberOfTyres": 4,
  "engineType": "gasoline"
};

console.log(vehicle);
{% endhighlight %}

The `vehicle` variable is internally represented as an object in javascript.

```javascript
[object Object] {
  engineType: "gasoline",
  numberOfTyres: 4
}
```

Now I want to define a `Class` which provides the functionality to store 2 properties and perform some actions on it. 

```javascript
function Vehicle(numberOfTyres, engineType){
  this.tyres = numberOfTyres;
  this.engine = engineType;
}

var car = new Vehicle(4, "gasoline");
console.log(car);
```
The above code creates a function with name `Vehicle` and takes two parameters. This function acts like a `Constructor` and in the code we call it using `new Vehicle(4, "gasoline")` to create an object from it. The output of the console says that it creates an object.

```javasscript
[object Object] {
  engine: "gasoline",
  tyres: 4
}
"gasoline"
4
```

what happens when we use `new` keyword ?
//TODO fill the text here.

Let us add some methods or functions to our `Vehicle` object. We create functions just like any other regular variables

```javascript
function Vehicle(numberOfTyres, engineType){
  this.tyres = numberOfTyres;
  this.engine = engineType;
  
  this.toString = function(){
    return("this vehicle has "+ this.tyres + " with engine model "+ this.engine);
  };
  
 }
//create vehicle object and call toString() method
var car =  new Vehicle(4, "gasoline");
console.log(car.toString());
```

The `toString()` method is called and it returns the following output.

```javascript
"this vehicle has 4 with engine model gasoline"
```

The problem with the above code is that it creates `toString()` function variable for every object that it creates. This method does not require to store as its implementation is same for all the objects, there is a need to define it in a syntax where you dont create it for each and every time. 

Javascript provides a hidden prototype object to create this. To create a method which does not create function variable for each object we have to use prototype 

```javascript
function Vehicle(numberOfTyres, engineType){
  this.tyres = numberOfTyres;
  this.engine = engineType;
  }

Vehicle.prototype.toString =  function(){
    return("this vehicle has "+ this.tyres + " with engine model "+ this.engine);
  };
var car =  new Vehicle(4, "gasoline");

console.log(car.toString());
```

The output will be shown as following

```javascript
"this vehicle has 4 with engine model gasoline"
```

