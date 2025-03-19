Sure, let's go through each of these topics with code examples in TypeScript.

### 1. Functions and Interfaces

#### Functions in TypeScript

```typescript
// Function with explicit type annotations
function addNumbers(a: number, b: number): number {
  return a + b;
}

// Function with inferred return type
function greet(name: string) {
  return `Hello, ${name}!`;
}
```

#### Introduction to Interfaces

```typescript
// Define an interface for a simple point
interface Point {
  x: number;
  y: number;
}

// Function that takes a Point as a parameter
function printPoint(point: Point) {
  console.log(`(${point.x}, ${point.y})`);
}
```

#### Using Interfaces for Type Checking

```typescript
// Function that returns a Point object
function createPoint(x: number, y: number): Point {
  return { x, y };
}

const myPoint = createPoint(3, 7);
printPoint(myPoint); // Type-checked by the interface
```

### 2. Encapsulation and Abstraction

#### Encapsulation in TypeScript

```typescript
// Encapsulation using classes and private members
class BankAccount {
  private balance: number = 0;

  deposit(amount: number): void {
    this.balance += amount;
  }

  getBalance(): number {
    return this.balance;
  }
}

const account = new BankAccount();
account.deposit(100);
console.log(account.getBalance()); // Accessed through a public method
```

#### Abstract Classes and Methods

```typescript
// Abstract class with an abstract method
abstract class Shape {
  abstract calculateArea(): number;
}

// Concrete class extending the abstract class
class Circle extends Shape {
  constructor(private radius: number) {
    super();
  }

  calculateArea(): number {
    return Math.PI * this.radius ** 2;
  }
}

const myCircle = new Circle(5);
console.log(myCircle.calculateArea());
```

#### Designing Classes with Encapsulation and Abstraction

```typescript
// Improved version using encapsulation and abstraction
class BankAccount {
  private balance: number = 0;

  constructor(initialBalance: number) {
    this.balance = initialBalance;
  }

  deposit(amount: number): void {
    this.balance += amount;
  }

  withdraw(amount: number): void {
    if (amount <= this.balance) {
      this.balance -= amount;
    } else {
      console.log("Insufficient funds.");
    }
  }

  getBalance(): number {
    return this.balance;
  }
}
```

### 3. Polymorphism

#### Understanding Polymorphism

Polymorphism allows objects of different types to be treated as objects of a common type.

#### Method Overloading and Overriding

```typescript
// Method overloading
class Calculator {
  add(a: number, b: number): number;
  add(a: string, b: string): string;
  
  add(a: any, b: any): any {
    if (typeof a === 'number' && typeof b === 'number') {
      return a + b;
    } else if (typeof a === 'string' && typeof b === 'string') {
      return a + b;
    } else {
      throw new Error('Invalid arguments');
    }
  }
}

const calculator = new Calculator();
console.log(calculator.add(5, 3));        // Output: 8
console.log(calculator.add('Hello', ' World'));  // Output: Hello World
```

#### Implementing Polymorphic Behavior in TypeScript

```typescript
// Polymorphism through interfaces
interface Shape {
  calculateArea(): number;
}

class Circle implements Shape {
  constructor(private radius: number) {}

  calculateArea(): number {
    return Math.PI * this.radius ** 2;
  }
}

class Square implements Shape {
  constructor(private sideLength: number) {}

  calculateArea(): number {
    return this.sideLength ** 2;
  }
}

const shapes: Shape[] = [new Circle(5), new Square(4)];
shapes.forEach(shape => console.log(shape.calculateArea()));
```

### 4. Interfaces and Contracts

#### Interfaces in OOP

Interfaces define contracts that classes must adhere to.

```typescript
interface Animal {
  makeSound(): void;
}

class Dog implements Animal {
  makeSound(): void {
    console.log("Woof!");
  }
}

class Cat implements Animal {
  makeSound(): void {
    console.log("Meow!");
  }
}

const dog = new Dog();
const cat = new Cat();

dog.makeSound(); // Output: Woof!
cat.makeSound(); // Output: Meow!
```

#### Implementing Interfaces in TypeScript

```typescript
// Implementing an interface
interface Printable {
  print(): void;
}

class Document implements Printable {
  print(): void {
    console.log("Document is printed.");
  }
}

const document = new Document();
document.print(); // Output: Document is printed.
```

### 5. Angular Services and Dependency Injection

#### Creating and Using Angular Services

Angular services are used to organize and share code across components.

```typescript
// Example Angular service
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root',
})
export class DataService {
  private data: string[] = [];

  addData(value: string): void {
    this.data.push(value);
  }

  getData(): string[] {
    return this.data;
  }
}
```

#### Understanding Dependency Injection in Angular

```typescript
// Using the service in a component
import { Component } from '@angular/core';
import { DataService } from './data.service';

@Component({
  selector: 'app-root',
  template: `
    <div *ngFor="let item of dataService.getData()">
      {{ item }}
    </div>
  `,
})
export class AppComponent {
  constructor(private dataService: DataService) {}

  // Using data service to add data
  addDataToService(value: string): void {
    this.dataService.addData(value);
  }
}
```

#### Designing Services with OOP Principles

```typescript
// Designing a more advanced Angular service with OOP principles
@Injectable({
  providedIn: 'root',
})
export class AdvancedDataService {
  private data: string[] = [];

  constructor(private logger: LoggerService) {}

  addData(value: string): void {
    this.data.push(value);
    this.logger.log(`Data added: ${value}`);
  }

  getData(): string[] {
    this.logger.log('Data retrieved.');
    return this.data;
  }
}

@Injectable({
  providedIn: 'root',
})
export class LoggerService {
  log(message: string): void {
    console.log(`[Logger] ${message}`);
  }
}
```

These examples cover a broad range of TypeScript and OOP concepts. Keep in mind that Angular service examples are simplified and might not work as standalone code without an Angular application setup.