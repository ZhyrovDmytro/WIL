# Pick and Omit

### Pick\<T,  K>

Creates a new type from an existing model&#x20;

`T` - type you want to pick from&#x20;

`K` - prop you want to select of that type

```
interface PickType {
  id: number
  firstName: string
  lastName: string
}

function showType(args: Pick<PickType, "firstName" | "lastName">) {
  console.log(args)
}

showType({ firstName: "John", lastName: "Doe" })
// Output: {firstName: "John"}

showType({ id: 3 }) // Error: 'id' does not exist in type 'Pick<PickType, "firstName" | "lastName">'
```

### Omit`<T, K>` <a href="#omit" id="omit"></a>

&#x20;It will remove `K` properties from the type `T`.

```
interface PickType {
  id: number
  firstName: string
  lastName: string
}

function showType(args: Omit<PickType, "firstName" | "lastName">) {
  console.log(args)
}

showType({ id: 7 })
// Output: {id: 7}

showType({ firstName: "John" })
// Error: 'firstName' does not exist in type 'Pick<PickType, "id">'
```
