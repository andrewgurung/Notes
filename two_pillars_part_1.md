
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
