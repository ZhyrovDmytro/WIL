# Partial and Required

### Partial\<T>

Allows to make all properties of the type `T` optional. It will add a `?` mark next to every field.

`Partial<T>`

```ts
interface User {
  id: number;
  firstName: string;
  lastName: string;
}

function showType(args: Partial<User>) {
  console.log(args)
}

showType({firstName: "John"}) // '{firstName: "John"}' - no type error
```

Interface User created and used with `Partial`, it makes all fields in `User` optional

### Requared\<T>

the `Required` utility makes all properties of the type `T` **required**.

```
interface User {
  id?: number;
  firstName?: string;
  lastName?: string;
}

function showType(args: Requared<User>) {
  console.log(args)
}

showType({firstName: "John"}) // Error: Type - missing id and lasteName
```
