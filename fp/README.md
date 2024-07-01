# FP
Are built mostly with a handful of very small, reusable, predictable pure functions.
So, you might start to see virtually everything as:

- A list (ej: map can be)
- An element of a list (ej: find)
- A predicate used to test list values (ej: filter)
- A transformation based on list values (ej: map, reduce)

Less bugs
- Easier to reason about

Less time
- Re-use more code

Better because we can control the state, control flow and code volume:
- Unified call Syntax
- Minimized state
- Captured assignments
- Forced control flow

## Functions are:
- Values can exploit this by dividing your code into small simple functions
and composing them together using Higher order functions

- Pass into functions(higher order functions)

##  High order functions (like, filter, map, reduce, ...)

Either take functions as parameters, return functions or both. The function returned isa variation of the argument function.

## Composition functions
Allows us to compose a lot of small functions into bigger functions

Ej:

```ts
  function makeAdder(constantValue) {
    return function adder(value) {
      return constantValue + value;
    };
  }
```

```ts
  function makeRegexParser(regex) {
    return regex.exec;
  }

  var parseSsn = makeRegexParser(/^\d{3}-\d{2}-\d{4}$/);
```


## Curry functions
That only takes a single parameter at a time

```ts
  const f = a => b => c => d => a + b + c + d

  console.log(f(1)(2)(3)(4)); // prints 10
```

## Immutability
### First-class functions:

- Treats functions as values. You can assing a function into a variable.

### Higher-order functions:

- Work on other functions.
- They take one or more functions as an argument and can also return a function.

```ts
// step 1
var mult5AfterAdd10 = value => mult5(add10(value));

// step 2
var add = x => y => x + y
var mult5AfterAdd10 = y => mult5(add(10)(y));

// step 3
var compose = (f, g) => x => f(g(x));
var mult5AfterAdd10 = compose(mult5, add(10));
```

Pure Functions are the Simplest Functions
- Given the same input, will always return the same output (Idempotent).
- Produces no side effects.
- Relies on no external "mutable" state
- Referential transparency.

```ts
const foo = f(a);
// result of `f(a)` were `42`
const foo = 42;
```

- Essential for reliable concurrency
- Extremely independent
- Ad-hoc polymorphism:

> Means that inside your function, you look at the inputs, and based on their types or values,you follow different branches of conditional logic.

## Function composition:
Is the process of combining two or more functions in order to produce a new function or perform some computation.

### Functions:
Is a process wich takes some input, called arguments, and produces some output called a return value.

- Communicating functions (I/O)
- Functions which perform I/O.
- Procedural functions (impure function)
- Alist of instructions, grouped together.
- Mapping functions (pure function: the majority of your functions should be)
-Given some input, return some corresponding output.


**Concise code is:**
- Less bug prone
- Easier to debug
- Easier to write
- Easier to read
- Easier to maintain

> "Concise syntax, currying & composition"

> factories are simply functions that create objs and return them

**composition:**

```ts
// factory barker
const barker = (state) => ({
  bark: () => console.log('woof, I am ' + state.name)
})

const driver = (state) => ({
  drive: () => console.log('woof, I am ' + state.name)
})

barker({name: 'gohan'}).bark(); // woof, I am gohan


// factory: function that create obj and return them
const murderRobotDog = (name) => {
  let state = {
    name,
    speed: 100,
    position: 0
  };

  return Object.assign(
    {},
    barker(state),
    driver(state),
    killer(state)
  );
};
```

>video about factory

**class:**
```ts
class Dog {
  constructor() {
    this.sound = 'woof'
  }

  talk() {
    console.log(this.sound);
  }
}

const pepe = new Dog(); // instancia

pepe.talk(); // woof
```

**factory:**
```ts
const dog = () => {
  const sound = 'woof'

  // return obj literal with one property
  return {
    talk: () => console.log(sound)
  }
}

const pepe = dog()
pepe.talk() // woof


murderRobotDog('pepe').bark(); // woof, I am pepe
```


## JS

2 paradigms:

### Prototypal Inheritance:
Obj without classes, and prototype delegation (aka, OLOO - Obj Linking to Other Objects)

### Functional Programming:
- Enabled by lambdas with closure
- ES6 classes are less flexible and less expressive than prototypes, composition.
- Dynamic object extention, and ES6 `class` does not supply any form of “type safety” benefit, either.


# Reactive Programming
- Uses functional utilities like map, filter and reduce to CREATE and PROCESS data flow.
- wich propogate changes throught the system: hence, REACTIVE.
- When input changes, output and updates automatically in response.

## Handling asynchronous operations
By callbacks, promises, rx, async&await.

### Promises:
- promise a certain value in the future.
- Handle a one value

### rx:
- handle streams of data.
- You can wrap and observable around click listener
- return a observable.
