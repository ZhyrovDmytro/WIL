# Jest Mocks

### The Mock Function <a href="1d32" id="1d32"></a>

The Mock Function provides features to:

* Capture calls
* Set return values
* Change the implementation

```
test("returns undefined by default", () => {
  const mock = jest.fn();

  let result = mock("foo");

  expect(mock).toHaveBeenCalled();
  expect(mock).toHaveBeenCalledWith("foo");
});
```

we can change the return value, implementation, or promise resolution:

```
test("mock implementation", () => {
  const mock = jest.fn(() => "bar");

  expect(mock("foo")).toBe("bar");
  expect(mock).toHaveBeenCalledWith("foo");
});

test("also mock implementation", () => {
  const mock = jest.fn().mockImplementation(() => "bar");

  expect(mock("foo")).toBe("bar");
  expect(mock).toHaveBeenCalledWith("foo");
});

test("mock return value", () => {
  const mock = jest.fn();
  mock.mockReturnValue("bar");

  expect(mock("foo")).toBe("bar");
  expect(mock).toHaveBeenCalledWith("foo");
});

test("mock promise resolution", () => {
  const mock = jest.fn();
  mock.mockResolvedValue("bar");

  expect(mock("foo")).resolves.toBe("bar");
  expect(mock).toHaveBeenCalledWith("foo");
});
```

### Mocking Modules and Functions <a href="3972" id="3972"></a>

* `jest.fn`: Mock a function
* `jest.mock`: Mock a module
* `jest.spyOn`: Spy or mock a function

### Mock a function with jest.fn <a href="2c44" id="2c44"></a>

```
import * as app from "./app";
import * as math from "./math";

math.add = jest.fn();
math.subtract = jest.fn();

test("calls math.add", () => {
  app.doAdd(1, 2);
  expect(math.add).toHaveBeenCalledWith(1, 2);
});

test("calls math.subtract", () => {
  app.doSubtract(1, 2);
  expect(math.subtract).toHaveBeenCalledWith(1, 2);
});
```

### Mock a module with jest.mock <a href="af80" id="af80"></a>

```
import * as app from "./app";
import * as math from "./math";

// Set all module functions to jest.fn
jest.mock("./math.js");

test("calls math.add", () => {
  app.doAdd(1, 2);
  expect(math.add).toHaveBeenCalledWith(1, 2);
});

test("calls math.subtract", () => {
  app.doSubtract(1, 2);
  expect(math.subtract).toHaveBeenCalledWith(1, 2);
});
```

### Spy or mock a function with jest.spyOn <a href="a6fc" id="a6fc"></a>

```
import * as app from "./app";
import * as math from "./math";

test("calls math.add", () => {
  const addMock = jest.spyOn(math, "add");

  // calls the original implementation
  expect(app.doAdd(1, 2)).toEqual(3);

  // and the spy stores the calls to add
  expect(addMock).toHaveBeenCalledWith(1, 2);c
});
```

mock a function, but then restore the original implementation:

```
import * as app from "./app";
import * as math from "./math";

test("calls math.add", () => {
  const addMock = jest.spyOn(math, "add");

  // override the implementation
  addMock.mockImplementation(() => "mock");
  expect(app.doAdd(1, 2)).toEqual("mock");

  // restore the original implementation
  addMock.mockRestore();
  expect(app.doAdd(1, 2)).toEqual(3);
});
```

storing the original implementation, setting the mock implementation to original, and re-assigning the original later:

```
import * as app from "./app";
import * as math from "./math";

test("calls math.add", () => {
  // store the original implementation
  const originalAdd = math.add;

  // mock add with the original implementation
  math.add = jest.fn(originalAdd);

  // spy the calls to add
  expect(app.doAdd(1, 2)).toEqual(3);
  expect(math.add).toHaveBeenCalledWith(1, 2);

  // override the implementation
  math.add.mockImplementation(() => "mock");
  expect(app.doAdd(1, 2)).toEqual("mock");
  expect(math.add).toHaveBeenCalledWith(1, 2);

  // restore the original implementation
  math.add = originalAdd;
  expect(app.doAdd(1, 2)).toEqual(3);
});
```
