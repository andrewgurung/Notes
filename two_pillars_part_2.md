
Author Info
-----------
Author: Andrew Gurung <br>
URL: http://andrewgurung.github.io/

Context
-------
The Two Pillars of JavaScript: Functional Programming <br>
By Eric Elliott

Notes
-----

## The two pillars of JavaScript:

1. **Prototypal Inheritance** (objects without classes, prototype delegation, OLOO -- Objects Linking to Other Objects)
2. **Functional Programming** (enabled by lambdas with closure)

## Functional Programming
- Functional Programming is a natural fit for JavaScript, since JS offers:
  - First-class functions
  - Closures
  - Simple lamda syntax

### Essence of Functional Programming
- small
- reusable
- predictable `pure functions`

### Pure Functions
Pure functions have a few properties that make that extremely reusable and useful for a variety of applications:

1. Idempotence:  
   - Given the same inputs, a `pure function` will always return the same result, regardless of the number of times the function is called
   - Important feature for building RESTful web services
   - Parallel and distributed computation (horizontal scaling)
   - Works great with continous data sets
2. Free from side-effects:  
   - Do not mutate any shared state or mutable arguments
   - Stronger guarantees of encapsulation
   - Function purity is FP’s answer to the gorilla/banana problem from OOP

Note: Complex programs that need to produce output cannot be composed using `only` pure functions. But where ever possible **USE** `pure functions`

### Working in Functional Programming (FP)
- Functional Programming provides several kinds of functions that are extremely usuable
- Haskell is a more popular FP, but you will find functions similar to it in several JavaScript libraries
- Some utilities from Haskell documentation:
  - head(), last(), equal(), map(), filter(), reduce(), loop() etc

Some of these common utilities got added to JavaScript:

```js
// (..) =>  is equivalent to function(..) {..}
var input = [1, 2, 3, 4, 5];
var mapOutput = input.map( (n) => n + 1 );
console.log( mapOutput );  // [2, 3, 4, 5, 6]

var filterOutput = input.filter( (n) => n >= 3 && n <= 5 );
console.log(filterOutput); // [3, 4, 5]

var reducedOutput = input.reduce( (n, el) => n + el );
console.log( reducedOutput ); // 15
```
