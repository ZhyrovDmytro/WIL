# Software development best practices

### YAGNI

[You Aint Gonna Need It](https://martinfowler.com/bliki/Yagni.html). Don't write code that you think you might need in future, but don't need yet.

> The same is true for commenting-out code; if a block of commented code is going into a release, it shouldn't exist.

### Test the code you write, not other people’s code

### Don't repeat yourself

The _**third**_ time you write the same piece of code is the time to extract it.

### API design

_**Simple things should be simple; complex things should be possible**_. Design for the simple case first, with preferably zero configuration or parameterization, if that's possible. Add _options_ or additional API methods for more complex and flexible use cases (as they are needed).

### Fail Fast

### Unit tests test to the unit of behavior, not the unit of implementation.&#x20;

Changing the implementation, without changing the behavior or having to change any of your tests is the goal, although not always possible. So where possible, treat your test objects as black boxes, testing through the public API without calling private methods or tinkering with state.

A good reference for getting started with the "test first" approach is [_Test Driven Development by Example_](https://www.amazon.com/Test-Driven-Development-Kent-Beck/dp/0321146530/ref=as\_li\_ss\_tl?s=books\&ie=UTF8\&qid=1493658724\&sr=1-1\&keywords=kent+beck+test+driven+development+by+example\&linkCode=sl1\&tag=voidspace-20\&linkId=2a938b01e7e04c54081b268e0e2d8000)

### _A_ll code paths should be tested

**Code without tests is a liability**. Measuring coverage and rejecting PRs that reduce coverage percentage is one way to ensure you make gradual progress in the right direction.

### Good naming practices and known programming style

Strive to make your code readable and self-documenting.

Code that can't be made **obvious**—working around an obscure bug or **unlikely** **condition**, or a necessary **optimization**—_**does**_** need commenting.**

### Always think about what can go wrong

What will happen on invalid input, and what might fail, which will help you catch many bugs before they happen.

### Logic is easy to unit test if it is stateless and side-effect free

Side effects _do_ need testing, but testing them once and mocking them out everywhere else is generally a good pattern.

### Globals are bad

Functions are better than types. Objects are likely to be better than complex data structures.

### Dependency injection

This does make API signatures more complex, so it is a trade-off. Ending up with a method that needs 10 parameters for all its dependencies is good sign your code is doing too much, anyway. The definitive article on dependency injection is "[Inversion of Control Containers and the Dependency Injection Pattern](https://www.martinfowler.com/articles/injection.html),"

### The more you have to mock out to test your code, the worse your code is

The goal is small testable units, along with higher-level integration and functional tests to test that the units cooperate correctly.

### Refactor whenever you see the need and have the chance

### Make code correct first and fast second

Writing obscure code because it is faster is only worth it if you’ve profiled and proven that it’s actually worth it.

### Smaller, more tightly scoped unit tests

They give more valuable information when they fail—they tell you specifically what is wrong. A test that stands up half the system to test behavior takes more investigation to determine what is wrong. **Generally a test that takes more than 0.1 seconds to run isn’t a unit test**

### Shared code ownership is the goal

At a minimum, this means discussing or documenting design decisions and important implementation decisions. Code review is the worst time to start discussing design decisions as the inertia to make sweeping changes after code has been written is hard to overcome.

### Always see your test fail at least once

Put a deliberate bug in and make sure it fails, or run the test before the behavior under test is complete. Otherwise you don’t know that you’re really testing anything. Accidentally writing tests that actually don’t test anything or that can never fail is easy.

### Constant feature grind is a terrible way to develop software

Not letting developers take pride in their work ensures you won’t get the best out of them. Not addressing technical debt slows down development and results in a worse, more buggy product.

