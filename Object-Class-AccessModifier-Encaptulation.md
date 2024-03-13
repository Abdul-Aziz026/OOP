# OOP
## .............................@(Class, Object, Constructor, Distructor, Access Modifier)....................................
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
/*
output:
        Values: 10
        Values: 20
*/
```

#### <ins>Importent Note:</ins> class state in variable and behaviour is function.


### what is constructor and distructor?
<ins>**constructor**</ins>
- in C++ constructor is a special method that is automatically called when an object of a class is created.   
- **constructor** is special type of function that is used to initialized the object.
- it's name is the same in which class it's belongs to.
- no return type like(void, int etc.)

   
<ins>**destructor**</ins>
- works opposite to constructor; 
- it destructs the objects of classes.
- Destructor is an instance member function that is called automatically whenever an object is going to be destroyed.

### Constructors Access specifiers
Constructors can be defined as public, protected, or private as per the requirements. By default or default constructors, which are created by the compiler are declared as the public. If the constructor is created as private, then we are not able to create its object.
When there is no requirement of the object of a class (in a situation when all class members are static) we can define its constructor as private.
Usually, constructors are defined as public because constructors are used to create an object and initialize the class data members for the object. An object is always created from outside of class, which justifies making constructors public.

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

## Static Variable and function:
### 1. Static Variable...
```cpp
#include <iostream>
#include <string>
using namespace std;

class MyClass {
public:
    // Member variables (data members)
    static string versity ;
    string name, id;
    int age;
    MyClass(string name, string id, int age) {
        this->name = name;
        this->id = id;
        this->age = age;
    }
    // Member functions
    void display();
};

string MyClass::versity = "BSMRSTU";

// Member function definition (implementation)
void MyClass::display() {
    cout << "Versity Name: " << versity << endl;
    cout << "Name: " << name << endl;
    cout << "Id: " << id << endl;
    cout << "Age: " << age << endl;
}

class MyClass1 {
public:
    // Member variables (data members)
    static string versity ;
    string name, id;
    int age;
    MyClass1(string name, string id, int age) {
        this->name = name;
        this->id = id;
        this->age = age;
    }
    // Member functions
    void display();
};

string MyClass1::versity = "DU";

// Member function definition (implementation)
void MyClass1::display() {
    cout << "Versity Name: " << versity << endl;
    cout << "Name: " << name << endl;
    cout << "Id: " << id << endl;
    cout << "Age: " << age << endl;
}

int main() {
    // Object creation
    MyClass obj1("Abdul_Aziz", "18CSE026", 25);
    MyClass obj2("Khatun", "18CSE021", 24);

    // Accessing member variables and calling member functions
    // obj1.myInt = 10;
    obj1.display();
    obj2.display();

    cout << endl;
    MyClass1 obj3("Abdul_Aziz", "18CSE026", 25);
    obj3.display();
    return 0;
}
/*
        Versity Name: BSMRSTU
        Name: Abdul_Aziz
        Id: 18CSE026
        Age: 25
        Versity Name: BSMRSTU
        Name: Khatun
        Id: 18CSE021
        Age: 24

        Versity Name: DU
        Name: Abdul_Aziz
        Id: 18CSE026
        Age: 25
*/
```

## 2. Static function...
```cpp
#include <iostream>
#include <string>
using namespace std;

static int x;

class MyClass {
public:
    // Member variables (data members)
    static string versity ;
    string name, id;
    int age;
    MyClass(string name, string id, int age) {
        x = 20;
        this->name = name;
        this->id = id;
        this->age = age;
    }
    static int sum(int a, int b) {
        return a + b ;
    }
    // Member functions
    void display();
};

string MyClass::versity = "BSMRSTU";

// Member function definition (implementation)
void MyClass::display() {
    cout << "Versity Name: " << versity << endl;
    cout << "Name: " << name << endl;
    cout << "Id: " << id << endl;
    cout << "Age: " << age << endl;
}

int main() {
    // Object creation
    MyClass obj1("Abdul_Aziz", "18CSE026", 25);

    // Accessing member variables and calling member functions
    obj1.display();
    // static method can be accessed without object instance...
    cout << "sum of 100 and 200 is : " << MyClass::sum(100, 200) << endl;
    cout << "sum of 100 and 200 is : " << obj1.sum(100, 200) << endl;

    return 0;
}
/*
        Versity Name: BSMRSTU
        Name: Abdul_Aziz
        Id: 18CSE026
        Age: 25
        sum of 100 and 200 is : 300
*/
```

### Access Modifier
In C++, access modifiers are keywords that specify the visibility and accessibility of class members (variables and functions) from outside the class.   
There are three main access modifiers in C++: **public, private, and protected.**

<ins>Public:</ins>
- Members declared as public are accessible from outside the class.
- They can be accessed by objects of the class and external functions.

<ins>Private:</ins>
- Members declared as private are not accessible from outside the class.
- They can only be accessed within the same class.

<ins>Protected:</ins>
- Similar to private, members declared as protected are not accessible from outside the class.
- However, they can be accessed by derived classes (inheritance).
```cpp
class BaseClass {
// accessmode...public/private/protected
public:
    int protectedVar;
    void protectedFunction();
};
```


## .................................................................(Encaptulation)......................................................................

### What is Encapsulation?
Encapsulation is a key concept in C++ that involves bundling data (variables) and functions (methods) into a single unit called a class. It promotes data security and code organization by hiding the internal details of a class and exposing only what's necessary.

#### Benefits of Encapsulation:

Data Hiding: Keeps internal details private.   
Modularity: Organizes code into self-contained units.   
Flexibility: Allows changing internal implementation without affecting external code.
#### How it Works:
<ins>Private and Public Members:</ins>
- private: Accessible only within the class.
- public: Accessible from outside the class.

<ins>Accessors and Mutators:</ins>
- Accessors (Getters): Provide read-only access to private members.
- Mutators (Setters): Allow controlled modification of private members.

Example:
```cpp
class BankAccount {
private:
    // Private members
    double balance;

public:
    // Public members

    // Constructor
    BankAccount(double initialBalance) : balance(initialBalance) {}

    // Accessor (Getter)
    double getBalance() const {
        return balance;
    }

    // Mutator (Setter)
    void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    // Mutator (Setter)
    void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
        }
    }
};
```

**<ins>Note:</ins>Encapsulation is a fundamental principle that enhances code security, organization, and flexibility in C++. It's about bundling related data and methods together for better software design.**

## .................@(INSHAALLAH YOU CAN DONE.ALLAH IS ALWAYS WITH YOU)...................
## ......................................................................@(END)....................................................................
