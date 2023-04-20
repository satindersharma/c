# C ++


###### https://code.visualstudio.com/docs/languages/cpp

#### Terminal > Run Build Task command (`Ctrl+Shift+B`)

#### run by `.\helloworld`


•
C++ is one of the oldest yet most popular programming languages in the world due to
its performance and efficiency.
•
It’s often used in building performance-critical applications, video games (especially
with Unreal Engine), servers, operating systems, etc.
•
To learn C++, you need to learn the syntax (grammar) of the language as well as C++
Standard Library, which is a collection of pre-written C++ code for solving common
problems.
•
To write C++ applications, we often use an Integrated Development Environment
(IDE). The most popular IDEs are MS Visual Studio, XCode, and CLion.
•
To run C++ applications, first we have to compile our C++ code to machine code.
•
The main() function is the starting point of a C++ program.


every 3 year new c plus version is comming

still the most fast and efficient language

main function is the enrty point of the program

before the functin name we should specify the type of value is gona return

c++ statnadard libray

iostream name of one of file in the standard library


std => standard library

cout => charactor out, we can output one or more charactor

`<<` stream insertion operator
`>>` stream exraction operator

complie to machine code , we ge an executable, but it will run on the same os only, for different os we need tho complie on the diffrent os


We use variables to temporarily store data in the computer’s memory.
•
To declare a variable, we should specify its type and give it a meaningful name.
•
We should initialize variables before using them. Using an uninitialized variable can
lead to unexpected behavior in our programs since these variables hold garbage values.
•
Unlike variables, the value of constants don’t change.
•
The common naming conventions used in C++ applications are: PascalCase,
camelCase, and snake_case.
•
An expression is a piece of code that produces a value. A mathematical (arithmetic)
expression consists of an operator (+, -, *, /, %) and two operands.
•
Multiplication and division operators have a higher priority than addition and
subtraction operators. So, they’re applied first


We can use parentheses to change the order of operators.
•
We use cout (pronounced sea-out) to write characters to the Standard Output Stream
which represents the terminal or console window.
•
We use cin (pronounced sea-in) to read data from the Standard Input Stream which
represents the keyboard.
•
We use the Stream Insertion Operator (<<) to write data to a stream.
•
We use the Stream Extraction operator (>>) to read data from a stream.
•
The Standard Template Library (STL) consists of several files each containing functions for
different purposes.
•
To use functions in the Standard Library, we should include the corresponding files
using the #include directive.
•
Using comments we can explain what cannot be expressed in code. This includes why’s,
how’s, and any assumptions we made while writing code.


variables

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

endl  to make a new line charactor



•
C++ has several built-in data types for storing integers (whole numbers), floating-point
numbers (numbers with a decimal point), characters, and Boolean values (true/false).
•
Floating-point numbers are interpreted as double by default. To represent a float, we
have to add the F suffix to our numbers (eg 1.2F).
•
Whole numbers are interpreted as int by default. To represent a long, we have to use
the L suffix (eg 10L).
•
Using the auto keyword, we can let the compiler infer the type of a variable based on its
initial value.
•
Numbers can be represented using the decimal, binary, and hexadecimal systems.
•
If we store a value larger or smaller than a data type’s limits, overflowing or underflowing
occurs.


•
Using the sizeof() function, we can see the number of bytes taken by a data type.
•
We can use stream manipulators to format data sent to a stream. The most common
manipulators are setw, fixed, setprecision, boolalpha, left, and right.
•
The Boolean false is represented as 0. Any non-zero number is interpreted as the
Boolean true.
•
In C++, characters should be surrounded with single quotes.
•
Characters are internally represented as numbers.
•
A string is a sequence of characters and should be surrounded by double quotes.
•
We use arrays to store a sequence of items (eg numbers, characters, etc).
•
Array elements can be accessed using an index. The index of the first element in an
array is 0.
•
When we store a smaller value in a larger data type, the value gets automatically cast
(converted to) the larger type. When storing a large value in a smaller data type, we
have to explicit cast the value.
•
C-style casting involves prefixing a variable with the target data type in parentheses. In
C++, we use the static_cast operator.
•
C++ casting is safer because conversion problems can be caught at the compile-time.
With C-style casting, we won’t know about conversion issues until the run-time


fundamental types

Type        Bytes        Range
short       2           -32768 to 32767
int         4           -2BIllion to 2Billion
long        4           same
long long   8           
most usfull is short and int

float       4          -3.4E38 to 3.4E38
double      8          -1.7E308 to 1.7E308
long double 8          -3.4E932 to 1.7E4832

most used double (because float sometime result in lost of accuracy)

bool        1               true/false
char        1                    





double price = 99.99;

float interestRate = 3.67F; // 3.67F or 3.67f 

long file_size = 9000L; // 9000l or 9000L both accepted but L is more used,(if we dont type L this will take it as integer)

char letter = 'a';  // use single qoute for character

bool isValid = true // true/false

we can also use auto , to let the complier infer the type of the variable

auto isValid = true;


int number 1.2;

this will show 1 at terminal

but a better way of intitalization

int number {1.2} /// t his will show compilation errro as float is tried in the int type
int number {}  // this will initilize to value 0


number system

demial (base 10)   0-9       255

Binary (base 2)    0, 1      11111111

hexa (base 16)     0-9, A-F  FF

int number = 0b11111111;
int number = 0xFF;


unsigned int number = -255; // unsigned cause problem

unsigned int number = 0;
number--;
cout <<number   \\this will cause problem


### Narrowing
assigneing higher tpe values ot smaller type

int number = 1'000'000;
short another = number;


reverse of it(this is not an issue)

short number 100;
int another {number}


cout << sizeof(int); // size of bytes


cout << numeric_limits<int>::min() << endl                // numeric_limits is a class
     << numeric_limits<int>::max()                        //this line will let you know the limit of the integer values


     
#### what happen if we store value larger than the limit

int number = numeric_limits<int>::max();
number++;
cout << number;  // this will result in smallest value, this is called overflow(the number was too big for it)
     
     
int number = numeric_limits<int>::min()
number--;
cout << number; // this will result in largest value, this is underflow(the nuber was too small for it)


bool isvalid = false;
cout << boolalpha << isValid; // otherwise this wll return 0 on termnal

char for single
string for seq of character

computer reperenst it asnumber is numeric

char ch = 'a'; // use singel qoute for char
cout << ch;
cout << +ch; // this will print the nueric reperesentaion of charactor a

char ch = 98;
cout << ch;

string name = "ajay sharma"; // for sequence of character


string name;
cout << "Enter Your name";
cin >> name;
cout << "Hi " << name; // this will missout naythin after first whitespace

use

string name;
cout << "Enter Your name";
getline(cin,  name)
cout << "Hi " << name; // this will show your name


to store list of integer

int numbers[5]; to write an array with the 5 integer values
cout << numbers; // this will print the hexadecimal address of the array

cout << numbers[0]; // this will print out 0
cout << numbers[1]; // this will print out 0 // by default at all places it keep integer 0



int numbers[5];
numbers[1] = 10;
cout << numbers[1];








