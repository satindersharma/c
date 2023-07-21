## Advance


programming paradigms(diffrent way oof building a software)

procedural

functional

object-oriented

event-driven




#### object
A Software entity that has attributes(properties) and fucntions (methods).



#### class 
a blueprint or recipe for creating objects.

#### structures vs classes
structures are more about data
classes are more about data and functionality together.means combinig the data and functionality togather, whch means encapsulation

#### encapsulation
combining  the data and  functions that operate on the data into onoe unit


#### Define a class
add a source file

create two files (we need two fiel one source file wiht cpp extention and header file with h or hpp extenstion)
assume we are creaate ing class rectangle
the header file represet the interface of a class

### Creating a class

`Rectangle.h`

```cpp

#ifndef RECTANGLE_H
#define RECTANGLE_H

#pragma once

class Rectangle
{

};

#endif
```
this header file represent the interface of the reactangle class 
we have to include the header file in the main file

```cpp
 #pragma once is now non-standard
```

```cpp
#ifndef RECTANGLE_H
#define RECTANGLE_H
```
this is the header gaurd. it is saying that if this constant RECTANGLE_H is not define(ifndef RECTANGLE_H) then(define RECTANGLE_H) define it 
```cpp
#endif
```
this tells that it is the end of the define

this help to prevent this file to bieng included multiple times in the complilation process

defination leaves in header .h file, implementation leaves in cpp .cpp file


### `Rectangle.h`

```cpp
#ifndef RECTANGLE_H
#define RECTANGLE_H

class Rectangle
{
int width;
int height;
void draw();
int getArea(); 

};

#endif
```


### `Rectangle.cpp`



```cpp
#include "Rectangle.h"
#include <iostream>

using namespace std;


void Rectangle::draw(){
    cout << "Drawing a rectangle";
    // in htis functio we have access of all the member of the Rectangle class
    // like
    // getArea()
    // width, height
    cout << width << endl << height << endl;

}

int Rectangle::getArea(){

    return width*height;
}
```

### why multple file

`Reactangle.h` if we made changes to this file then this file and any file that is dependent on this file has to be recompiled

`Rectangle.cpp` if we made changes to this file then only this file has to be recomiled and then it it likend with other complied file. so the other file is not going to be recomplied.

this is the reason we need to seperate the implementation class from its interface


### Create a rectangle Object

### `main.cpp`
 
```cpp

#include "Rectangle.h"
#include <iostream>

using namespace std;

int main(){
    Rectangle rectangle1;
    rectangle1.width = 10;// we cannot access it outside the calss as ti is private member
    // this is the main deiffrence fro the strucrtures


    // to make them public
    return 0;
}
```

to make them public  go to `Rectangle.cpp`

```cpp
#ifndef RECTANGLE_H
#define RECTANGLE_H


class Rectangle
{
public:
  int width;
  int height;
  void draw();
  int getArea(); 

};

#endif
```

# to build from multiple files
# `g++ -o main.exe main.cpp ./Rectangle.cpp`

or you can in clue header in compilation
## `g++ -o main.exe main.cpp ./Rectangle.cpp ./Rectangle.h`

## `main.cpp`

```cpp

#include "Rectangle.h"
#include <iostream>

using namespace std;

int main(){
    Rectangle rectangle1;
    rectangle1.width = 10;// we cannot access it outside the calss as ti is private member
    // this is the main deiffrence fro the strucrtures


    // to make them public go to Rectangle.cpp

    rectangle1.height = 20;

    cout<< rectangle1.getArea() ;
    return 0;
}

```



### Data Hiding / Access Modifier

A class Should hide its internal data form the outside code and provide functions for accessing the data.

how can we hide inter data of the objcet. (by using access modifier)(public and private and protected keywords are the access modifier)

we are going to declare 
```cpp

int width;
int height;

```

as private

order is not mendetary , even we can have mulitpl private and public section (but not recomemnded)

### `Rectangle.h`
```cpp
#ifndef RECTANGLE_H
#define RECTANGLE_H

class Rectangle
{
public:

    void draw();
    int getArea(); 
private:
    int width;
    int height;

};

#endif
```


### this is an error

### `main.cpp`

```cpp
rectangle1.width = -1

```
the above will cause error as the width should be a positive number

to tackle this is, we need to use Getter and setter to better manage this

### 7. Getter and Setters
get the value and set the vale
```cpp

// as we make the data private
private:
    int width;
    int height;

// now we need the function for accing that data
// one to get thevalue and other to set the value
```

### `Rectangle.h`
```cpp
class Rectangle
{
public:

    void draw();
    int getArea(); 
private:
    int width;
    int height;

};

#endif
```

#### `Rectangle.cpp`

```cpp
int Rectangle::getWidth() {
    return width
}

void Rectangle::setWidth(int width) {
    if(width < 0)
        throw invalid_argument("width") 
    // set the width , but look it is not appropeiate
    width=width
    // some developer use this approach, prefix member valiable of the classes with m_
    m_width=width
    // some developer use this approach, some change the name of parameter with like theWidth
    width = theWidth
    // but we can use the this pointer, this point to the current object,this is pointer and *this is current object
    (*this).width = width

}
```

now we acnnto use the following in the main.cpp
### `main.cpp`
```cpp
    rectangle1.width = -1
```
### `main.cpp`
```cpp
    rectangle1.width = -1
```

now change the above with the following to test if it goint to give error on negative number
### `main.cpp`
```cpp
int main(){
    Rectangle rectangle1;
    rectangle1.setWidth(-1);
    return 0;
}

```
now you get the exception

same way heigth
```cpp

int Rectangle::getHeight() {
    return height;
}

void Rectangle::setHeight(int height) {
    if(height<0)
        throw invalid_argument("height");
    // some prefer this form also
    Rectangle::height = height;
    // but for consisitency we will use the below notation
    this->height = height;
}

```

this is the benifits of defining getter and setter



#### 8. Constructor
constructor don't have a return time , not even void and there name is same as the class name

```cpp
#include <iostream>

using namespace std;


class Rectangle{

    public:
        Rectangle(int width, int height){
            cout << "callling constructor";
            setWidth(width);
            setHeight(height);
        }


        int getWidth(){
            return width;
        }

        void setWidth(int width){

            if (width<=0){
                throw invalid_argument("Invalid Width argument is passed");
            }
            this->width = width;
        }

        int getHeight(){
            return height;
        }

        void setHeight(int height){

            if (height<=0){
                throw invalid_argument("Invalid height argument is passed");
            }
            this->height = height;
        }

        int getArea(){
            return width*height;
        }
        
    private:
        int width;
        int height;

};

int main(){

    Rectangle rec1(10,20); // call this way or
    Rectangle rec2{10,20}; // call this way or for the most part bothe expression has thesame result, 

    cout << "Width " << rec1.getWidth() << endl;
    cout << "Height " << rec1.getHeight() << endl;
    cout << "Area " << rec1.getArea() << endl;

    return 0;
}
```

#### Member intitializer list



we also have a diffrent and more efficent way to intiatalze 

: then one or more intializer
```cpp
Rectangle(int width, int height):width(width)
```
or
```cpp
Rectangle(int width, int height):width{width} // curly braces is more common in mordern cpp
```
width{width} first on is the width parameter another one is width attribute   // width_parameter{width_attribute}
```cpp
 Rectangle(int width, int height):width{width}, height{height}{ // can define multiplr, and no need to have any thing in body
            
        }

```
if we initialize in the body then compiler gona create he member varaible first and then gona initilize them as an second operation whereas 
if we use member initializer then this happen in one go

also we can initialize like this for the simple attribute only as we canot write like custom logic or validation

also we can use both of this like
```cpp
Rectangle(int width, int height):width{width}{
            setHeight(height);
        }
```

but in our case we cann't use member initializer as we loose the validation logic

so in our case it is better to use like this
```cpp
Rectangle(int width, int height){
            cout << "callling constructor" << endl;
            setWidth(width);
            setHeight(height);
        }
```



#### default constructor
we can create a defult congtsrucgor sho that we can create class wihtou parameter. 
not that just like function we can overload the constructor

```cpp
class Rectangle{

    public:
        Rectangle() = default;// default constructor, also after = default; no need to write its defenation in .h file.

        Rectangle(int width, int height){
            cout << "callling constructor" << endl;
            setWidth(width);
            setHeight(height);
        }

           }
        ...
    private:
        int width = 0;
        int height = 0;

};

```

also rememmber cpp create a default cunstory by it's own 


#### using explicit keyword

to show the use of explicit , let us create a class and a function 


here the class has the only one memenber and constructor is needed only one paramter
```cpp

class Person{
public:
    Person(int age):age{age}{

    }

private:
    int age;
};


void showPerson(Person person){

}

```

so what happen that when we  do something like (in main fn)
```cpp
Person person(20);
showPerson(person);
showPerson(20);
```
`showPerson(person);` is working as expected but in `showPerson(20);` this case what happen is that it create the Person class intance on the fly(eg. here Person person(20))

in this case `showPerson(20);`  compoier is going to do implicit conversion

but it don't make sence (as we are just passing int and it get converted into class obj)

this is why we should use explicit keyword

so

```cpp

class Person{
public:
    explicit Person(int age):age{age}{

    }

private:
    int age;
};


void showPerson(Person person){

}
int main(){
    Person person(20);
    Person person1{30};

    showPerson(person);
    showPerson(20); // now we can't create like this.(now we cna't pass integer to this function. now complier will force use to pass Person class obj
     
    return 0;

}
```


### constructor delegation

first best way to pass string is like this (const string& color)  string& to not make the copy and also const, so we dono't accidently change the value

here is an example , we have added the third memeber color , andlo used an another constructor with color
```cpp
#include <iostream>

using namespace std;


class Rectangle{

    public:
        Rectangle()= default;// default constructor
        Rectangle(int width, int height){
            cout << "callling constructor" << endl;
            setWidth(width);
            setHeight(height);
        }
        // not the below has the duplication of the code
        Rectangle(int width, int height, const string& color){
            cout << "callling constructor" << endl;
            setWidth(width);
            setHeight(height);
            this->color = color;
        }

        int getWidth(){
            return width;
        }

        void setWidth(int width){
            if (width<=0){
                throw invalid_argument("Invalid Width argument is passed");
            }
            this->width = width;
        }

        int getHeight(){
            return height;
        }

        void setHeight(int height){

            if (height<=0){
                throw invalid_argument("Invalid height argument is passed");
            }
            this->height = height;
        }

        int getArea(){
            return width*height;
         }
        
    private:
        int width = 0;
        int height = 0;
        string color;

};



int main(){

    Rectangle rec1(10,20); // call this way or

    cout << "Width " << rec1.getWidth() << endl;
    cout << "Height " << rec1.getHeight() << endl;
    cout << "Area " << rec1.getArea() << endl;

    return 0;

}

```


as you can see the line is duplicated

```cpp
setWidth(width);
setHeight(height);
```

this is where constructor delegation comes to the rescue


```cpp
#include <iostream>

using namespace std;


class Rectangle{

    public:
        Rectangle()= default;// default constructor
        Rectangle(int width, int height){
            cout << "callling constructor" << endl;
            setWidth(width);
            setHeight(height);
        }
        // not the below now using constructor delecation, it is using the constructe above
        Rectangle(int width, int height, const string& color):Rectangle(width,height){
            cout << "counstructing with color"<< endl;
            this->color = color;
        }

        int getWidth(){
            return width;
        }

        void setWidth(int width){
            if (width<=0){
                throw invalid_argument("Invalid Width argument is passed");
            }
            this->width = width;
        }

        int getHeight(){
            return height;
        }

        void setHeight(int height){

            if (height<=0){
                throw invalid_argument("Invalid height argument is passed");
            }
            this->height = height;
        }

        int getArea(){
            return width*height;
         }
        
    private:
        int width = 0;
        int height = 0;
        string color;

};



int main(){

    Rectangle reactange(10,20,"blue");
    
    return 0;

}

```




### the destructor

the destructor is used to relase the memory whiel useing the object

```cpp
~Rectangle(); //remember we can't overload destructor , so each class should have only one destructor
```
here is full exmple

at the end of the main function end the destructor will call

```cpp
#include <iostream>

using namespace std;


class Rectangle{

    public:
        Rectangle()= default;// default constructor
        Rectangle(int width, int height){
            cout << "callling constructor" << endl;
            setWidth(width);
            setHeight(height);
        }
        // not the below now using constructor delecation, it is using the constructe above
        Rectangle(int width, int height, const string& color):Rectangle(width,height){
            cout << "counstructing with color"<< endl;
            this->color = color;
        }

        ~Rectangle(){
            cout << "Destructor called"<< endl;
        }

        int getWidth(){
            return width;
        }

        void setWidth(int width){
            if (width<=0){
                throw invalid_argument("Invalid Width argument is passed");
            }
            this->width = width;
        }

        int getHeight(){
            return height;
        }

        void setHeight(int height){

            if (height<=0){
                throw invalid_argument("Invalid height argument is passed");
            }
            this->height = height;
        }

        int getArea(){
            return width*height;
         }
        
    private:
        int width = 0;
        int height = 0;
        string color;

};



int main(){

    Rectangle reactange(10,20,"blue");
    
    return 0;

}
```


### static member

member that belongs to the class itself


```cpp

#include <iostream>

using namespace std;


class Rectangle{

    public:
        static int objectCounts = 0;
        Rectangle()= default;// default constructor
        Rectangle(int width, int height){
            cout << "callling constructor" << endl;
            objectCounts++;
            setWidth(width);
            setHeight(height);
        }

        int getWidth(){
            return width;
        }

        void setWidth(int width){
            if (width<=0){
                throw invalid_argument("Invalid Width argument is passed");
            }
            this->width = width;
        }

        int getHeight(){
            return height;
        }

        void setHeight(int height){

            if (height<=0){
                throw invalid_argument("Invalid height argument is passed");
            }
            this->height = height;
        }

        int getArea(){
            return width*height;
         }
        
    private:
        int width = 0;
        int height = 0;

};



int main(){

    Rectangle reactange(10,20);
    Rectangle reactange1{10,20};
    cout << Rectangle::objectCounts << endl; // :: is the scope resolution operator. as it belong to class we can't access on object. it is common for all obj
    
    return 0;

}
 
```






