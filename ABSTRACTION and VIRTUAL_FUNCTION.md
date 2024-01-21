#### Link: https://www.linkedin.com/pulse/mastering-abstraction-c-comprehensive-guide-practical-irina-grigoras-63u8e/?trk=article-ssr-frontend-pulse_more-articles_related-content-card

## Data Abstraction
Abstraction is a fundamental concept in object-oriented programming (OOP) that involves managing complexity by hiding unnecessary details from the user.
- Data abstraction refers to providing only essential information to the outside world and hiding their background details, only represent the needed information in program without presenting the details.
- C++ provides a great level of abstraction. For example, pow() function is used to calculate the power of a number without knowing the algorithm the function follows.


## Key Principles of Abstraction

- **<ins>Simplification:</ins>** Abstraction simplifies complex reality by modeling classes appropriate to the problem.
- **<ins>Focus on Relevance:</ins>** It allows focusing on what an object does instead of how it does it.
- **<ins>Reusability:</ins>** Abstracting functionality into classes allows for code reusability.
- **<ins>Modularity:</ins>** It enhances modularity by separating the implementation and the interface.

#### Abstract Class Example
```cpp
/*Bismillahir Rahmanir Rahim....*/
#include <iostream>
using namespace std;

// abstract Base class
class Base {
public:
    virtual void display() = 0;
    void show() {
        cout << "This is Base Show Class" << endl;
    }
};

class Derived : public Base {
public:
    void display() override {
        // display();
        cout << "Derived class display function" << endl;
    }
};

signed main() {
    Derived d;
    d.display();
    d.show();
    Base *b = &d;
    b->display();
    b->show();
    return 0;
}
/*output:
          Derived class display function
          This is Base Show Class
          Derived class display function
          This is Base Show Class
*/
```

### Abstract class vs Abstract Class...
**Instantiation:**
- **<ins>Abstract Classes:</ins>** You cannot create an object (instance) directly from an abstract class. Abstract classes are like blueprints that need to be extended by other classes.
- **<ins>Interfaces:</ins>** Similarly, you cannot create an object directly from an interface. Interfaces are designed to be implemented by other classes, providing a way to enforce a specific set of behaviors.

**Data Members:**
- **<ins>Abstract Classes:</ins>** Abstract classes can contain both abstract methods (methods without implementation) and data members (variables with values).
- **<ins>Interfaces:</ins>** Interfaces are usually more focused on declaring a set of abstract methods. They typically do not include data members. The emphasis is on specifying what methods a class must have rather than what data it must store.
### Abstract Class Example...
```cpp
  #include <iostream>

// Interface (using abstract class)
class Printable {
public:
    // Pure virtual function (abstract method)
    virtual void print() const = 0;

    // Optionally, you can have other virtual functions (not pure virtual) or constants.
    virtual void info() const {
        std::cout << "This is a printable object." << std::endl;
    }

    // Virtual destructor (important for base classes)
    virtual ~Printable() {}
};

// Concrete class implementing the interface
class Message : public Printable {
public:
    // Implementing the abstract method from Printable
    void print() const override {
        std::cout << "This is a printable message." << std::endl;
    }
};

int main() {
    // You cannot instantiate an interface directly.
    // Printable printable;  // Error!

    // However, you can create objects of classes implementing the interface.
    Message message;
    message.print();
    message.info();  // Accessing the non-pure virtual function from the interface.

    return 0;
}
```
### Interface Class Example: 
- **<ins>Interfaces:</ins>** Interfaces are usually more focused on declaring a set of abstract methods. They typically do not include data members.
```cpp
#include <iostream>
using namespace std;

// Interface class
class Shape {
public:
    // Pure virtual functions (no implementation)
    virtual void draw() const = 0;
    virtual double area() const = 0;

    // Virtual destructor (important for base classes)
    virtual ~Shape() {}
};

// Concrete class implementing the Shape interface
class Circle : public Shape {
private:
    double radius;

public:
    Circle(double r) : radius(r) {}

    // Implementing the pure virtual functions from Shape
    void draw() const override {
        cout << "Drawing a circle." << endl;
    }

    double area() const override {
        return 3.14 * radius * radius;
    }
};

int main() {
    // You cannot instantiate an object of the interface directly.
    // Shape shape;  // Error!

    // However, you can create objects of classes implementing the interface.
    Circle circle(5.0);
    circle.draw();
    cout << "Area of the circle: " << circle.area() << endl;

    return 0;
}
```


### Virtual and Pure Virtual Function:
**Virtual Function:**
- Declaration: virtual void functionName().
- Implementation:	May have a default implementation.
- Object Instantiation:	Can instantiate objects of the class.
- Derived Class Override	Optional (can choose to override).

**Pure Virtual Function:**
- Declaration: virtual void functionName() = 0;
- Implementation:	No implementation in the base class
- Object Instantiation: Cannot instantiate objects of the class
- Derived Class Override Mandatory (must override in derived class)

**Virtual and Pure Virtual Example**
```cpp
#include <iostream>
using namespace std;

// Virtual Function
class BaseVirtual {
public:
    // Virtual function with a default implementation
    virtual void display() {
        std::cout << "BaseVirtual class display function" << std::endl;
    }
};

// Derived class for Virtual Function
class DerivedVirtual : public BaseVirtual {
public:
    // Override the virtual function
    void display() override {
        cout << "DerivedVirtual class display function" << endl;
    }
};

// Pure Virtual Function
class BasePureVirtual {
public:
    // Pure virtual function with no implementation
    virtual void show() = 0;
};


// Derived class for Pure Virtual Function Example
class DerivedPureVirtual : public BasePureVirtual {
public:
    // Must provide an implementation for the pure virtual function
    void show() override {
        cout << "DerivedPureVirtual class show function" << endl;
    }
};

int main() {
    // Virtual Function
    BaseVirtual baseVirtual;
    baseVirtual.display();  // Calls the default implementation

    DerivedVirtual derivedVirtual;
    derivedVirtual.display();  // Calls the overridden implementation

    // Cannot instantiate objects of the abstract class
    // BasePureVirtual basePureVirtual;  // Error!

    DerivedPureVirtual derivedPureVirtual;
    derivedPureVirtual.show();  // Calls the overridden implementation

    return 0;
}

```

