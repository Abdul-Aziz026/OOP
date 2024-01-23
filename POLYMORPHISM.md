## POLYMORPHISM

### Table of Contents

1. Introduction
2. Types of Polymorphism
    1. Compile-time Polymorphism (Static Binding)
       - Function Overloading
       - Operator Overloading
    2. Runtime Polymorphism (Dynamic Binding)
       - Function Overriding
3. Benefits Of Polymorphism 
6. Conclusion

### Introduction:
**polymorphism** comes from Greek, where "poly" means many and "morph" means form.
polymorphism refers to the ability of a function or object to perform in different ways, depending on how the function or object is used.
In simple words, we can define polymorphism as the ability of a message to be displayed in more than one form. A real-life example of polymorphism is a person who at the same time can have different characteristics. A man at the same time is a father, a husband, and an employee.

### Types of Polymorphism
#### 1. Compile-time Polymorphism (Static Binding)
Compile-time polymorphism is achieved through function and operator overloading. The compiler determines the appropriate function or operator at compile-time based on the provided arguments.
#### 1.1 Function Overloading:
When there are multiple functions with the same name but different parameters, then the functions are said to be overloaded, this is known as Function Overloading.
```cpp
class MathOperations {
public:
    int add(int a, int b);
    double add(double a, double b);
};
```
#### 1.2 Operator Overloading:
define how operators work with custom data types.   
has the ability to provide the operators with a special meaning for a data type.
```cpp
#include <iostream>
using namespace std;

class Vector {
private:
    double x, y;
public:
    // Constructor
    Vector(double x_val = 0.0, double y_val = 0.0) : x(x_val), y(y_val) {}
    // Overloading the + operator for vector addition
    Vector operator+(const Vector& other) const {
        return Vector(x + other.x, y + other.y);
    }
    // Overloading the << operator for convenient output
    void display() {
        cout << x << ", " << y ;
    }
};

int main() {
    // Creating vectors
    Vector v1(2.0, 3.0);
    Vector v2(1.5, 2.5);

    // Using the overloaded + operator for vector addition
    Vector sum = v1 + v2;
    cout << "Sum of "; v1.display();
    cout << " and " ; v2.display();
    cout << " = "; sum.display();
    cout << endl ;
    return 0;
}
```
#### 2. Runtime Polymorphism (Dynamic Binding)
This type of polymorphism is achieved by Function Overriding.   
Late binding and dynamic polymorphism are other names for runtime polymorphism.   
2.1 Function Overriding
```cpp
// C++ Program to demonstrate
// the Virtual Function
#include <iostream>
using namespace std;

// Declaring a Base class
class Base {

public:
    // virtual function
    virtual void display()
    {
        cout << "Called virtual Base Class function"
            << "\n";
    }
    void print()
    {
        cout << "Called GFG_Base print function"
            << "\n\n";
    }
};

// Declaring a Child Class
class Child : public Base {
public:
    void display()
    {
        cout << "Called GFG_Child Display Function"
            << "\n\n";
    }
    void print()
    {
        cout << "Called GFG_Child print Function"
            << "\n\n";
    }
};

// Driver code
int main()
{
    // Create a reference of class GFG_Base
    Base* base;
    Child child;
    base = &child;
    // This will call the virtual function
    base->Base::display();
    base->display();
    base->print();
    return 0;
}

/* output:
        Called virtual Base Class function
        Called GFG_Child Display Function
        Called GFG_Base print function
*/
```
### Advantages
- Code Reusability
- Flexibility and Adaptability
- Dynamic Binding



