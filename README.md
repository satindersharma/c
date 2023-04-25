# C ++



##### https://code.visualstudio.com/docs/languages/cpp



#### Terminal > Run Build Task command (`Ctrl+Shift+B`)

#### `g++ -o main.exe main.cpp utils/greet.cpp`

#### `g++ -o main.exe main.cpp utils/greet.cpp calcu/calculation.cpp`

#### run by `.\helloworld`



• C++ is one of the oldest yet most popular programming languages in the world due to its performance and efficiency.



• It’s often used in building performance-critical applications, video games (especially with Unreal Engine), servers, operating systems, etc.


• To learn C++, you need to learn the syntax (grammar) of the language as well as C++ Standard Library, which is a collection of pre-written C++ code for solving common problems.


• To write C++ applications, we often use an Integrated Development Environment (IDE). The most popular IDEs are MS Visual Studio, XCode, and CLion.


• To run C++ applications, first we have to compile our C++ code to machine code.


• The main() function is the starting point of a C++ program.



• every 3 year new c plus version is comming



• still the most fast and efficient language



• main function is the enrty point of the program



• before the functin name we should specify the type of value is gona return



c++ statnadard libray


iostream name of one of file in the standard library



std => standard library



cout => charactor out, we can output one or more charactor



`<<` stream insertion operator

`>>` stream exraction operator



complie to machine code , we ge an executable, but it will run on the same os only, for different os we need tho complie on the diffrent os



• We use variables to temporarily store data in the computer’s memory.


• To declare a variable, we should specify its type and give it a meaningful name.


• We should initialize variables before using them. Using an uninitialized variable can lead to unexpected behavior in our programs since these variables hold garbage values.


• Unlike variables, the value of constants don’t change.


• The common naming conventions used in C++ applications are: PascalCase, camelCase, and snake_case.


• An expression is a piece of code that produces a value. A mathematical (arithmetic) expression consists of an operator (+, -, \*, /, %) and two operands.


• Multiplication and division operators have a higher priority than addition and subtraction operators. So, they’re applied first


• We can use parentheses to change the order of operators.


• We use cout (pronounced sea-out) to write characters to the Standard Output Stream which represents the terminal or console window.


• We use cin (pronounced sea-in) to read data from the Standard Input Stream which represents the keyboard.


• We use the Stream Insertion Operator (<<) to write data to a stream.


• We use the Stream Extraction operator (>>) to read data from a stream.


• The Standard Template Library (STL) consists of several files each containing functions for different purposes.


• To use functions in the Standard Library, we should include the corresponding files using the #include directive.


• Using comments we can explain what cannot be expressed in code. This includes why’s, how’s, and any assumptions we made while writing code.



### variables


varibale is a name of lacation of a memmory


declare int a;


if not initialized, due to garbage, data currently in memory



int filze_size = 0, counter = 1;

also this works, but not ecouraged



const double pi = 3.14;

act like js const



int file_size // Snake Case



int FileSIze // pascal case



int fileSize // camel Case



int iFileSize // hugarian case (just like pascal case but the data type is in the front) it is very old , not releven but is in the old window code, that time the ede+itor was ot that feature rich



using namespace std;



now you can use cout instead of std::cout



endl to make a new line charactor



• C++ has several built-in data types for storing integers (whole numbers), floating-point numbers (numbers with a decimal point), characters, and Boolean values (true/false).


• Floating-point numbers are interpreted as double by default. To represent a float, we have to add the F suffix to our numbers (eg 1.2F).


• Whole numbers are interpreted as int by default. To represent a long, we have to use the L suffix (eg 10L).


• Using the auto keyword, we can let the compiler infer the type of a variable based on its initial value.


• Numbers can be represented using the decimal, binary, and hexadecimal systems.


• If we store a value larger or smaller than a data type’s limits, overflowing or underflowing occurs.


• Using the sizeof() function, we can see the number of bytes taken by a data type.


• We can use stream manipulators to format data sent to a stream. The most common manipulators are setw, fixed, setprecision, boolalpha, left, and right.


• The Boolean false is represented as 0. Any non-zero number is interpreted as the Boolean true.


• In C++, characters should be surrounded with single quotes.


• Characters are internally represented as numbers.


• A string is a sequence of characters and should be surrounded by double quotes.


• We use arrays to store a sequence of items (eg numbers, characters, etc).


• Array elements can be accessed using an index. The index of the first element in an array is 0.


• When we store a smaller value in a larger data type, the value gets automatically cast (converted to) the larger type. When storing a large value in a smaller data type, we have to explicit cast the value.


• C-style casting involves prefixing a variable with the target data type in parentheses. In C++, we use the static_cast operator.


• C++ casting is safer because conversion problems can be caught at the compile-time. With C-style casting, we won’t know about conversion issues until the run-time



### fundamental types



| Type      | Bytes | Range                 |
|-----------|-------|-----------------------|
| short     | 2     | -32768 to 32767       |
| int       | 4     | -2BIllion to 2Billion |
| long      | 4     | same                  |
| long long | 8     |                       |

most usfull is short and int


| Type        | Bytes | Range                |
|-------------|-------|----------------------|
| float       | 4     | -3.4E38 to 3.4E38    |
| double      | 8     | -1.7E308 to 1.7E308  |
| long double | 8     | -3.4E932 to 1.7E4832 |


most used double (because float sometime result in lost of accuracy)



| Type | Bytes | Range      |
|------|-------|------------|
| bool | 1     | true/false |
| char | 1     |            |


char a = 'b';


double price = 99.99;



float interestRate = 3.67F; // 3.67F or 3.67f



long file_size = 9000L; // 9000l or 9000L both accepted but L is more used,(if we dont type L this will take it as integer)



char letter = 'a'; // use single qoute for character



bool isValid = true // true/false



we can also use auto , to let the complier infer the type of the variable



auto isValid = true;



int number 1.2;



this will show 1 at terminal



but a better way of intitalization



int number {1.2} /// t his will show compilation errro as float is tried in the int type

int number {} // this will initilize to value 0



number system



demial (base 10) 0-9 255



Binary (base 2) 0, 1 11111111



hexa (base 16) 0-9, A-F FF


```cpp
int number = 0b11111111;

int number = 0xFF;
```

```cpp
unsigned int number = -255; // unsigned cause problem
```

```cpp
unsigned int number = 0;

number--;

cout <<number \\this will cause problem
```


### Narrowing



assigneing higher tpe values ot smaller type


```cpp
int number = 1'000'000;

short another = number;
```


reverse of it(this is not an issue)


```cpp
short number 100;

int another {number}
```

```cpp

cout << sizeof(int); // size of bytes
```

```cpp
#include <limits>

cout << numeric_limits<int>::min() << endl // numeric_limits is a class

<< numeric_limits<int>::max() //this line will let you know the limit of the integer values
```


#### what happen if we store value larger than the limit


```cpp
#include <limits>

int number = numeric_limits<int>::max();

number++;

cout << number; // this will result in smallest value, this is called overflow(the number was too big for it)
```

```cpp
#include <limits>


int number = numeric_limits<int>::min()

number--;

cout << number; // this will result in largest value, this is underflow(the nuber was too small for it)
```

```cpp
bool isvalid = false;

cout << boolalpha << isValid; // otherwise this wll return 0 on termnal
```


char for single

string for seq of character



computer reperenst it asnumber is numeric


```cpp
char ch = 'a'; // use singel qoute for char

cout << ch;

cout << +ch; // this will print the nueric reperesentaion of charactor a
```

```cpp
char ch = 98;

cout << ch;
```

```cpp
string name = "ajay sharma"; // for sequence of character
```

```cpp
#include <string>

string name;

cout << "Enter Your name";

cin >> name;

cout << "Hi " << name; // this will missout naythin after first whitespace
```


use


```cpp
#include <string>

string name;

cout << "Enter Your name";

getline(cin, name)

cout << "Hi " << name; // this will show your name
```


to store list of integer


```cpp
int numbers[5]; to write an array with the 5 integer values

cout << numbers; // this will print the hexadecimal address of the array
```

```cpp
cout << numbers[0]; // this will print out 0

cout << numbers[1]; // this will print out 0 // by default at all places it keep integer 0
```

```cpp
int numbers[5];

numbers[1] = 10;

cout << numbers[1];
```

```cpp
cout << numbers[5]; this will print the any number that garbage collector found at that time
```

```cpp
int numbers[5] = {10,20}

cout << numbers[0]; //
```

```cpp
int numbers[] = {10, 20}; // to let the compiler decide how many values need
```

```cpp
int x = 1;

double y = 2.0;

int z = x + (int)y; // c style casting,but if conversion cannot be done wi won't know untill run time

int z = x + static_cast<int>(y);// this will show error on compile time if error on conversion(casting)

cout << z;
```



```cpp
int x = 10;

int y = 3;

double z = x / y; this will return int, to solve this caste any one value

double z = static_cast<double>(x) / y;
```


comparison operator


expression is a peiceof code that produce a value
```cpp
int x = 10;
int y = 15;
boal isValue = x != y;
cout << boolalpha << isValue 
```

```cpp
int x = 10;
double y = 15;
boal isValue = x == y; // c automatically convert the lower datatypes to upper data types
cout << boolalpha << isValue
```

logical variable (&&, ||, !)

```cpp
int age = 18;
bool isEledgible  = age > 18 && age < 65;   // c check from left to right
cout << boolalpha << isEledgible;
```

```cpp
int age = 18;
bool isEledgible  = age > 18 || age < 65;   // c check from left to right, both are checked
cout << boolalpha << isEledgible;
```

```cpp
int age = 18;
bool isEledgible  = age > 18 || age < 65;   // c check from left to right, both are checked
cout << boolalpha << !isEledgible; // not logical operator
```

preority order
() // higest prioritiy
! 
&&
|| 



```cpp
bool a = true;
bool b = false;
bool c = false;
bool result = b && !a;
bool result = a || b && c;
cout << boolalpha << result;
```


if statements


```cpp
int temp = 30;
if (temp < 60)
    cout << "Cold"
```

```cpp
int temp = 70;
if (temp < 60)
   cout << "cold";
cout << "warm";
```


If there is more than one statements in if the use paranthisis


```cpp
int temp = 70;
if (temp < 60){
   cout >> "new cout"
   cout << "cold";
   }
cout << "warm";
```


```cpp
int temp = 70;
if (temp < 60)
   cout << "cold";
else if(temp > 20){
    cout << "else if part"
    }
else
   cout "else part"
cout << "warm";
```

also we can write in one line

```cpp
int temp = 70;
if (temp < 60) cout << "cold";
else if(temp > 30) cout << "else if part";
else cout "else part";
cout << "warm";
```

nested if 

```cpp
int temp = 70;
if (temp < 60)
   cout << "cold";
   if (temp < 60)
    cout << "nested cold";
else if(temp>30){
    cout << "else if part"
    }
else
   cout "else part"
cout << "warm";
```

```cpp
int sales = 1'000;
if (sales > 10'000)
   commision = .1;
else
   commision = .05;
 // the below is same as the above 4 lines
double commission = (sales > 10'000) ? .1 : .05;  condidition ? if value is true : if value is false
```


switch statement(to caire variablle with a set of values)

```cpp
cin >> input;

switch (input){
    case 1:
        cout << "You selected 1";
        break; // break is must other wise it will print case 2 also even it is not true
    case 2:
        cout << "you selected 2";
        break;
    default:
        cout << "good bye" // as this is the last statement, there is no break statement needed as there is notheing to execute after that

```

loops

to repeat 1 or more example
```cpp
for (int i = 0; i < 5; i++)  {   // intial value, condition, increment/decriment,      wrap in braces for more exp, controller
  cout << i <<endl;
}
```


```cpp
for (int i = 5; i > 0; i--)  // intial value, condition, increment/decriment,      wrap in braces for more exp
  cout << i <<endl;
```


```cpp
int numbers[] = {1,2,3}
for (int i = 0; i < 3; i++)
    cout << numbers[i] << endl;
```


but we are hardcoding it (ie i < 3)
```cpp
int numbers[] = {1,2,3,4}
// sizeof(numbers): 16  // this might not same on every os
// sizeof(int): 4
for (int i = 0; i < sizeof(numbers) / sizeof(int); i++)   // now this is dynamic, but there is a newer way in morder cpp
    cout << numbers[i] << endl;
```


    
    
 range base for loop
 ```cpp
 for (int number:numbers)
      cout << number << endl;
      
```

 ```cpp
string name = "Mosh Hamedani";
for (char ch:name) // we can loop over string also
    cout << ch << endl;
```


while loop

```cpp
int i = 1;
while (i <= 5){
    cout << i << endl;
    i++;
}  
```


do{  // braces are requied here
     // do will run atleast one time
}while()

```cpp
do{
cout << "Enter a number "
int number; // so take this variable outside of do
cin >> number;
} while (number < 1 || number > 5) // the number is not accsibe here, as in cpp vairable is on ly accible in the scope of the block in wich it declare

```

```cpp
int number; // so take this variable outside of do
do{
cout << "Enter a number "

cin >> number;
} while (number < 1 || number > 5) // the number is not accsibe here, as in cpp vairable is on ly accible in the scope of the block in wich it declare

```

break & continue

nested loop

 
function

if a function doesnot return a value then type void keyword
```cpp
viod greet(){
    cout << "hell" << endl;
    }

int main(){
    greet()
    cout << "o";
}
```

```cpp
void greet(string firstName, string lastName){
    cout << "hell" << firstName " " << lastName << endl;
    }

int main(){
    greet("ajay","sharma")
    cout << "done";
}
```


parameter the names that define in the function
arguments are the values that is applied to those parameters


```cpp
void greet(string firstName, string lastName){
    cout << "hell" << firstName " " << lastName << endl;
    }
string full_name(string firstName, string lastName){
    return  firstName + " " + lastName;
    }

int main(){
    greet("ajay","sharma")
    string name = fullname("ajay","Kumar")
    cout << name;
    cout << "done";
}
```

```cpp
int max(int first, int second){
    if (first > second)
        return first;
    else
        return second;
}

int max(int first, int second){
    if (first > second)
        return first;
    return second;
}

int max(int first, int second){
    return (first > second) ? first : second;
}
```

function with default value(should be at the end)
```cpp
double calculateTax(double income, double taxRate = .2){
    return income * taxRate;
}
```

fucntion overloading
```cpp
// in overloading each function should have unique signature
void greet(string name){  // this is valid
    cout << "Hello " << name;
    }
/*
*void greet(string name,string lastname){  // this is not valid, as this has the same signature as the next one
*    cout << "Hello " << name;
 *   }
 
 */
 
 
// signature = name of the function + (number and type of parameter)        here we have name greet and 2 parameter of string type   
void greet(string title, string name){
    cout << "Hello " << title << " " << name;
    }
    
 int main(){
    greet("ajay")
    greet("ajay" , "sharam")
}
```


passing arguments by value or reference(by default it is passed as value in c)

```cpp
void increaseNumber(double price){ // as the parameter have the block level scope
    // price = price * 1.2;
    price *= 1.2;
    }
    
    
int main(){
    double price 100;
    increaseNumber(price); // this will act like a copy of price is passed to the function
    cout << price;  //thus this not gaonna change
    }
```


```cpp
void increaseNumber(double& price){ // now this will act as pass by reference
    price *= 1.2;
    }
   
int main(){
    double price 100;
    increaseNumber(price); 
    cout << price;  //due to apprasent in function, thus this gonna change
    }
```
the above is helpful if we have large amount of data, so copy may decrrease the efficincy

```cpp
void greet(string& name){
    cout << "Hello " << name;
    }

int main (){
    string name = "aja";
    greet(name);
    cout << name;
    return 0;
    }
```

```cpp
void greet(string& name){
    cout << "Hello " << name;
    name = "abc"; //will change the name value in the main function also
    }

int main (){
    string name = "aja";
    greet(name);
    cout << name;
    return 0;
    }
```

to prevent accidental change of refernce value use const


```cpp
void greet(xonst string& name){  // use const so there is no changes by any mistake
    cout << "Hello " << name;
    }

int main (){
    string name = "aja";
    greet(name);
    cout << name;
    return 0;
    }
```

### local and global variable


```cpp
int taxRate = 20; // global variable

double calculateTax(int sales){
    return sales * taxRate; // this is available in the function as it is in global scope
}



int main (){
    // this is an local variable
    int sales = 10'000;
    double tax = calculateTax(sales);
    cout << tax;
    return 0;
    }
```

function decalaration

```cpp
int main(){
    greet("AJ"); // this will throw error as main doesnt know about function greet, in another words it should be define before main
    return 0;
 }
 void greet(string name){
    cout << "Hello " << name;
    }
```


```cpp
// function decaleration (function prototype)
void greet(string name)


 int main(){
    greet("aBC");
    return 0;
 }
 
 // function defination
 void greet(string name){
    cout << "Hello " << name;
    }
```

---

### organizing functions in file

#### `HelloWorld/main.cpp`

here we are tring to define the greet function in another file

this will be helpfull to make file size small, and we are also able to use it in another files or project
```cpp
#include <iostream>

using namespace std;

// function decaleration (function prototype)
void greet(string name);

int main(){

    greet("ajay")
    
    return 0;
}

// function defination
void greet(string name){

cout << "Hello " << name;

}
    
    
```

create a new directory to work with

eg
#### `HelloWorld/utls`

add 2 files in this directory
1. the header file  // eg `greet.h` or `greet.hpp` both works but  `greet.hpp` is more common
2. the implemientaion file // eg `greet.cpp`


#### `HelloWorld/utls/greet.cpp`

```cpp
#include <iostream> // you have to include this at the top

using namespace std;

// function defination
void greet(string name){

cout << "Hello " << name;

}
```

#### `HelloWorld/utls/greet.hpp`

```cpp
#include <string> // we could #include <iostream> but it is not neccessary here so only using #include <string> where the string class is defined


// function decaleration (function prototype)
void greet(std::string name);  //now as we included #include <string> change string to std::string

```

now in our main file becomes like this

#### `HelloWorld/main.hpp`
```cpp
#include <iostream>
#include "utils/greet.hpp"

using namespace std;

int main(){

greet("AJ")

return 0;

}


```
the above file still cause error on build time


if you include #include "utils/greet.hpp"in another (like we did in main.cpp) this will cause error, so wee need to tell to `only include this once`

#### go to `HelloWorld/utls/greet.hpp` and use another derective ifndef

```cpp
#ifndef UTILS_GREET               // #ifndef the any constant(here we used UTILS_GREET)
#define UTILS_GREET                //if not defined , define it UTILS_GREET (both spelling should be exactly the same)

#include <string>

void greet(std::string name);

#endif
```

when the above lines run first it check for if not define, the run all the code inside(define it and all code) utils to we get to endif
but when it runs again ,now the constant UTILS_GREET is defien so it will not run the code inside

### to build from multiple files

### `g++ -o main.exe main.cpp utils/greet.cpp`



###  namespace

#### `utils/greet.hpp`
```cpp
#ifndef UTILS_GREET               // #ifndef the any constant(here we used UTILS_GREET)
#define UTILS_GREET                //if not defined , define it UTILS_GREET (both spelling should be exactly the same)

#include <string>
namespace messaging {

    void greet(std::string name);
}

#endif
```

#### `utils/greet.cpp`
```cpp
#include <iostream>

using namespace std;

namespace messaging {
    void greet(string name){
        cout << "Hello " + name

        }
}
```

#### `main.cpp`

```cpp
#include <iostream>
#include "utils/greet.hpp"

using namespace std;

int main(){
    messaging::greet("AJ")
    return 0;
}

```
#### another version

```cpp
#include <iostream>
#include "utils/greet.hpp"

using namespace std;
using namespace messaging;


int main(){
    greet("AJ")
    greet("AJ")
    greet("AJ")
    greet("AJ")
    return 0;
}

```

#### another version
sometiem we may need to import only specific function only form a namespace
```cpp
#include <iostream>
#include "utils/greet.hpp"

using namespace std;
using messaging::greet;


int main(){
    greet("AJ")
    greet("AJ")
    greet("AJ")
    greet("AJ")
    return 0;
}

```

#### if you only need cout, or any specific one

```cpp
using std::cout;
```
```cpp
using std::cout;
using std::cin;
```
```cpp
using std::cout, std::cin;
```


