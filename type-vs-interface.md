# Title : What are the core differences between type aliases and interface in TypeScript? When should you choose one over the other?

# Introduction 
Type Alias and Interface are both ways we can define the structure and shape of data in typescript.
Their naming is different but they often work similarly. But they have different capabilities and used in exact cases where each is required than the other. We are going to discuss core differences between these two in this blog.

# Analysis
We use interface to design object shapes. Interfaces
can be extended with extends key word too. If there are declarations with the same name they are automatically merged.

A type alias can be used to describe object shapes too. It can also represent unions, primitives, tuples, and combinations of types. 
For example:

```typescript
interface User {
  name: string;
}

interface User {
  age: number;
}
// User is merged because same name interface
const user: User = { name: "Mina", age: 24 };

// type alias example
type User = {
    name: string;
    age: number;
};
// we can use union in type alias
type Status = "pending" | "success" | "failed";

type Point = [number, number];

// interface uses extends key word
interface Employee extends User {
  salary: number;
}
```
We can choose interface when we are defining an object or class contract and especially when we want declaration merging or extending
the shape. Type can be used when we need unions, tuples, primitive
aliases, mapped types, or more complex type composition. For ordinary
object definitions, both are valid.

# Conclusion
So to summarize, neither option is better than the other. We can use interfaces for extendable
object contracts and type aliases for flexible type expressions. Whichever suits our need in the project better.


