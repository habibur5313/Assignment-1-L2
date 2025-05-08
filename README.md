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

console.log(getValue(person, "name")); // Outputs: "Bob"
console.log(getValue(person, "age"));  // Outputs: 25
```

### What it does
- `keyof Person` makes a type with the property names: `"name" | "age"`.
- The function `getValue` only accepts valid keys (`"name"` or `"age"`), ensuring type safety.
- Helps avoid mistakes by checking keys at compile time.


# Provide an example of using union and intersection types in TypeScript.
### Union Type
A union type lets a value be one of several types.

```typescript
type ID = string | number;

// Function using union type
function printID(id: ID) {
  console.log("ID is: " + id);
}

printID("ABC123"); // Outputs: ID is: ABC123
printID(456);      // Outputs: ID is: 456
```

### Intersection Type
An intersection type combines multiple types into one, requiring all properties.

```typescript
interface Name {
  name: string;
}

interface Age {
  age: number;
}

type Person = Name & Age;

function showPerson(person: Person) {
  console.log(`Name: ${person.name}, Age: ${person.age}`);
}

const person: Person = { name: "Alice", age: 25 };
showPerson(person); // Outputs: Name: Alice, Age: 25
```

### Explanation
- **Union (`string | number`)**: `ID` can be a string or number, so `printID` accepts either.
- **Intersection (`Name & Age`)**: `Person` must have both `name` and `age`, so `person` needs both properties.
