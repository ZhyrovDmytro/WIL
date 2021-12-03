# Record

`Record<K,T>`

Constructs a type with a set of properties `K` of a given type `T`.

```
interface EmployeeType {
  id: number
  fullname: string
  role: string
}

let employees: Record<number, EmployeeType> = {
  0: { id: 1, fullname: "John Doe", role: "Designer" },
  1: { id: 2, fullname: "Ibrahima Fall", role: "Developer" },
  2: { id: 3, fullname: "Sara Duckson", role: "Developer" },
}

// 0: { id: 1, fullname: "John Doe", role: "Designer" },
// 1: { id: 2, fullname: "Ibrahima Fall", role: "Developer" },
// 2: { id: 3, fullname: "Sara Duckson", role: "Developer" }
```

It expects a `number` as a type which is why we have 0, 1, and 2 as keys for the `employees` variable. And if you try to use a string as a property, an error will be thrown.
