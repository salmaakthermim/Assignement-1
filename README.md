# TypeScript Interview Questions - Answers

### 1. What are some differences between interfaces and types in TypeScript?

**Interfaces** and **Types** are similar in TypeScript but have some key differences:

- **Declaration Merging**: 
  - Interfaces allow declaration merging, meaning you can declare the same interface multiple times, and TypeScript will merge them together. This is not possible with types.
  
    ```typescript
    interface Person {
      name: string;
    }
    
    interface Person {
      age: number;
    }
    
    const user: Person = { name: "John", age: 30 };
    ```

- **Extending**: 
  - Both can extend other types or interfaces, but interfaces are better suited for this purpose.
  
    ```typescript
    interface Employee extends Person {
      position: string;
    }
    ```

- **Use Cases**:
  - **Interfaces** are primarily used for **object shapes** and **class implementations**.
  - **Types** are more flexible and can represent **primitives, unions, intersections**, and **tuples**.

---

### 2. What is the use of the `keyof` keyword in TypeScript? Provide an example.

The `keyof` keyword in TypeScript is used to obtain the **union type** of all keys in an object type. It creates a type that represents the keys of the object, making it useful for dynamic property access or restrictions.

#### Example:

```typescript
interface Person {
  name: string;
  age: number;
}

type PersonKeys = keyof Person;  

function getProperty(person: Person, key: PersonKeys) {
  return person[key];
}

const user: Person = { name: "John", age: 30 };
console.log(getProperty(user, "name"));  // Output: John
