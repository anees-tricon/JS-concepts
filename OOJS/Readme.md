# Object Oriented Javascript

`a normal object with properties and methods`

    var person = {
        name: ['Bob', 'Smith'],
        age: 32,
        gender: 'male',
        interests: ['music', 'skiing'],
        bio: function() {
            alert(this.name[0] + ' ' + this.name[1] + ' is ' + this.age + ' years old. He likes ' + this.interests[0] + ' and ' + this.interests[1] + '.');
        },
        greeting: function() {
            alert('Hi! I\'m ' + this.name[0] + '.');
        }
    };
    
`use of this`

    var person1 = {
        name: 'Chris',
        greeting: function() {
            alert('Hi! I\'m ' + this.name + '.');
        }
    }

    var person2 = {
        name: 'Brian',
        greeting: function() {
            alert('Hi! I\'m ' + this.name + '.');
        }
    }
    
`constructor function`

    function Person(first, last, age, gender, interests) {
        this.name = {
            first,
            last
        };
        this.age = age;
        this.gender = gender;
        this.interests = interests;
        this.bio = function() {
            alert(this.name.first + ' ' + this.name.last + ' is ' + this.age + ' years old. He likes ' + this.interests[0] + ' and ' + this.interests[1] + '.');
        };
        this.greeting = function() {
            alert('Hi! I\'m ' + this.name.first + '.');
        };

      };
      
    var person1 = new Person('Bob', 'Smith', 32, 'male', ['music', 'skiing']);
    var person2 = new Person('sam', 'jake', 32, 'male', ['music', 'skiing']);
      
`add methods on the prototype instead of adding them on each instance`

    Person.prototype.greeting = function() {
        alert('Hi! I\'m ' + this.name.first + '.');
    };

    Person.prototype.bio = function() {
        alert(this.name.first + ' ' + this.name.last + ': bio');
    }
    
`create a Teacher constructor which will be child class of the Person`

    function Teacher(first, last, age, gender, interests, subject) {
        Person.call(this, first, last, age, gender, interests);
        this.subject = subject;
    }
    
    Teacher.prototype.greeting = function() {
        var prefix;
        if (this.gender === 'male' || this.gender === 'Male' || this.gender === 'm' || this.gender === 'M') {
          prefix = 'Mr.';
        } else if (this.gender === 'female' || this.gender === 'Female' || this.gender === 'f' || this.gender === 'F') {
          prefix = 'Mrs.';
        } else {
          prefix = 'Mx.';
        }

        alert('Hello. My name is ' + prefix + ' ' + this.name.last + ', and I teach ' + this.subject + '.');
    };
    
`make teacher inherit from the person class`

    Teacher.prototype = new Person();
    Teacher.prototype.constructor = Teacher;
