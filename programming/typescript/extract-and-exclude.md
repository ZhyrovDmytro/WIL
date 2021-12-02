# Extract and Exclude

### Extract\<T, U> <a href="#extract" id="extract"></a>

Constructs a type by picking properties that are present in two different types. The utility will extract from `T` all properties that are assignable to `U`.

```
interface FirstType {
  id: number
  firstName: string
  lastName: string
}

interface SecondType {
  id: number
  address: string
  city: string
}

type ExtractType = Extract<keyof FirstType, keyof SecondType>
// Output: "id"
```

Two types have in common the property `id,` **Extract** utility will extract all similar properties.

### Exclude <a href="#exclude" id="exclude"></a>

Constructs a type by excluding properties that are already present in two different types

&#x20;It excludes from `T` all fields that are assignable to `U`.

```
interface FirstType {
  id: number
  firstName: string
  lastName: string
}

interface SecondType {
  id: number
  address: string
  city: string
}

type ExcludeType = Exclude<keyof FirstType, keyof SecondType>

// Output; "firstName" | "lastName"
```

The properties `firstName` and `lastName` are assignable to the `SecondType` type since they are not present there. And by using the `Extract` keyword, we get back these fields as expected.
