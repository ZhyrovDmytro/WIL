# Conditional Types

Conditional types test two types and select one of them depending on the outcome of that test.

```
type NonNullable<T> = T extends null | undefined ? never : T
```

Checks if the type is null or not and handle it depending on that, it uses the JavaScript ternary operator.
