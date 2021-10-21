---
description: Pipe, Compose
---

# Function composition

### Compose

Chaining multiple functions together to create a new function, split big problems into smaller solutions.

```
codeconst multiply20 = (price) => price * 20;
const divide100 = (price) => price / 100;
const normalizePrice = (price) => price.toFixed(2);
```

Put functions as an argument to another function

```
// result = a(b(c(x)))
const discount = normalizePrice(divide100(multiply20(200))); // 40.00
```

**The result of the inner function is taken by the outer function as an argument** until the end of the chain. Simplified with a compose function:

```
const compose = (a, b, c) => (x) => a(b(c(x)));
```

usage:

```
const discount = compose(normalizePrice, divide100, multiply20);
discount(200.0); //40.00
```

Using more than 3 functions with HOC:

```
const compose =
  (...fns) =>
  (x) =>
    fns.reduceRight((res, fn) => fn(res), x);
```

the X value is passed to reduce func as an acc and as a initial value, **we execute every function passed as argument from rigth to left with the result of aprevious one. **

### **Pipe**

Works same as a _compose_ function but **execute functions from left to right.**

```
const pipe =
  (...fns) =>
  (x) =>
    fns.reduce((res, fn) => fn(res), x);
```

example: _the first executed function will be normilixePrice, then divide and then multiply_

```
const discountPipe = pipe(multiply20, divide100, normalizePrice);
```

sources:&#x20;

* [Function compositions with compose and pipe](https://itnext.io/write-better-javascript-function-composition-with-pipe-and-compose-93cc39ab16ee)
