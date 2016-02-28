
Author Info
-----------
Author: Andrew Gurung <br>
URL: http://andrewgurung.github.io/

Context
-------
The Two Pillars of JavaScript: Prototypal Inheritance <br>
By Eric Elliott

Notes
-----

## The two pillars of JavaScript:

1. **Prototypal Inheritance** (objects without classes, prototype delegation, OLOO -- Objects Linking to Other Objects)
2. **Functional Programming** (enabled by lambdas with closure)

### Creating a mess
- Constructors violate `open/closed principle` because they couple all callers to the details of how your object gets instantiated
- If a caller forgets `new` and you are not using strict mode or ES6 classes, anything assigned to `this` will pollute global space
- In JS, `factory functions` are `constructors` minus `new` keyword, global pollution danger and initial capitalized letter convention
- JS doesn't need constructor function since any function can return a new object

> The problem with object-oriented languages is they’ve got all this implicit environment that they carry around with them. You wanted a banana but what you got was a gorilla holding the banana and the entire jungle.   
~ Joe Armstrong

### What is a Prototype?
- A working sample

### Three kinds of Prototype
1. Delegate Prototype
  - Shared methods
  - Delegate to look up the not found property in another object

  #### Old N Busted
  - A bit akward with `new` keyword and constructor functions since technically you don't need `new` to create objects in JavaScript

  ```js
  function Greeter(name) {
    this.name = name || "John Doe";
  }

  Greeter.prototype.hello = function() {
    return "Hello, " + this.name;
  };

  var foo = new Greeter( "Foo" );
  ```

  #### New N Hot
  - Create a prototype and pass it to `Object.create(..)` to create a new object
  - Then set any property on the newly created object since JavaScript supports dynamic object extension

  ```js
  var proto = {
    hello: function() {
        return "Hello, " + this.name;
    }
  };

  var foo = Object.create( proto );
  foo.name = "Foo";
  ```

2. Cloning/Concatenation Prototype
  - Create a new object out of copied properties
  - Used for Mixins
  - `$.extend(target, source1, source2, ..)` method to copy properties from different objects

  #### Mixin Style

  ```js
  var proto = {
    hello: function() {
        return "Hello, " + this.name;
    }
  };

  var foo = $.extend( {}, proto, {name: "Foo"} );
  ```

3. Function Prototypes
  - Not really a type of prototype but really useful when used in conjuction to prototypal Inheritance to create functional objects
  - Great for data encapsulation
  - Can replace constructor, super() and init functions

  #### Simple model implementation

  ```js
  var model = function() {

    // private data
    var attrs = {};

    this.set = function(name, value) {
      attrs[name] = value;
    };

    this.get = function(name) {
      return attrs[name];
    };

    return this;

  };

  var foo = {};
  model.call( foo ).set( "name", "Foo" );
  foo.get( "name" ); // Foo
  ```

## Factory functions
- Like constructors, but don't need to use `new` or `this`
- Mix and match all three types of Prototypes
- Use `call()` or `apply()` to swap out source prototype at instantiation

### stamp{it} Library
- Stamps allow you to inherit easily from multiple ancestors by composing multiple source stamps
- URL: https://github.com/stampit-org/stampit
- Stampit uses three different kinds of prototypal OO
- Specify which prototypes to use:
  - `.methods()` for delegation
  - `.state()` for cloning/concatenation
  - `.enclose()` for functional data/privacy

> Favor object composition over class inheritance. Program to an interface, not an implementation. ~ Gang of Four

### Good code is simple

- As you strip out constructors and classical inheritance from JavaScript, it gets simpler, more flexible and more powerful.
- Classes deal with the idea of objects
- Prototypes deal with the objects themselves
- Google con
