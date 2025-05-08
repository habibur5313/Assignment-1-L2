# What is the use of the keyof keyword in TypeScript? Provide an example.
`keyof` in TypeScript creates a type from the keys of an object type as a union of strings.

### Simple Example
```typescript
interface Person {
  name: string;
  age: number;
}

// `keyof Person` gives "name" | "age"
type PersonKeys = keyof Person;

function getValue(obj: Person, key: PersonKeys) {
  return obj[key];
}

const person: Person = { name: "Bob", age: 25 };

// Works fine
console.log(getValue(person, "name")); // Outputs: "Bob"
console.log(getValue(person, "age"));  // Outputs: 25

// Error if key is invalid
// getValue(person, "email"); // Error: "email" is not "name" | "age"
```

### What it does
- `keyof Person` makes a type with the property names: `"name" | "age"`.
- The function `getValue` only accepts valid keys (`"name"` or `"age"`), ensuring type safety.
- Helps avoid mistakes by checking keys at compile time.
