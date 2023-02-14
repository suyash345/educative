## Challenge 1 display text on console
> print "I am John"
```C++
std::cout<<"I am John"<<std::endl;
```
## Challenge 2 display right angled triangle
> print <br />
> & & & & & & <br />
> & & & & &<br />
> & & & & <br />
> & & & <br />
> & &<br />
> &

``` C++
for(int i =6; i>0;i--)
{
    for(int j =i; j>0;j--)
    { 
    std::cout<<"&";
    if(j!=1){
        std::cout<<" ";
    }
    }
    std::cout<<"\n";
}

```

## Challenge 3 Convert double into int
```C++
int int_value ;
int_value = double_value ;
```

Recursion exponent
```C++


int power(int base, int exponent)
{
    if(exponent==0||base==0)
    {
        return 0;
    }

    if(exponent==1)
    {   
        return base; // returing base to the case before-> think like a stack
    }
    return base*power(base, exponent-1);

}
```
## Challenge 5
``` C++
int factorial (int number)
{
    if(number==1)
    {
        return 1;
    } 
    return number*factorial(number-1);
}
```
## Challenge 6
```C++
int fibonacci(int n) {

  if (n == 0) {
    return 0;
  } else if (n == 1) {
    return 1; (int i =0;i<size-1;i++){
    int ans=arr[i];
    arr[i]=arr[i+1];
    arr[i+1]=ans;
  }
}
```
## References
```C++
  int i =10 
  int& iRef = i; 

```
* no need to dereference when compared to a pointer
* if iRef is changed so is i, if you change the value of reference it also changes the thing of the address.

References as parameters
```C++
void change(int &x, int &y)
{
  y= 20;
  x =40;
}

int main()
{
  a = 12;
  b = 14;

  change(a,b); // after this a is now 40 and b is 20, as when a reference is passed in as the parameter it changes the value of the address, hence to change it as a value it is easier to just pass the reference in.
}
```
* A pointer is an address->therefore, if we use pointers to change the value of a and b.
```C++
  void change(int* x, int* y) // an int pointer is expected, rememeber pointer is an address
  {
    *y = 20; // dereference
    *x = 41;
  }

  int main
  {
    int a = 12;
    int b = 14;
    change(&a,&b) // address of a and b gets passed
  }
```

## Dynamic Allocation
* the __new__ alloctor, reserves space for getting the memeory in run-time. syntax -> new int -> reserves 4 bytes
* To store where this memeory is we need a pointer for this address.
``` C++
int main()
{
  int *ptr; // declare pointer
  ptr = new int; //allocate the space
  *ptr = 100; // derefernce the pointer and change the value that is held in that address.

  delete ptr; // this clears what was stored inside the pointer memory, however, we can still use the ptr to store a different address.
  int a = 40; 
  ptr = &a; // now ptr points to a
  return 0;
}
```
* dynamic arrays can shrink or grow during program execution
* to increase the size of an array you need to copy all its elements and resize.
``` C++
 int main()
 {
  int size = 5;
  int *array = new int[size] // Initialize an array
  for(int i = 0;i<size;i++)
  {
    *(array+i)=i; // works i think
  }
  int * resize = new int[size+2];
  for(int i = 0; i<size; i++)
  {
    *(resize + i) = *(array+i);
  }
  delete array;
  array = resize; // array will now point to the resized.
  *(resize+size)=21;
  *(resize+size+1) = 312;
  // gives new array with new values;
 }
```
## Coding exercise setting all the odd numbers in an array to -1
``` C++
void set_odd(int *arr , int size) {
    for(int i = 0; i<size; i++)
    {
      if(*(arr+i)%2!=0)
      {
        *(arr+i)=-1;
      }
    }

  }
```
## Coding exercise SD and mean in a dynamic array
```C++
#include <iostream>
#include <cmath>
using namespace std;

int main() {
  int size = 10;

  //Declare dynamic array
  int *Array = new int[size];

  //Initialize dynamic array
  for(int i = 0 ; i < size; i++){
    Array[i] = rand() % 100; 
  }   

  //Prints dynamic array
  cout << "Elements of array: ";
  for(int i = 0 ; i < size; i++){
    cout << Array[i] << " ";
  } 
  cout << endl;

  //Calculate mean and print
  float sum = 0;
  for(int i = 0 ; i < size; i++){
    sum += Array[i];
  } 
  float mean = sum/size ;
  cout << "Mean: " << mean << endl;

  //Calculate standard deviation and print
  float stdDev = 0;
  for(int i = 0 ; i < size; i++){
    stdDev += pow(Array[i] - mean, 2);
  }
  stdDev = sqrt(stdDev / size);
  cout << "Standard Deviation: " << stdDev << endl;
  // Deletes a memory allocated to dynamic array
  delete[] Array;
}
```
## Structures

* with functions the structure can be simpily be passed into the paramter

```C++
#include <iostream>
#include <string>


struct Student{
    std::string name;
    int roll_number;
    int marks;
  };

  Student print_student(Student s)
  {
    s.roll_number = 12;
    return s; 
  }

  int main()
  {
    Student s;
    s.roll_number = 20;
    s.marks =10;
    s.name = "hello";
    s = print_student(s); // this actually changes it
    std::cout<<s.roll_number<<" "<< s.marks<<std::endl;
  }
```
* Structures with pointers
``` C++
struct Student {
  std::string name;
  int roll_number;
  int marks;
};

int main()
{
  Student s1;
  Student *s1ptr; // student type pointer;
  s1ptr = &s1;

  *(s1ptr).name = "John";
  *(s1ptr).marks = 12; 
  //  OR 
  s1ptr->name = "John";
  s1ptr->marks = 12;
}
```
## OOP
* Member  Initializer Lists-> the constructor is given the intial varaibles
``` C++
class Sphere {
  private: 
    const double density;
    double radius;
  public:
    Sphere(double r) : radius(r), density(4.3) {
      // The following initialization wouldn't work, because density is a const
      // density =  4.3;
    }
    double volume() {
      return 4 * PI * radius * radius * radius / 3;
    }
    double mass() {
      return density * volume();
    }
};
```
* Contructor delegation-> the base constructor is given a base with the member initializer list of 0, therefore the other contructor with one parameter is called.
``` C++   
 Collector() : Collector(0) {}
    Collector(int cap) : capacity(cap), size(0)  {
      if (cap > 0) {
        list = new int[cap];
      }
      else
        capacity = 0;
    }
```
* Destrcutors with pointers; 
```C++
int main()
{
  Collector * c;
  c = new Collector(); // the thing inside the bracket is the constructor value;
  delete c;
}
```
## Request and Supress methods C++ (look more into)
* Friend Functions are independent functions which have access to the variables and methods of its befriended class
```C++
class Ball
{
  double radius;
  std::string colour;

  friend void setRadius(Ball &b, double r);
};
// The implementation of our friend function
void setRadius(Ball &b, double r){
  b.radius = r;
}

int main()
{
  Ball b(30, "green");
  b.setRadius(b,60); // calls the friend fucntion using the private variaible 
}


```
* Unions-> are a special data type where only one datatype in its class can be accessed at a time.
* Encapsulation->using get and set functions in clasess;
* Abstraction-> only getting the relevant parts from classes. We can put irrlevant details into a .h file
```C++ 
  // main.cpp
  #include <iostream>
  #include <Circle.h>
  int main() 
  {
    Circle(5);
  }
```
``` C++
  // Circle.h
#ifndef CIRCLE_H
#define CIRCLE_H
class Circle
{
  private: 
      double radius;
  double pi;

  public:
      Circle ();
  Circle(double r);  
  double area();  
  double perimeter();
};
```

``` C++ 
  //Circle.cpp
  #include "Circle.h"
  Circle::Circle(){
    radius = 12;
    pi = 3.141;
  }
  Circle::Circle(double r)
  {
    radius =r;
    pi = 3.141
  }
  double Circle::area(){
    return radius*pi*radius;
  }
```
## Inheritance
* If a class inherits it gets everything from the public to the protected variables/functions from the parent class. 
```C++
class Vehicle{
  protected:
  string Make;
  string Color;
  int Year;
  string Model;

  public:
  Vehicle(){
    Make = "";
    Color = "";
    Year = 0;
    Model = "";
  }
  
  Vehicle(string mk, string col, int yr, string mdl){
    Make = mk;
    Color = col;
    Year = yr;
    Model = mdl;
  }

  void print_details(){
    cout << "Manufacturer: " << Make << endl;
    cout << "Color: " << Color << endl;
    cout << "Year: " << Year << endl;
    cout << "Model: " << Model << endl;
  }
};

class Cars: public Vehicle{
  string trunk_size;

  public:
  Cars(){
    trunk_size = "";
  }

  Cars(string mk, string col, int yr, string mdl, string ts)
    :Vehicle(mk, col, yr, mdl){
    trunk_size = ts;
  }

  void car_details(){
    print_details();
    cout << "Trunk size: " << trunk_size << endl;
  }
};

class Ships: public Vehicle{
  int Number_of_Anchors;

  public:
  Ships(){
    Number_of_Anchors = 0;
  }
  
  Ships(string mk, string col, int yr, string mdl, int na)
  :Vehicle(mk, col, yr, mdl){
    Number_of_Anchors = na;
  }

  void Ship_details(){
    print_details();
    cout << "Number of Anchors: " << Number_of_Anchors << endl;
  }
};

int main(){
  Cars car("Chevrolet", "Black", 2010, "Camaro", "9.1 cubic feet");
  car.car_details();
  
  cout << endl;
  
  Ships ship("Harland and Wolff, Belfast", "Black and whilte",
            1912, "RMS Titanic", 3);
  ship.Ship_details();
}
``` 
* When we make an instance of the derived class, it will first call the default contructor of the parent first and then call the contructor of the derived class. Same with destructor but in opposite order, the dervied class destructor is called first, then the base destructor.
```C++
#include <iostream>
#include <string>

using namespace std;

class Employee
{
    protected:
        string name;
        int ID;
        int reportsTo;
    public:
        Employee(string name, int ID,int boss) : name(name), ID(ID), reportsTo(boss){} // member intializer
        string getName() 
        {
            return name;
        }

        int getID()
        {
            return ID;
        }
        int getBoss()
        {
            return reportsTo;
        }
        void display() 
        {
             cout << ID << " " << name << " reports to " << reportsTo << endl;
        }
        void display(string salutation)
        {
            cout << salutation << " ";
             display();
        }
    
};

class Manager : public Employee
{
    protected:
        string teamName; 

    public:
        Manager(string name, int ID, int boss, string teamName) : Employee(name,ID, boss), teamName(teamName) 
        {
            // here the Employee(name,ID,boss) calls the parent class contructor, and teamName(teamName) is the member intilizer list to give teamName an initial value
        }
        void display() 
        {
             Employee::display();
            cout << "   Heads the team " << teamName << endl;
        }
        void print() // this demonsrates that the dervied class can access all the features of the parent class.
        {
            cout<<name<<ID<<reportsTo<<endl;
        }
};

int main()
{
    Employee worker("John Smith",1,1);
    Manager CEO("Suyash K ",0,0,"bob");
    Manager CTO("Tim",2,0,"IT");
    //worker.display("MR");
    CEO.display();
    CTO.display();
    CEO.print();
   // CEO.display("MR"); // this does not work since the display function is overloaded it cannot call other overloaded functions within itself in the class.

}
```
* Modes of Inheritance
* By using private inheritance, the public and protected members become private in the derived class.
* By using protected inheritance, the public and protected members become protected in the derived class .

* By using public inheritance, the public members remain public.
```C++
#include <iostream>
#include <string>

using namespace std;

class Vehicle 
{
  protected: 
    string Make;
    string Color;
    int Year;
    string Model;

  public: 
    Vehicle(){
      Make = "";
      Color = "";
      Year = 0;
      Model = "";
    }
    Vehicle(string mk, string col, int yr, string mdl)
    {
      Make = mk;
      Color = col;
      Year = yr;
      Model = mdl;
    }
    void print_details()
    {
      cout<<"Manufacturer "<< Make << endl;
      cout<<"Colour "<< Color<<endl;
      cout<<"Year " << Year<<endl;
      cout<<"Model " <<Model<<endl;
    }
};

class Car{
  string trunk_size;

  public:
  Car(){
    trunk_size = "";
  }

  Car(string ts){
    trunk_size = ts;
  }

  void car_details(){
    cout << "Trunk size: " << trunk_size << endl;
  }
};


class Honda: public Vehicle, public Car
{
  int top_speed;

  public:
    Honda(){
      top_speed =0;
    }
    Honda(string mk,string col, int yr,string mdl, string na, int ts) : Vehicle(mk,col,yr,mdl), Car(na) // call the constructors of the other parent classes
    {
      top_speed = ts;
    }

    void Honda_details()
    {
      print_details();
      car_details();
      cout << "Top speed of the car: " << top_speed << endl;
    }
};

int main(){
  Honda car("Honda", "Black", 2006, "Accord", "14.7 cubic feet", 260);
  car.car_details();
  car.print_details();
  car.Honda_details(); // can use child class to call the parent functions if they are public;
}

```
```C++
// In this code the object is looking for a function init, first looks at C->B->A where it finds and executes. Now c.update looks C->B where it finds it in B.  
#include <iostream>
using namespace std;

class A {
  public:
    void init() {
      cout << "Class A initialized!" << endl;
    }
    void update() {
      cout << "Class A updated!" << endl;
    }
};

class B : public A {
  public:
    void update() {
      cout << "Class B updated!" << endl;
    }
};

class C : public B { };

int main() {
  // your code goes here
  C c;
  c.init();
  c.update();
  return 0;
}
```
* The diamond problem solution-> use virtual keyword
* __override__ keyword to override the method in the base class 
* __final__ the method cannot be overwritten. 
* in inheritaince you have to be careful where and when the method is called or looked at, to confrim always use print statments to see how the code is being executed.`

```C++
// Challenge 2 Inheritance
#include <iostream>
#include <string>

using namespace std;

class Animal
{
  private:
    string Name;
    string Sound;
  public:
    Animal(string N,string S){
      Name = N;
      Sound = S;
    }
    void Animal_Details(){
      cout<<Name<<" "<<Sound;
    }
};

class Dog : public Animal {
  private:
    string family;
  public:
    Dog(string Name, string Sound, string fam) : Animal(Name, Sound){
      family = family;
    }
    void Dog_detail(){
      cout<<family;
      Animal_Details();
    }
};

class Sheep : public Animal{
  private:
    string color;
  public:
    Sheep(string Name, string Sound, string c) : Animal(Name,Sound) {
      color = c;
    }
    void Sheep_details(){
      cout<<color;
      Animal_Details();
    }
};

int main(){
  Sheep s("Shaun","Baa","white");
  Dog d("BOB","WOLF","Pomerian");
  d.Animal_Details();
  cout<<endl;
  s.Animal_Details();
}
```
## Polymorism
* can use parent class to point to the address of a child class and still call the child class overriden function-> virtual
* A pure virtual function must be overriden in the child classes
```C++
#include <iostream>
#include <string>
#include <cmath>

class Shape{
  protected: 
    double height;
    double width; 
  public:
    Shape(double l)
    {
      height  = l;
      width = l;      
    }
    Shape (double h, double w){
      height = h;
      width = w;
      }
    virtual double Area(){
      std::cout<<"Called Inital ";
      return height*width;
    }
};

class Circle : public Shape {
  public:
     Circle(double w) : 
     Shape(w){

     }
     double Area(){
      std::cout<<"Called Circle ";
      return 3.142* std::pow((width/2),2);
     }

};

void Showarea(Shape& s)
{
  std::cout<<"Area: "<<s.Area()<<std::endl; // here the shapes are being called from what the actual class they are from instead of calling the most recent one
}                                           // Eg if you get rid of virtual only the inital function is being called

int main()
{
  Shape square(10,15);
  Circle circle(10);
  Showarea(square);
  Showarea(circle);
  return 0;
}
```
* Compoistion is where if the parent dies so do all the children. eg if a car is broken so are all its components (Part of)
* Aggregation is where the children is independent, eg if a person dies in a country doesnt mean that the country dies. (Has a)
* Association is where two classes are related by lines but are not directly tied to each other.

# The Standard Library
* Components of the Standard Template Library are containers, alogorithms that run on containers and iterators which connect the two.
* Containers such as vectors, arrays, lists, deque are sequential containers (unquie domain).
* Assocaitive Containers can be key value pairs, such as set, map which can be ordered or unordered.
* 100+ alogorithms are also given in the standard library.

Min/Max functions-> #include <algorithm>
> * min/max(a,b)-> finds the minimum of a and b
> * min/max(initialiser list) -> finds the minimum in the list.
> minmax(a,b)-> returns the min and max values of a,b

Move/Copy functions -> include <utility>
```C++
#include <utility>
//...
std::vector<int> myBigVec(10000000, 2011);
std::vector<int> myVec;

myVec = myBigVec;             // copy semantic
myVec = std::move(myBigVec);  // move semantic
```
* Moving is cheaper than copying


