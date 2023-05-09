---
layout: post
title: "What is class in JavaScript?"
date: 2023-05-09 15:48:00 +0200
---

## 1. What is class in JavaScript?

I have made several projects but never used class. I used types and interfaces and found they are enough for me.
But its always good to know more.

## 2. Simple example explaining class

Class is a template for creating objects. It encapsulates data with code to work on that data. Like following example:
  
```javascript
  class Puppy {
  id: number;
  breed: string;
  name: string;
  birthdate: string;

  constructor(id: number, breed: string, name: string, birthdate: string) {
    this.id = id;
    this.breed = breed;
    this.name = name;
    this.birthdate = birthdate;
  }

  bark() {
    console.log(`${this.name} says woof!`)
  }
}
```

Class puppy not only has its necessary information, but also has a method to bark like a REAL dog. This is how it different from types and interfaces.

## 3. Where to use class

In my previous projects, I used types to store the information for each users, including their name, email address and hashed password. But actually I can use class to do the same thing.

```javascript
class User {
  id: number;
  username: string;
  email: string;
  password: string;

  constructor(id: number, username: string, email: string, password: string) {
    this.id = id;
    this.username = username;
    this.email = email;
    this.password = password;
  }

  // Authenticate user
  authenticate(password: string): boolean {
    return this.password === password;
  }

  // Other user-related methods
}

// Usage
const user = new User(1, 'john_doe', 'john.doe@example.com', 'secure_password');
console.log(user.authenticate('secure_password'));
```
It is better(maybe🫥 I guess) than types because I can authenticate user by calling the method `authenticate` on the user object.

## 4. Other situatiions to use class

### 4.1. Chat app

```javascript
class ChatUser {
  id: number;
  name: string;

  constructor(id: number, name: string) {
    this.id = id;
    this.name = name;
  }
}

class ChatMessage {
  id: number;
  sender: ChatUser;
  content: string;
  timestamp: Date;

  constructor(id: number, sender: ChatUser, content: string, timestamp: Date) {
    this.id = id;
    this.sender = sender;
    this.content = content;
    this.timestamp = timestamp;
  }
}

class ChatRoom {
  id: number;
  name: string;
  messages: ChatMessage[];

  constructor(id: number, name: string) {
    this.id = id;
    this.name = name;
    this.messages = [];
  }

  addMessage(message: ChatMessage): void {
    this.messages.push(message);
  }
}
```

### 4.2. E-commerce app

For customer, product and order, they all have multiple necessary information to carry.

```javascript
class Product {
  id: number;
  name: string;
  price: number;

  constructor(id: number, name: string, price: number) {
    this.id = id;
    this.name = name;
    this.price = price;
  }
}

class Customer {
  id: number;
  name: string;
  email: string;

  constructor(id: number, name: string, email: string) {
    this.id = id;
    this.name = name;
    this.email = email;
  }
}

class Order {
  id: number;
  customer: Customer;
  products: Product[];

  constructor(id: number, customer: Customer, products: Product[]) {
    this.id = id;
    this.customer = customer;
    this.products = products;
  }

  // Calculate total order value
  getTotalValue(): number {
    return this.products.reduce((total, product) => total + product.price, 0);
  }
}
```