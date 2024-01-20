# OOP

### what is class?
class is a template from which individual object can be created.

### what is object?
Object is a class type variable.

### class and class object declaration.
```cpp
#include <iostream>

class MyClass {
public:
    // Member variables (data members)
    int myInt;
    
    // Member functions
    void display();
};

// Member function definition (implementation)
void MyClass::display() {
    std::cout << "Values: " << myInt << std::endl;
}

int main() {
    // Object creation
    MyClass obj1;

    // Accessing member variables and calling member functions
    obj1.myInt = 10;
    obj1.display();

    // Another object
    MyClass obj2;
    obj2.myInt = 20;
    obj2.display();

    return 0;
}
```

#### class state in variable and behaviour is function.
