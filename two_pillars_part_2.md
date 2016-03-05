
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
   - Idempotence is an important feature for building RESTful web services
   - Valuable for parallel and distributed computation (horizontal scaling)
   - Great for working with continous data sets
2. Free from side-effects:  
   - Do not mutate any shared state or mutable arguments
   - Other than the return value, they don't produce any observable output including thrown exceptions, logs, console, display, I/O devices etc.
   - Less likely to conflict with other programs or cause bugs
   - Stronger guarantees of encapsulation
   - 
