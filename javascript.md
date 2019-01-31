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
- 

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
-






