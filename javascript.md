# Javascript main topic 

 ## Function
------
 Function is more than a normal function unlike in orther languages, a function can be assigned to a varible(expression),declare with key word function(declaration), passed around as an argument to another function(callback function), can also be returned from another(closure).Es6 has invoked the arrow function which doesn't has 'this' and argument parameter.

 #### Hoisting
All variable declarations using var and function declaration are lifted to the top of their current scope regardless of the actual declaration has been made. However, a key thing to note is that only thing that gets moved to the top is the variable declarations, not the actual value given to the variable.And if there are a function and a variable with same name, the function will be overwritten by variables.

#### IIFE
It stands for Immediarely Invoked Function Expression, is a common JavaScript design pattern used by most popular libraries(jQuery, Backbone.js). It's composed with a function declararion inside a parenthesis and following a parenthesis. it can help to keep variable private, clear global environment, aliasing variables, capturing the global object and optimization for minfication

#### bind apply and call
 - bind: &nbsp; it return a new function with provided value and context
 - call: &nbsp; it executes the function with provided context and parameter
 - apply: &nbsp; it executes the function with provided context and parameter as array

#### scope
 - Global scope
 - Local scope
 - Block scope(let)

#### closure
Javascript allow inner function full access to all the variables and functions defined inside the outer function and all other variables and fucntions that the outer function has access to. This provides sort of encapsulation for the variable of the inner function to emulate privacy and can be used as a function foctory. However it will also negatively effect script performance both in terms of processing speed and memory consumption
#### callback function
It is a function passed into another function as an argument, which is then invoked the function to complete some kind of routine or action
#### arrow function 
it is a shorter syntax than a function expression and does not have its own this and argument. Arrow functions follow the normal variable lookup rules. They end up finding this from its enclosing scope.
#### promise
It is a proxy of a value not known when the promise is created, it can associates multiple handlers with an asynchronous action's success value and failure reason.(reject,resolve,pending)
#### this key word
The value of this, when used in a function, is the object that "owns" the function.The value of this, when used in an object, is the object itself. The this keyword in an object constructor does not have a value. It is only a substitute for the new object.The value of this will become the new object when the constructor is used to create an object.
#### Scope and Context
scope is function-based while context is object-based.scope pertains to the variable access of a function when it is invoked. Context is always the value of the this keywor which is a reference to the object that "owns" the currently executing code.
#### execution context
An execution context can be divided into a creation and execution phase. In the creation phase, the interpreter will first create a variable object (also called an activation object) that is composed of all the variables, function declarations, and arguments defined inside the execution context. From there the scope chain is initialized next, and the value of this is determined last. Then in the execution phase, code is interpreted and executed.


-----
## Object 
In the javascript world, almost everthing could to be an object. Tt is a map that stores Key, value pairs which can be anything, such as a list, another object, a function.

- object <=> Json
    - JSON.stringify() object=>json
    - JSON.parse() json => object
- get keys and values
    - Object.keys(obj)
    - Object.values(obj)
    - Object.entries(obj)
- object.prototype
    - hasOwnproperty: &nbsp; it useful to find out wehter a given property/ket exists in an object
    - instanceof: &nbsp; it evalutates whether a given objet is the type of a particular prototype
    - Object.freeze and Object.seal
        - freeze a frozon object can no longer be changed, however,it only applies to the immediate properties of object itself and will prevent future property addition
        - seal preventing new properties from being added to it and marking all existing properties as non-configurable. Values of present properties can still be changed as long as they are writable.
- object.assign: &nbsp; copies the values of all enumerable own properties from one or more source objects to a target object *Object.assign(target, ...sources)*
- Event delegation
    - if there are multiple elements inside one parent, we want to handle all of the elements inside, don't bind event to every inside elements, instead, bind the single handler in parent and get the child from the event.target. Event delegation help simplify event handling by smart usage of bubbling
- enumerability
    Enumerable properties are those properties whose internal enumerable flag is set to true,Enumerable properties show up in for...in loops
- Immutable object is an object whose state can be modified after it is created.Examples of native JavaScript values that are immutable are numbers and strings.

- Observable
  - observable support for passing messages between publishers and subscribers obserble are lazy and it can delivery multiple data in a row like stream. observable only runs when it is subscribe use to handle http  and event or handling multiple values 

---
## regular expression 
    
#### normal character
- \d &nbsp; matches a digit character. equivalent to [0-9]  &nbsp;\D match a non-digit character
- \w &nbsp; Matches any alphanumeric character including the underscore [A-Za-z0-9_] &nbsp; \W
- ^ &nbsp; Matches beginning of input 
- $ &nbsp; Matches end of input
- \* &nbsp; Matches the preceding expression or more tines {0,}
- \+ &nbsp; Matches the preceding expression 1 or more times. {1,}
- . &nbsp; Matches any signle character except the newline character 
- x(?=y) &nbsp; lookhead, match x only if it is followed by 'y'
- x(?!y) &nbsp; negated lookhead, match x only if it is not followed by 'y'
- (?<=y)x &nbsp; matche x only if x is preceded by y
- () &nbsp; capturing parentheses
- [] &nbsp; character class
- {} &nbsp; quantifier

#### normal question
- match a UserName(at least 6 characters and at max 15 characters)
    - ```/^[\w]{6,15}$/```
- match a password(at leadt 6 characters, at max 15 characters and at least has a captial letter and a special symbol) 
    - ``` ^.*(?=.{6,15})(?=.*\d)(?=.*[A-Z])(?=.*[a-z])(?=.*[!@#$%^&*?\(\)]).*$```
- match an emial
    - ``` /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/```


## Important embeded method
- map: &nbsp; create a new array with the results of calling a provided function on every element in the calling array
- reduce: &nbsp; return a new array, reduce((accumulator,current)=>{},initialValue)
- ilter: &nbsp; method creates a new array with all elements that pass the test implemented by the provided function.
- slice: &nbsp; arr.slice([begin[, end]]) returns a shallow copy of a portion of an array into a new array object selected from begin to end (end not included). 
- push, unshift: &nbsp; method adds one or more elements to the end of an array and returns the new **length** of the array
- concat: &nbsp; This method does not change the existing arrays, but instead returns a new array.
- split: &nbsp; splits a String object into an array of strings by separating the string into substrings, using a specified separator string to determine where to make each split.

## Inheritance

- In javascript, it use prototype chain to implement inheritance between objects,if we want to create a child ingeritance object, Firstly, we need to call the super constructor and then extends the supperclass.(overload=> no, override=> prototype,Es6 just rewrite the method in the child class)

``` javascript
// Create a class
function Vehicle(color){
  this.color = color;
}

// Add an instance method
Vehicle.prototype.go = function(){
  return "Underway in " + this.color;
}

// Add a second class
function Car(color){
  this.color = color;
}

// And declare it is a subclass of the first
Car.prototype = new Vehicle();

// Override the instance method
Car.prototype.go = function(){
  return Vehicle.prototype.go.call(this) + " car"
}

// Create some instances and see the overridden behavior.
var v = new Vehicle("blue");
v.go() // "Underway in blue"

var c = new Car("red");
c.go() // "Underway in red car" 
```