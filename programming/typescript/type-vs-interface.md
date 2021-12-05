# Type vs Interface

**Interfaces** are basically a way to describe data shapes, for example, an object.

**Type** is a definition of a type of data, for example, a union, primitive, intersection, tuple, or any other type.

### Differences

#### Type

Setup a type alias for just a single core type

```
type Age = number;
```

Possible to create a bit more custom type aliases by using **unions**.

```
type UserType = 'developer' | 'admin' | 'tester';
type User = {
    userType: UserType,
    id: numbder
};
```

#### Interface

Declaration merging not available  with a `type`

```
interface User {
    name: string;
    id: nimber;
}

interface User {
    role: string
}

const newUser: User = {
    name: "John",
    id: 1,
    role: "admin"
}
```

We can create few interfaces with same name and they will be merged;

It is possible **extends** or **implements** the interface.

```
class Car {
  printCar = () => {
    console.log("this is my car")
  }
};

interface NewCar extends Car {
  name: string;
};

class NewestCar implements NewCar {
  name: "Car";
  constructor(engine:string) {
    this.name = name
  }
  printCar = () => {
    console.log("this is my car")
  }
};
```
