**Arrays**
- Special type of object
- Accessed using []
    - If looking for non-existent index, you get undefined
    - Can iterate though array regularly
    - New way to do it with ES2015
        ```javascript
        for (const currentValue of a) {
        // Do something with currentValue
        }
        ```
- Have a property of length
    - Not neccecarily the number of items in the array
    - But is the value one higher the the highest index
- Created by: `var a = new Array();`
    - Can use array literals too
- Appending items to array
    `a.push(item);`
- See full list of methods on website

**Functions**
- Example
    ```javascript
    function add(x, y) {
        var total = x + y;
        return total;
    }
    ```
- cam take >= 0 para,s
  - if you call a function without passing necc args it returns undefined
  - if you pass too many args it ignores the extra ones at the end
- similar to functions in other languages
- have access to the array-like object holding the values passed into the function
  - called `arguments`
  - rest parameter operator - used in the function parameter like belog
        ```javascript
        function avg(...args) {
        var sum = 0;
        for (let value of args) {
            sum += value;
        }
        return sum / args.length;
        }

        avg(2, 3, 4, 5); // 3.5
        ```
- can call a function with an arbitrary array of arguments using `apply()`
    ```javascript
    avg.apply(null, [2, 3, 4, 5]); // 3.5
    ```
- can also make annymous functions - function definition where you would put an expression
    ```javascript
    var avg = function() {
    var sum = 0;
    for (var i = 0, j = arguments.length; i < j; i++) {
        sum += arguments[i];
    }
    return sum / arguments.length;
    };
    ```
- cam use recursion w/ funcs
  - can provide names to functions without a name only availible to the function's scope

**Custom Objects**
- JS uses functions as classes
- can attach functions to objects
    ```javascript
    function Person(first, last) {
        this.first = first;
        this.last = last;
        this.fullName = function() {
            return this.first + ' ' + this.last;
        };
        this.fullNameReversed = function() {
            return this.last + ', ' + this.first;
        };
    }
    var s = new Person('Simon', 'Willison');
    ```
- `this` meaning
  - refers to the current object
  - if called with dot/braket notation on an object, it refers to that object
  - if no dot/bracket notation used, it refers to the global object
- `new` meaning
  - creates a brand new object
  - when function is called, `this` is set tp that object
  - funcs designed to be called by new are constructors
    - can assign references inside the constructor
        ```javascript
        function Person(first, last) {
        this.first = first;
        this.last = last;
        }
        Person.prototype.fullName = function() {
        return this.first + ' ' + this.last;
        };
        Person.prototype.fullNameReversed = function() {
        return this.last + ', ' + this.first;
        }; 
        ```  
    - Person.prototype is an obj shared by all instances of Person
      - if Person properties arent set, JS will che the prototype to see if it exists there
      - also, you can modify the prototype at any time in your program (even at runtime)
      - can also add mehod to prototypes of built in JS objs    
  - capitalize these funcs to remember to call them with new
  - can use `apply()` and have first argument as the obejct to be treated as `this`
    ```javascript
    function trivialNew(constructor, ...args) {
    var o = {}; // Create an object
    constructor.apply(o, args);
    return o;
    }
    ```
    - calling the function
    ```javascript
    var bill = trivialNew(Person, 'William', 'Orange');
    // is equivaent too
    var bill = new Person('William', 'Orange');
    ```

**Innner Fuctions**
- decalring functions inside functins are allowed
- shares variables with parents - act like local-global variables

**Closures** // Come back to it, is confusing
- powerful but confusing abscrations
- creates new adder functions, qhen called with one arg adds to the arg that it was created with
- closures are the combination of a function and the scope object in which it was created