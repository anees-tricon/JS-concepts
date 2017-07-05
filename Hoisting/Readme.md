# Hoisting in Javascript

The variables and function declarations are hoisted in javascript. The variable initializations and assignments are not hoisted. Function assignments are not hoisted

    function showName () {
        console.log ("First Name: " + name); //undefined
        ​var name = "Ford";
        console.log ("Last Name: " + name); //Ford
    }
    
    showName ();
    
In the above example, the variable declaration is hoised but not the initialization and hence the value undefined is printed in first line. After hoisting the function would look something like below

    function showName () {
        var name;
        console.log ("First Name: " + name); //undefined
        name = "Ford";
        console.log ("Last Name: " + name); //Ford
    }

#### Hoisting precedence: function declaration > variable declaration

`function declaration is hoisted above variable declaration`

    var myName;
    function myName () {
        console.log ("Rich");
    }
    console.log(typeof myName); // function
    
`variable assignment overrides function declaration`

    var myName = "Richard";
    function myName () {
        console.log ("Rich");
    }
    console.log(typeof myName); // string
