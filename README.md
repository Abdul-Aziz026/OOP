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

#### <ins>Importent Note:</ins> class state in variable and behaviour is function.


### what is constructor and distructor?
<ins>**constructor**</ins>
- in C++ is a special method that is automatically called when an object of a class is created.   
- **constructor** is special type of function that is used to initialized the object.
- it's name is the same in which class it's belongs to.

   
<ins>**destructor**</ins>
- works opposite to constructor; 
- it destructs the objects of classes.
- Destructor is an instance member function that is called automatically whenever an object is going to be destroyed.
```cpp
#include <iostream>
using namespace std;

class MyClass {
    int x, y;
public:
    // Default constructor
    MyClass(){
        cout << "Default Constructor Called...\n";
    }

    // Parameterized constructor
    MyClass(int x, int y){
        cout << "Parameterized Constructor Called...\n";
    }

    // Destructor declaration
    ~MyClass(){
        cout << "Distroy object...\n";
    }
};

int main() {
    // Creating objects and invoking constructors
    MyClass *obj1 = new MyClass;         // Invokes default constructor
    delete obj1;                         // distructor called by own

    MyClass obj;                         // Invokes default constructor
    MyClass obj2(10, 20);                // Invokes parameterized constructor
    
    // Destructor is automatically called when objects go out of scope
    return 0;
}

/* output:
            Default Constructor Called...
            Distroy object...
            Default Constructor Called...
            Parameterized Constructor Called...
            Distroy object...
            Distroy object...
*/
```
