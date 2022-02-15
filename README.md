<div id="top"></div>

[//]: # ([![LinkedIn][linkedin-shield]][linkedin-url])

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/Hegabovic/JavaScript.git">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>

<h2 align="center">ES6: ECMAScript</h2>

</div>



<!-- TABLE OF CONTENTS -->

<details>
<summary>Table of Contents</summary>
<ol>
    <li>
      <a href="#Hoisting">Hoisting</a>
        <ul>
            <li><a href="#Hoisting-for-variables">Hoisting for Variables</a></li>
            <li><a href="#Hoisting-for-Functions">Hoisting for Functions</a></li>
        </ul>
    <li><a href="#let-and-const:-block-scope">Let and Const: Block Scope</a></li>
   <li><a href="#Literal-string:-backticks">Literal String: backticks</a></li>
   <li><a href="#Default-Values-for-Parameters">Default Values for Parameters</a></li> 
   <li><a href="#Spread-and-Rest-Operators">Spread and Rest Operators</a></li>
    <li><a href="#Arrow-function">Arrow Function</a></li>
   </li>

</ol>
</details>

# Hoisting

## Hoisting for Variables

* var  : variable declaration <br>
* myVar : variable assign <br>

1. trying to access `myVar` before declaration line, its value will be `undefined` until it reach the assigning line
   because of `Hoisting`<br>

2. under `script tag` there is `Hoisting section`, All variables declared using `var` keyword will be put here and
   javascript engine is seeing all these variables.<br>

3. when using `var keyword` you can reassign and overwrite the variable

```javascript
<script>
    console.log(myVar); // myVar = Undefined;
    var myVar=10; // global scope (declaration + assign)
    console.log(myVar); // myVar = 10;
</script>
```

there is `Hoisting section` locally for the functions<br>

```javascript
function myfun() {
    // there is Hoisting section locally for functions 
    console.log(myFnVar);  // myFnVar = undefined 
    var myFnVar = 10;  // local scope varirable
    console.log(myFnVar);  // myFnVar = 10
}
```

## Hoisting for Functions

### Function statement hoisting

- line of declaration begin with `function keyword`<br>
- name of the function is required. <br>
- hoisting section: `var myFnc =function(){console.log("my function statement");}`

```javascript
<script>
    // hoisting section:var myFnc=function(){console.log("from myFnc")}
    myFnc(); // workable
    function myFnc(){     // function header: function keyword + function name + parameters list 
    console.log("my function statement") // function body
}
    myFnc(); // workable
</script>
```

### Function expression hoisting

- function name is optional
- hoisting section: `var myFnc` with value `undefined` NOT a function

```javascript
<script>
    // hoisting section:var myFnc=function(){console.log("from myFnc")}
    myFnc(); // NOT workable because myFnc is not a function
    var myFnc = function(){     // function header: function keyword + function name + parameters list 
    console.log("my function expression") // function body
}
    myFnc(); // workable
</script>
```

# let and const: block scope

- represent `block scope`
- let and const variables are `not hoisted`
- you can't declare the same variable name using let or const or var `within the same scope`.

```javascript
<script>
    console.log(myVar); // undefined
    console.log(myLet); // error 'cant access myLet'
    var myvar = 10;
    let mylet = 10;
</script>
```

example on `let` scope

```javascript
console.log(myLet);  // error (out of scope) 
if (true) {
    console.log(myLet); //error (myLet is not hoisted)
    let myLet = 10;
}
console.log(myLet); // error (out of scope)
```

`const` variables which defined using const `must be assigned` its value `cannot be changed`

```javascript
const myvar; // error in declaration
```

# Literal String: backticks

multi-line strings in ES5:

- you were needed to put `\` as escape<br>

```javascript
// ES5 
var myname = "Abdullah\
            Ahmed\
            mahmoud\    
            hegab";
```

this problem is solved in `ES6` using `backticks`<br>

- backticks represent a string<br>
- can put multi-line string as you want and use `${ }` to put variables names in between<br>

```javascript
let myname = `Abdullah "Ahmed" 'Mahmoud' Hegab`;
let firstName = `Abdullah`;
let lastName = `Hegab`;
let nickName = `Hegabovic`;
let FullName = `my full name is ${firstName + " " + lastName} and my Nickname is ${nickName}`;
```

# Default Values for Parameters

- default values are added from `right to left`<br>

```javascript
function tr(x) {
    return x * 3;
}

function sum(a, b = tr(a), c = b / 2) {
    return a + b + c;
}

console.log(`${sum(1, 2)}`)   // NaN
console.log(`${sum(1, 2)}`)   // will get result after adding default value
```

# Spread and Rest Operators

rest and spread are represented as `...`

- **rest: ...**
    - with function declaration as parameters:
    - Destructing

* any function can't contain more than `one rest operator`<br>
* it `must` appear at `last position` with parameter list<br>
* takes vales and represent an array object with values<br>

```javascript
function getResult(op) {
    // create an array object contains value started from index 1
    let arr = [];
    for (let i = 1; i < arguments.length; i++) {
        arr.push(arguments[i]);
    }
    return eval(arr.join(op));
}
console.log(getResult("+",1,2,4,5,6));
```
Using rest operator
```javascript
function getResult(op,...myArr){
    return eval(arr.join(op));
}

let arr = [1,2,3,4,5,6,7];
console.log(getResult("+",...arr));  // spread array: spread is used in array calling
```
use spread to add array elements inside another array elements 
```javascript
let arr1=[10,20,30,40];
let arr2=[100,200];
//let arr3=[10,20,100,200,30,40];
let arr3 = [10,20,arr2,30,40];     // output [10,20,[100,200],30,40]
let arr3 = [10,20,...arr2,30,40]; //  output [10,20,100,200,30,40]
```

# Arrow Function: 
