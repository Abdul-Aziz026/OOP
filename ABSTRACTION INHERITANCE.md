#### Link: https://www.linkedin.com/pulse/mastering-abstraction-c-comprehensive-guide-practical-irina-grigoras-63u8e/?trk=article-ssr-frontend-pulse_more-articles_related-content-card

## Data Abstraction
Abstraction is a fundamental concept in object-oriented programming (OOP) that involves managing complexity by hiding unnecessary details from the user.
- Data abstraction refers to providing only essential information to the outside world and hiding their background details, only represent the needed information in program without presenting the details.
- C++ provides a great level of abstraction. For example, pow() function is used to calculate the power of a number without knowing the algorithm the function follows.


## Key Principles of Abstraction

- **Simplification:** Abstraction simplifies complex reality by modeling classes appropriate to the problem.
- **Focus on Relevance:** It allows focusing on what an object does instead of how it does it.
- **Reusability:** Abstracting functionality into classes allows for code reusability.
- **Modularity:** It enhances modularity by separating the implementation and the interface.

##### Abstract Class example
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
