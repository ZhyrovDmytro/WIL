# Generics

Use generics for a helper filter function

```
const filterArrayByValue = (items: User[], propertyName: string, valueToFilter: string): User[] => {
  return items.filter(item => item[propertyName] === valueToFilter);
};
```

To make this function reusable and applied for different items we can use generics.

```
const filterArrayByValue = <T>(
  items: T[],
  propertyName: string,
  valueToFilter: string
): T[] => {
  return items.filter(item =>item[propertyName] === valueToFilter);
};
```

\<T> is a generic type;

To make it better, we want the **propertyName** to be the **name of a property contained in the type of **_**T**_, plus we want the value to filter to be a **partial** value of the entity __ T. We can introduce **another generic type which extends T**_**,**_** called P** to tell TypeScript we want to use a property of __ T __ as the second parameter

```
const filterArrayByValue = <T, P extends keyof T>(
  items: T[],
  propertyName: P,
  valueToFilter: T[P] //Partial<T> 
): T[] => {
  return items.filter(item =>item[propertyName] === valueToFilter);
};
```

