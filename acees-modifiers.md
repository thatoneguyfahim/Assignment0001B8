## Blog 2
# Title: Explain how Access Modifiers (public, private, protected, and readonly) work in TypeScript OOP with examples.

# Introduction
In typescript, access modifiers control where class members can be accessed. Therec are public, private, and protected to manage visibility. There's also readonly modifier. It serves a different purpose, preventing a property from being reassigned after initialization.

# Analysis
Public: Public members can be accessed from anywhere. In TypeScript, class members are public by default. In the Employee example below,
getDetails() is public. So any code outside the class can call
manager.getDetails().

Private: Private members can only be accessed inside the class where they are declared. The Employee class uses private baseSalary: number. Its has its own getDetails() method that can read the salary, but the Manager subclass cannot access baseSalary directly.

Protected: Protected members are accessible inside their declaring class and its subclasses, but not from outside. In our example Employee class declares protected name: string. Therefore, Manager.getRoleInfo() can use this.name, but the external code cannot access manager.name.

```typescript
class Employee {
  protected name: string;
  private baseSalary: number;

  constructor(name: string, baseSalary: number) {
    this.name = name;
    this.baseSalary = baseSalary;
  }

  public getDetails(): string {
    return `Employee: ${this.name}, Base Salary: ${this.baseSalary}`;
  }
}

class Manager extends Employee {
  private department: string;

  constructor(name: string, baseSalary: number, department: string) {
    super(name, baseSalary);
    this.department = department;
  }
}
```
Readonly: Readonly prevents reassignment by others accidentally. In the coordinate problem example below, readonly [number, number,string] prevents the function from changing the tuple's elements. 

```typescript
function formatCoordinate(
  coordinate: readonly [number, number, string]
): string {
  const [latitude, longitude, locationName] = coordinate;
  return `Location: ${locationName} (${latitude}, ${longitude})`;
}
```

# Conclusion
Each has its own use cases. We can use public for accessible members, private for class-only details, and protected when subclasses need access. We use readonly when a value
should be read but not reassigned. These modifiers make TypeScript
classes safer and easier to maintain.