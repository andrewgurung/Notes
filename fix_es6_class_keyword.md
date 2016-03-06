
Author Info
-----------
Author: Andrew Gurung <br>
URL: http://andrewgurung.github.io/

Context
-------
How to Fix the ES6 `class` keyword <br>
By Eric Elliott

Notes
-----

### Intro
- `class` keyword in ES6 is fundamentally broken in many ways
- In Javascript, you don't need `class` to instantiate an object
- Any function can instantiate and return objects (factory functions) without constructor call which are far more powerful than `class`
- GoF Design Patterns book has whole section on object creation to bypass constructors and classes

### How to Fix `class`
- Make class inheritance compositional
- In other words, deprecate `extends` and replace it with `compose` that multiple classes
- Deprecate `new` keyword since it violates both substitution principle and open/closed principle
  - To replace existing `class` `new` keyword with factory function, you need to refactor all callers
  - Problematic for shared libraries
- Make sure that `class` obeys the substitution principle
- Deprecate `super` keyword
  - `super` tightly couples child classes to parent
  - Changing parent would cause unknowable ripple effect on child classes
  - Debugging is a nightmare if you have to traverse through 6 levels of hierarchy
- Deprecate `instanceof` keyword since it doesn't do what the name describes
- Replace constructor with factory function

  ```js
  // Class
  class ClassPolygon {
    constructor(height, width) {
      this.height = height;
      this.width = width;
    }
  }

  // Factory function
  function FuncPolygon(height, width) {
    var self = {
      height: height,
      width: width
    };
    return self;
  }

  // Constructor call
  var c1 = new ClassPolygon( 10, 20 ); // {height: 10, width: 20}

  // Factory function
  var c2 = FuncPolygon( 10, 20 ); // {height: 10, width: 20}
  ```
