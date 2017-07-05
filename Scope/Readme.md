# Scope in Javascript

In javascript, the variable scope is not same as in other languages. For example, there is no block level scope in javascript.
For example, a variable declared inside an if block is accessible outside the if block

#### Simple global and local scope

`1. a variable defined inside an function has a local scope and is accessible only within this function`.

    var a = 10;
    function test() {
        if(true) {
            var a = 20;
        }
        console.log(a); //20 local variable 
     }
     test();
     console.log(a); //10 global variable
     

`2. when we remove the var keyword inside the function, the global variable a is changed`

    var a = 10;
    function test() {
        if(true) {
            a = 20;
        }
        console.log(a); //20 global variable modified
    }
    test();
    console.log(a); //20  global variable modified
    
`3. when we define the local variable inside an if condition which is never executed, the variable declaration is hoisted up and hence the value is undefined`

    var a = 10;
    function test() {
        if(false) {
            var a = 20;
        }
        console.log(a); //undefined
    }
    test();
    console.log(a); //10
    
`4. Now when we remove the var keyword inside this if condition, the global variable is accessed inside the function and hence value is 10`

    var a = 10;
    function test() {
        if(false) {
            a = 20;
        }
        console.log(a); //10
    }
    test();
    console.log(a); //10
    
    
#### the scope of this inside Timeout

`No matter the context, the this always points to the window context when used inside a Timeout`

    var highValue = 200;
    var constantVal = 2;
    var myObj = {
        highValue: 20,
        constantVal: 5,
        calculateIt: function () {
            console.log(this.constantVal * this.highValue);
        },
        calculateItTimer: function () {
            setTimeout (function  () {
              console.log(this.constantVal * this.highValue);
            }, 2000);
        }
    }
    
    myObj.calculateIt(); // 100
    myObj.calculateItTimer(); //400 and not 100
    
  