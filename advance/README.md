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

#### new example

### `Alt + x` type TextBox













