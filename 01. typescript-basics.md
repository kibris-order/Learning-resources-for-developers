Sure, let's go through each session and provide a brief explanation along with code examples.

### Session 1: TypeScript Basics

#### Introduction to TypeScript
TypeScript is a superset of JavaScript that adds static typing to the language. It allows developers to define types for variables, function parameters, and return types, which can catch potential errors during development.

#### Setting up a TypeScript development environment
To set up a TypeScript development environment, you need to install Node.js and then use npm (Node Package Manager) to install TypeScript globally. After that, you can use a `tsconfig.json` file to configure your TypeScript project.

Example `tsconfig.json`:
```json
{
  "compilerOptions": {
    "target": "es5",
    "module": "commonjs",
    "strict": true
  }
}
```

#### TypeScript syntax and basic types
```typescript
// Basic types
let num: number = 5;
let str: string = "Hello";
let isTrue: boolean = true;

// Arrays
let numArray: number[] = [1, 2, 3];
let strArray: string[] = ["apple", "banana", "orange"];

// Tuples
let tuple: [string, number] = ["John", 25];

// Enums
enum Color {
  Red,
  Green,
  Blue
}
let myColor: Color = Color.Green;

// Any type
let dynamic: any = "Hello";
dynamic = 42;

// Void function
function sayHello(): void {
  console.log("Hello!");
}
```

### Session 2: Functions and Interfaces

#### Functions in TypeScript
```typescript
// Function with types
function addNumbers(a: number, b: number): number {
  return a + b;
}

// Optional parameter
function greet(name: string, greeting?: string): void {
  if (greeting) {
    console.log(`${greeting}, ${name}!`);
  } else {
    console.log(`Hello, ${name}!`);
  }
}
```

#### Introduction to interfaces
```typescript
// Interface
interface Person {
  firstName: string;
  lastName: string;
  age: number;
}

// Function with interface
function displayPerson(person: Person): void {
  console.log(`${person.firstName} ${person.lastName}, ${person.age} years old`);
}
```

#### Using interfaces for type checking
```typescript
// Type checking with interface
let user: Person = {
  firstName: "John",
  lastName: "Doe",
  age: 30
};

displayPerson(user);
```

### Session 3: Classes and Inheritance

#### Introduction to classes
```typescript
// Class
class Animal {
  // Constructor
  constructor(public name: string) {}

  // Method
  makeSound(): void {
    console.log("Some generic sound");
  }
}
```

#### Constructor and properties
```typescript
// Class with properties and constructor
class Person {
  // Properties
  firstName: string;
  lastName: string;

  // Constructor
  constructor(firstName: string, lastName: string) {
    this.firstName = firstName;
    this.lastName = lastName;
  }

  // Method
  getFullName(): string {
    return `${this.firstName} ${this.lastName}`;
  }
}
```

#### Inheritance and access modifiers
```typescript
// Inheritance
class Dog extends Animal {
  // Constructor with super
  constructor(name: string, public breed: string) {
    super(name);
  }

  // Overriding method
  makeSound(): void {
    console.log("Woof! Woof!");
  }
}

// Access modifiers
class PrivatePerson {
  private secret: string;

  constructor(secret: string) {
    this.secret = secret;
  }

  getSecret(): string {
    return this.secret;
  }
}
```

These examples provide a basic overview of TypeScript and cover topics like basic types, functions, interfaces, classes, inheritance, and access modifiers. Feel free to adapt and expand upon these examples based on your specific needs.