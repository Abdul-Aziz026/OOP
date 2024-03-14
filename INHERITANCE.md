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

### Types of inheritance
#### Single inheritance.
Single inheritance involves a derived class inheriting from only one base class.
```cpp
#include <iostream>

// Base class
class Shape {
public:
    void draw() {
        std::cout << "Drawing a shape." << std::endl;
    }
};

// Derived class inheriting from a single base class
class Circle : public Shape {
public:
    void drawCircle() {
        std::cout << "Drawing a circle." << std::endl;
    }
};

int main() {
    Circle myCircle;
    myCircle.draw();       // Accessing the base class method
    myCircle.drawCircle(); // Accessing the derived class method
    return 0;
}
/*
output:
      Drawing a shape.
      Drawing a circle.
*/
```
#### Multiple Inheritance
Multiple inheritance involves a derived class inheriting from two or more base classes.
```cpp
#include <iostream>

// Base classes
class Shape {
public:
    void draw() {
        std::cout << "Drawing a shape." << std::endl;
    }
};

class Color {
public:
    void fill() {
        std::cout << "Filling with color." << std::endl;
    }
};

// Derived class inheriting from multiple base classes
class ColoredCircle : public Shape, public Color {
public:
    void drawColoredCircle() {
        std::cout << "Drawing a colored circle." << std::endl;
    }
};

int main() {
    ColoredCircle myColoredCircle;
    myColoredCircle.draw();             // Accessing methods from the first base class
    myColoredCircle.fill();             // Accessing methods from the second base class
    myColoredCircle.drawColoredCircle(); // Accessing the derived class method
    return 0;
}
/*output:
      Drawing a shape.
      Filling with color.
      Drawing a colored circle.
*/
```
#### Multilevel Inheritance
Multilevel inheritance involves a chain of inheritance with more than two levels.
```cpp
class A {
    // Implementation
};

class B : public A {
    // Implementation
};

class C : public B {
    // Implementation
};

```
#### 4. Hierarchical Inheritance
Hierarchical inheritance involves multiple derived classes inheriting from a single base class.
```cpp
class Vehicle {
    // Implementation
};

class Car : public Vehicle {
    // Implementation specific to Car
};

class Bike : public Vehicle {
    // Implementation specific to Bike
};

```
#### Hybrid Inheritance
Hybrid inheritance is a combination of two or more types of inheritance within a program. It often involves using multiple, multilevel, or hierarchical inheritance together.   
Example: Combining multiple and multilevel inheritance.
```cpp
#include <iostream>

// Base class
class Shape {
public:
    void draw() {
        std::cout << "Drawing a shape." << std::endl;
    }
};

// Intermediate class inheriting from the base class
class Circle : public Shape {
public:
    void drawCircle() {
        std::cout << "Drawing a circle." << std::endl;
    }
};

// Another base class
class Color {
public:
    void fill() {
        std::cout << "Filling with color." << std::endl;
    }
};

// Derived class inheriting from both intermediate class and another base class
class ColoredCircle : public Circle, public Color {
public:
    void drawColoredCircle() {
        std::cout << "Drawing a colored circle." << std::endl;
    }
};

int main() {
    ColoredCircle myColoredCircle;
    myColoredCircle.draw();             // Accessing methods from the first base class
    myColoredCircle.drawCircle();       // Accessing methods from the intermediate class
    myColoredCircle.fill();             // Accessing methods from the second base class
    myColoredCircle.drawColoredCircle(); // Accessing the derived class method
    return 0;
}

```
#### Virtual Inheritance
Virtual inheritance is used to address the Diamond Problem in multiple inheritance.
![image](https://github.com/Abdul-Aziz026/OOP/assets/57495952/5e0d12e5-9c89-4018-9a03-a6194ff67442)
![image](https://github.com/Abdul-Aziz026/OOP/assets/57495952/b745de22-be95-4053-906b-e50a9dbc1156)

![image](https://github.com/Abdul-Aziz026/OOP/assets/57495952/3b0892f2-0e19-4122-a9ed-6f80a64ed081)

```cpp
#include <iostream>

// Base class with virtual keyword
class Shape {
public:
    virtual void draw() {
        std::cout << "Drawing a shape." << std::endl;
    }
};

// Intermediate classes with virtual keyword
class Circle : virtual public Shape {
public:
    void drawCircle() {
        std::cout << "Drawing a circle." << std::endl;
    }
};

class Color : virtual public Shape {
public:
    void fill() {
        std::cout << "Filling with color." << std::endl;
    }
};

// Derived class inheriting from both intermediate classes
class ColoredCircle : public Circle, public Color {
public:
    void drawColoredCircle() {
        std::cout << "Drawing a colored circle." << std::endl;
    }
};

int main() {
    ColoredCircle myColoredCircle;
    myColoredCircle.draw();             // Accessing the virtual method from the base class
    myColoredCircle.drawCircle();       // Accessing methods from the first intermediate class
    myColoredCircle.fill();             // Accessing methods from the second intermediate class
    myColoredCircle.drawColoredCircle(); // Accessing the derived class method
    return 0;
}

```
### Diamond Problem
The diamond problem occurs in languages with multiple inheritance when a class inherits from two classes that have a common ancestor.
```cpp
class A {
    // Implementation
};

class B : public A {
    // Implementation
};

class C : public A {
    // Implementation
};

class D : public B, public C {
    // Ambiguity arises when accessing A's members from D.
};
```

### Initialization and Cleanup
#### Constructor Initialization

```cpp
class Base {
public:
    Base(int value) : data(value) {
        // Constructor implementation
    }
private:
    int data;
};

class Derived : public Base {
public:
    Derived(int value) : Base(value) {
        // Constructor implementation
    }
};

```
#### Destructor Cleanup
```cpp
class Base {
public:
    ~Base() {
        // Destructor implementation
    }
};

class Derived : public Base {
public:
    ~Derived() {
        // Destructor implementation
    }
};
```

**Link: https://chat.openai.com/c/ba9e6f9b-d655-4f06-88e6-ecd466103988#introduction**
