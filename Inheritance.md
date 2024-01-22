# Inheritance

### Table of Contents
1. Introduction
2. Inheritance Basics
   - Derived Classes
   - Base Classes
   - Access Specifiers
3. Access Types of Inheritance
   - Public Inheritance
   - Protected Inheritance
   - Private Inheritance
4. Virtual Functions and Polymorphism
   - Virtual Functions
   - Pure Virtual Functions
   - Polymorphism
5. Types of inheritance
   - Single inheritance.
   - Multi-level inheritance.
   - Multiple inheritance.
   - Hierarchical Inheritance.
   - Hybrid Inheritance.
   - Virtual Inheritance
6. Diamond Problem
7. Initialization and Cleanup
8. Best Practices
9. Conclusion

### Introduction:
Inheritance is a key concept in object-oriented programming (OOP) that allows a class to inherit properties and behaviors from another class. It promotes code reusability and establishes a relationship between classes.

### Inheritance Basics
#### Derived Classes
A derived class is a class that inherits properties and behaviors from another class, called the base class or parent class.
Example:
```cpp
// Base class
class Animal {
public:
    void eat() {
        // Implementation
    }
};

// Derived class
class Dog : public Animal {
public:
    void bark() {
        // Implementation
    }
};
```
#### Base Classes
A base class is a class whose properties and behaviors are inherited by another class.
```cpp
// Base class
class Shape {
public:
    virtual void draw() {
        // Implementation
    }
};

```
### Access Specifiers && Types of Inheritance
      - Public Access Specifier / Inheritance.
      - Protected Access Specifier / Inheritance.
      - Private Access Specifier / Inheritance.
      
```cpp
// PUBLIC
class Derived : public Base {
    // Public and protected members of Base are accessible here.
    // public public become public, protected member become Protected
};
//PROTECTED
class Derived : protected Base {
    // Public and protected members of Base are now protected in Derived.
};
//PRIVATE
class Derived : private Base {
    // Public and protected members of Base are now private in Derived.
};

```
### Virtual Functions and Polymorphism
#### Virtual Functions
Virtual functions allow a function in the base class to be overridden by a function in the derived class.
```cpp
class Shape {
public:
    virtual void draw() {
        // Implementation
    }
};

class Circle : public Shape {
public:
    void draw() override {
        // Implementation specific to Circle
    }
};

```
#### Pure Virtual Functions
Pure virtual functions have no implementation in the base class and must be overridden in derived classes.
```cpp
class Shape {
public:
    virtual void draw() = 0; // Pure virtual function
};

class Circle : public Shape {
public:
    void draw() override {
        // Implementation specific to Circle
    }
};

```
#### Polymorphism
Polymorphism allows a base class pointer to refer to objects of derived classes and access their specific methods.

```cpp
// Example:
Shape* shapePtr = new Circle();
shapePtr->draw(); // Calls draw() of the Circle class.
```

### Multiple Inheritance




**Link: https://chat.openai.com/c/ba9e6f9b-d655-4f06-88e6-ecd466103988#introduction**
