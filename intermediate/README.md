## Intermediated


```cpp
#include <iostream>

using namespace std;
int main(){
   int numbers[] =  {10,20}
  for (int number:numbers)
      cout << number << endl;
   return 0;
}
```

// size is the prefered way
```cpp
#include <iostream>

using namespace std;
int main(){
  int numbers[] =  {10,20}
  for (int i=0; i< size(numbers); i++)
      cout << numbers[i] << endl;
   return 0;
}
```

#### copy array

we cannot assign one array to another one like
```cpp
int first[] = {10, 20, 30};

int second[] = first // this will not work

int second[3];

  second = first; // this will also not work, we can't directly copy array in c,we can't assign one array to another one(you have to loop over it and copy each element sepratly


```


we have to copy each element seperatly
```cpp
int first[] = {10, 20, 30};

// int second[3];
int second[size(first)];

for (int i = 0; i < size(first); i++)
  second[i] = first[i]                      // this is the correct way to copy array in c

```

#### comparing array

```cpp

int first[] = {10, 20, 30};

int second[] = {10, 20, 30};


if (first == second) // this will always false, even the values are same, there memeory address is always different
  cout << "equal"
  

```
```cpp

int first[] = {10, 20, 30};

int second[] = {10, 20, 30};
bool areEqual =  true;
for (int i = 0; i < size(first); i++)
  if (second[i] != first[i]){
      areEqual = false;
      break;
      }

cout << boolalpha << areEqual << endl;
      

```

### passing array to function
```cpp

#include <iostream>

using namespace std;
// when you print an array it show the address of the array more specificaly the addressof the first array element
// what is happening here is that now our integer array is converted into integer pointer  i.e int[] -> int*
// so it donen't make sence to loop over an integer pointer which is just a number 
void printNumbers(int numbers[]){
   for(int number: numbers)  // this will give compilation error as it is looping over a number
      cout << number;
}

// even the size funtion will not work as it hase interger point er which is an memory address number, so function size to int

void printNumbers(int numbers[]){
   for (int i = 0; i <size (numbers); i++) // as this size over here has nno kowlege about the size of array
      cout << numbers[i];

// so we have to pass the size of the array in fuction 
void printNumbers(int numbers[], int size){
   for (int i = 0;i < size; i++)
      cout numbers[i];
      
 }
 
 ```
 
 
```cpp

#include <iostream>

using namespace std;
 void printNumbers(int numbers[], int size){
   for (int i = 0; i < size; i++)
      cout numbers[i];
      
 }
 
 ```
 
 
 #### size_t
 
 if you have a 32 bit compiler the size of size_t is unsigned int otherwiise if you have a 64 bit compiler the size is unsigned long long
 
 i.e 
 
 ##### size_t = unsigned int(on system 32)
 
 ##### size_t =  unsigned long long(on system 64)
 
 
```cpp

cout << sizeof(long long) << endl;
cout << size(size_t) << endl;  // this will return size of 8 byte// here size_t is the type of size() function

```

#### unpacking array

```cpp
int values[3] = {10,20,30};

// C++: structured binding
// JavaScript: destructuring
// Python: unpacking

// one way to do that is 
int x = values[0];
int y = values[1];
int z = values[2];

// new way

auto [x,y,z] = values;

cout << x << ", " << y << ", " << z << endl;

```

#### searching array
###### linear search element

best is O(1) worst is O(n) we need iterate over entire array to find it

this is called linear search as the cost of the algorithum is is direct propostion to the size of the array, as our array grow the cost grow

many other algorathe are
binary search
ternary search
jump search
exponential search

```cpp

int find(int numbers[], int size, int target){

   for (int i = 0; i< size ; i++)
      if(numbers[i] == target)
         return i;
         
  return -1;
  }
  
  
  
  int main(){
  int numbers[] = {10,20,30}
  
  cout << find(numbers,size(numbers)) << endl;
  
  returnn 0;


}

```


#### sorting array

bubble sort
Selection sort
Insertion sort
Merge sort
Quick sort

##### bubble sort

compare two consicutive array element and swap the in asseinding order
eg {8,2,4,1,3}
it first iteration the above became(8,2 became 2,8 
{2,8,4,1,3} // swap 8,2
{2,4,8,1,3} // swap 8,4
{2,4,1,8,3} // swap 8,1
{2,4,1,3,8} // swap 8,3

as the  largest item automaticly came(bubble up) at last, therefore it is called buble sort

// after each pass the next largest item moves to correct possition
{2,1,4,3,8} // swap 4,1
{2,1,3,4,8} // swap 4,3


// again on more pass

{1,2,3,4,8} // swap 2,1

now our arry is fully sorted

```cpp

void swap(int numbers[], int i, int j){
   int temp = numbers[i];
   numbers[i] = numbers[j]
   numbers[j] = temp;
   
   }

void sort(int numbers[], int size){

for (int pass = 0; pass<size;pass++){

   for (int i = 1;i < size; i++)

      if (numbers[i] < numbers[i - 1]){
         // int temp = numbers[i];
         // numbers[i] = numbers[i-1];
         // numbers[i-1] = temp;
         swap(numbers,i, i-1)
         }

   }
   
  int main (){
   int numbers[] = {30,10,20}
   
   sort(numbers,size(numbers))
   
   for (int number:numbers):
      cout << number << endl;
 return 0;
 }
 
 ```
 
 ### mulit demientional array
 
 ```cpp
 int main(){
 // 2X3 matrix
 //  int matrix[2][3] = {
 //              {1,2,4},
 //              {23,34,12}
               }
 int rows =  2;
 int columns = 3;
 
    int matrix[row][columns] = {
               {1,2,4},
               {23,34,12}
               }
 
 // the outer loop is gnna use for the row and inner fo the coumns
 
 
 for  (int row = 0; row < rows; row++){
   for (int col = 0; col < columns; col++)
      cout << matrix[row][col
   }
   round 0;
   
   
   }
 ```



## pointers

A special variable that hold the address of another variable in memory

why to use pointer

efficiently passing large objects(instead of copying them pass by the reference )
dynamic memory allocation(help to reisize an arry dynamically at run time)
enabling polymorphism



```cpp
int main(){
int number = 10;
cout << &number << endl; // to print the address of number

int* ptr = &number; // this is the interger pointer ptr (remember the type should be always same)
// int* ptr; /// again here it will point to nay variable address in the garbage, it will throw the error of memory address violation, so always intitalize a ptr

// int *ptr = &number; this is also valid

// The address-of operator
// int* ptr  = nullptr; // a nullptr is a pointer that don't point to anything,
// in older c++ we use
// int* ptr = NULL or int ptr = 0, but now int* ptr  = nullptr;  is the prefered way
cout << ptr;


//how to access pointer value (by using * at front of the pointer)

cout << *ptr; //t his will print out the value


// we can also change the value to the target memeory location
// inderection (de-reference) operator
*ptr  = 20;

cout << number << endl;


return 0;
}

```


```cpp

int main(){

int x = 10;
int y = 20;
int* ptr = &x;
*ptr *= 2;
ptr = &y;
*ptr *= 3;

return 0;

}
```
#### constant pointer
```cpp

int main(){

   const  int x = 10;
   // we can't have an interger pinter poit to contant integer. types hould be itdenticals
   int* ptr = &x;
   // so make it
   const int* ptr = &x; /// in this senrio the target data is constance but pointer is not
   
   // so we cant do
   *ptr = 20; //as it is same as x = 20, which is not allowed
   
   int y  = 30;
   // this valid as our pointer is not constant
   ptr = &y;
   
   
   
   
return 0;

}

```

here is  another examples where pointer is constant

```cpp

int main(){

int x = 10;
int* const ptr = &x; // now we have an connstant pointer

// senerio where both data and pointer are constant

const x = 10;
const int* const ptr = &x;// we have a const pointer pointing to constant int

return 0;
}
```

#### passing pointers to function

// by default it is passed by value(no by reference), so 
```cpp

void increasePrice(double price){ // here price parametere here is like local variable in the function
price *= 1.2;

}

int main(){
double price = 100;
increasePrice(price);
cout << price;
}
return 0; 

```
### how to make it reference (the more mordern way)
```cpp

void increasePrice(double& price){ // now here it is passed as reference
   price *= 1.2;

}

int main(){
double price = 100;
increasePrice(price);
cout << price;
}
return 0; 

```

#### how to make it reference (another but old way)
```cpp

void increasePrice(double* price){ // defien as poineter
   // use indirection operator
   *price *= 1.2;

}

int main(){
double price = 100;
increasePrice(&price); //pass address of price
cout << price;
}
return 0; 

```


#### swap two variables with pointer

```cpp

void swap(int* first, int* second){
int temp = *first;
*first = *second;
*second = temp;
}

int main(){
   int x = 10;
   int y = 20;
   swap(&x, &y);
   
   cout << x << endl << y << endl;

   return 0;
}
```

### relationship btw array and pointer

```cpp
int numbers[] = {10,20,30}

// as cout print the address of the 1st elemt of the array we can use indirection to print the value of first item in array
cout << numbers;// address of first elemtn of the array
cout << *numbers

int* ptr = numbers;
cout << ptr; // address
cout << *ptr; // value of the first elemtn in  the array
cout << ptr[1]; // value of the seconnd element in the array
```

### the array passing to function

```cpp

void printNumbers(int numbers[]){
   numbers[0] = 0;
}


int main(){
int numbers[] = {10, 20, 30}
printNumbers(numbers); // c++ compiler always passes array pointer to the funciton(this is more efficient then copying array and passing to the function)
cout << numbers[0] << endl; // this number is changed

}
```

### pointer arthemics

below assume that the pointer address is 100(actually it is hexa decimal, but for simpllicity we are taking decimal), so when we do ptr++ it will become 104,
because on most of the machine int take 4 bytes so the first element in the array takes from 100 - 103 (4 byte space)
so on ptr++ it gonna increase like sizeof(data)  size of data type

```cpp

int main(){
int numbers[] = {10, 20, 30}
int* ptr = numbers;
// 100
ptr++ // it became 104, so it is pointing to the start of second element
// ptr-- // this will again start to point to 1st element
cout << *ptr;



// also  on add opereator

cout << *(ptr +1); // next value, it is same as bellow
cout << ptr[1]; //under the hood this is rewirte as above, it is same as below, better approach wiht pointer
cout << numbers[1];
}

```

ptr != nullptr


```cpp

// {10,20,30} create a pointer and print in reverse

int numbers[] = {10,20.30};
int* ptr = &numbers[size(numbers) - 1];//get the address of the last element in the array
// while (ptr >= &numbers[0]) // &numbers[0] is same as numbers (as by default it return the address of first element of the array, so
while (ptr >= numbers) // 
   cout << *ptr << endl; // dereference tht pointer,(i.e print the value)
   ptr--; //move the pointer to previous element

```

#### dynamic memory allocation

there is case we have alocated a high memory whereas the array has only one value,.
so there is way you can intialize with a given size, but also can change dynamiclly

by default the memory is clieaned up on block end, but in case of heap programmer is responseible for the cleanup,
otherwise this memry is never gona realse and eventually gonna crash. we say our program is having a memory leak, meaning it constatly ocnsuming more and more memory

so we dealocate the memeory using delete operator

```cpp
// int numbers[1000];

// by this sytanx variable is diclared in a part of memery called Heap(free store)
int* numbers = new int[10]; // this return an integer pointer
int* num = new int;
delete[] numbers;// here we dealing with array so delete[] followed by the name of the pointer
delete num;
// also it is not mendetory but we reset these pointer to nullptr

numbers = nullptr;
num = nullptr;
```

#### smart pointers
real life program has 1000s of pointer so it is hard to track and delete is realy dificult, hats way in mordern c++ we have the concept of smart pointer which free use from delting the pointer


#### Types of smart pointers

###### Unique pointers
###### Shared pointers



#### Unique pointers

means only one pointer is ownig a memory address

first include another fie from the statdanrd library called memery
```cpp
#include <iostream>
#include <memory>

using namespace std;

int main(){

// class used for unique pointer
unique_ptr 
// class used for unique pointer, use angle brackets <> to specifiy the type of pointer we are gona create, 
unique_ptr<int>  x(new int); // unique_ptr<int>  is the type, x vaiable name, (new int)  new operator to create integer pointer
// here x(new int) essentianly we are create int poinerter here ((new int) and we are passing that to x which is called an object
// so x is an instance of unique_ptr (unique pointer) class

// now we can work with it
cout << x; // will see a memery address

// we can derefernce it
*x = 10;
// and print it

cout << *x; //but remeber we cannot perform arthmetic operation on unique pointer

// x++ or x-- will not work

```
##### there is a simpler way to create a unique pointer

using `make_unique<>`

```cpp
#include <memory>

// make_unique<int> // to create interger pointer , this return an instance of unique_ptr class , so we can write it as
unique_ptr<int> y = make_unique<int>();
// as above we can see th that it gona return unique pointer of int , then we can eaily use auto keyword, so we are letting the compiler infer the type of 
auto y = make_unique<int>();

```
we are not limited to only int , we can create any datatype , for eg

```cpp
#include <memory>
auto numners = make_unique<int[]>(10); // int array with initial size of 10 , not working
numbers[0] = 10;
cout << numbers[0];
```

##### shared pointer
```cpp
#include <memory>
using namespace std;
int main(){

shared_ptr<int> x(new int); // or
shared_ptr<int> x = make_shared<int>(); // or
auto x = make_shared<int>();
*x = 10;
shared_ptr<int>y(x); // y is sharing the memory address of x
if (x == y)
   cout << "Equal" //
cout << *x;
cout << *y;


return 0;
}

```

---
#### strings


##### old way(c string) (before string type is created)
```cpp
// here we can store only 4 characters as the last character alway should be Null terminator (\0)
char name[5] = {'h','e','l','l','\0'} \\ using \0 we re[esent end of string
// there is a simpler way
// string literal
char name[5] = "Josh" \\ no need to add \0 as it is automaticlly added

we can change idividual char like
name[0] = 'H'

cout << name[0];
```

we have bunch of function to work with c string , all this are defiend in the file called cstring
here are some of them
   
###### strlen
   
   
```cpp
#include <iostream>
#include <cstring>
using namespace std;
   
int main(){
   char name[5] = "Hosh";
   cout << strlen(name); // to print the size of the string
return 0;
}
```

   
###### string concat
```cpp
#include <cstring>
   
int main(){
   
   char name[5] = "Hosh";
   char lastName[] = "Sharma";
   // we can't do
   name + lastName // this will cause error in older c++
   
   strcat(name, lastName)// contact tow strings
   return 0;
   }
   
```
strcat gona take two argumetn and gona add second argument and add to first argument
the above work, but there is a prablem as name[5] allowed only 5 element, but by compineing we have gone beyond hte boint of this array, so we have written data somewhere in the memory which not spossed to. som ight face some bug in big program. simple solution is make the array bigger like name[50]
   
   
also we cannot set lastName to name like
lastName = name;

##### copy string
```cpp
strcpy(name,lastName);// here name will we updated with the valueof lastName
cout << name;
```
comopare string
as we can't do
   name == lastName
so
```cpp
strcmp(name,lastName); // if name comes first than lastName(alphabetically) then -1, if name comes second after lastName(alphabetically) then it will return 1, if equal then 0
```

#### new string (c++ string) new style string
   
this new string usues the internal char array. but it hase many more imprve ment and easy to work with.
```cpp

   #include <iostream>
   
   using namespace std;
   int main(){
   string name = "hello";
   cout name[0]; // first element of string object
   
   // we can call length method for string length
   cout name.lenght(); // length of string
   
   // we can append to it
   name + " oo"
   // or
   name = name + " oo" // or name += " oo"
   
   // copy string
   string another = name;
   
   // compair
   
   name == another; // or name < another
                                        
  // startswith
   name.starts_with('h') // return true false
  // endswith
   name.ends_with('o') // return true false
                                        
   // empty
   name.empty() // return true if no characters in name
                                        
   // front
   name.front() // return first character                              
   // back
   name.back() // return last character   
                                        
   
   return 0;
   }
```
##### modifying string
                                        
```cpp
string name = "Sharma";

name.append('as'); 
name.insert(0,'df');
name.erase(0,2);   // go to 0 position and delete next 2 characters
name.clear();// which is same like name = "";
name.replace(0,2,"MH"); // go to position 0 and replace next two character with MH

```
##### search in string

```cpp
string name = "Sharma";
name.find('a'); //return the position of first occrance, here it return 2. find is case sensitive
name.find('a',4); // return the position but start from 4th postion, here it return 5. find is case sensitive
name.find('A'); // this will return a very large value, wihic is equilent to -1
size_t t = -1;// by default size_t hold unsigned value, but as here -1 is passed this will underflow
cout << t << endl; // therfore it will print the larges poisble value it can hold

so you can see that t and name.find('A') return the same value

if (name.find('A') == -1)
   cout << "dosn't exist";
   
   
name.rfind('a'); //work like find , but start the search from the end
name.find_first_of(" ,:")// first occarance of any of these characters
name.find_last_of(" ,:")// last occrance of any of these chracters
```
##### extracting sub-string
```cpp
string name = "Satinder shrama"
name.substr(); //  this will retuen a brand new copy of string
name.substr(5); // goto name and extract string from position 5
name.substr(5,3); // goto name and extract string from position 5 and extract 3 str


//example , to get first and last name
string firstName = name.substr(0,name.find(' '));
string lastName = name.subtr(

```
```cpp
string name = "Neil Nitin Mukesh"
// auto index = name.find(' '); // here it is better to use auto , bcz it is returning size_t
auto index = name.rfind(' '); // for middle name 
string firstName = name.substr(0,index);
// string lastName = name.substr(index); // this will return with whiespace at front
string lastName = name.substr(index+1); // to avoid whatspace at front
cout << firstName << lastName;
```
##### working with characters
```cpp
string name = "Neil Nitin Mukesh"
cout << islower(name[0])
cout << isupper(name[0])
cout << isalpha(name[0]) // if a-z A-Z
cout << isdigit(name[0])
cout << isspace(name[0])
cout << toupper('a') // will retunr 65
cout << (char) toupper('a') //c style casting
```


####### customer number shout have 2 alphabet charcters followed by 4 digits
```cpp
book isValid(string customerNumber){
if (customerNumber.length() != 6)
   return false;
for( int i = 0; i <2; i ++)
   if(!isalpha(customerNumber[i])
      reutrn false;
for( int i = 2; i < customerNumeer; i ++)
   if(!!isdigit(customerNumber)
      reutrn false;
return true;
}

int main(){
string customerNumber = "AB234"
cout << isValid(customerNumber);
}

``` 

##### string conversion

```cpp
// const price = "19.90";
double price = stod("19.90"); // you will get output even on 19.x00 19.34x34 19x9.09
cout << price;

string str = to_string(19);
cout << str;
```
##### escape squence
```cpp
string str = "c:\my folder"; // this will not show \
string str = "c:\\my folder"; // this will show \
char = '\''; \\ to print single quatation mark
string str = "'hello'";
string str = "\n\thello";
```
##### raw strings
```cpp
string str = R"("c:folder\folderb\file.txt")"; // this will show exct the same
```

### Structures and Enumerations
---
#### defining structure

in structure we can define custom datatypes

we call this abstract data type or ADT

another common term is abstraction (which means a general model of something)


abstract data type ADT
abstraction: an general model of something

without structure 

```cpp
string title;
int realseYear;
```
with structure
```cpp

// use PascalCase naming convention  
struct Movie{ // this is not alocatin any memory, it just simply telling tht computer that a Movie straction consist these variables
   string title;
   int releaseYear;
};
int main(){
Movie movie; // when this line executed the compiler is gona allocate space for these two vairables. this a movie object
movie.title; // to access the member of the structure
movie.title = "The";
movie.releaseYear = 1987;
cout << movie; // error , as stream insertion operator is implemented only for builtin type of c++;
cout << movie.title; // this will work

return 0;
}


```
#### initializing structure

```cpp
struct Movie{ 
   string title;
   int releaseYear;
};
int main(){
Movie movie = {"The", 243}; // you can initialze like this, also asigning operator is option means
Movie movie {"The", 243}; // also valid. remember order is mendatory
}

```
also initialize in structure
```cpp
struct Movie{  // we can also give it a default value 
   string title; // string is by default is like this  string title = "";
   int releaseYear = 0; // if not inittialized we will get the garbage value. so it is food practice to intialize
   // bool isPopular=false; // no need to set false as by default bool naribale is defined as false
   bool isPopular; // so this is enough
};
int main(){
Movie movie = {"The", 243}; // you can initialze like this, also asigning operator is option means
Movie movie {"The", 243}; // also valid
}
```
#### unpacking structures
to store the structure memeber value in a different valiable
on way is 
```cpp

Movie movie = {"Harry Porter",1929,true}
string title = movie.title
int releaseYear = movie.releaseYear;
bool isPopular = movie.isPopular;

```

but there is a better way, c++ structure binding
```cpp
Movie movie = {"Harry Porter",1929,true}
// c++ structured binding
// js destructring
// python unpacking

auto [title, releaseYear, isPopular] {movie};

cout title;
```
#### array of  structures

we can create an array of structure
in thet

```cpp

struct Movie {
      string title;
      int releaseYear = 0;
      bool isPopular;
};
int main (){
   int numbers[5]; //same like regular array we can create array of structre
   Movie movies[5]; // Movie array
return 0;
}

```

in the statdard library we have a class called vector
which implement a dynamic array
that is the prefered way to store a list of object
with this class we are not gonna allocate too much memeroy , not gonna waset too much memeroy,
the vector class gonna take care of the all the complexity

let's see how gonna use vector and loop over them

```cpp
#include <vector>

int main(){
vector<Movie> movies;   vector<Type of object we gona use> variable_name
Movie movie {"Terminator 1",1929}

movies.push_back(movie); // the at the end of the object
movies.push_back({"Terminator 2",1929}); // or can directly pass at the end of the object
cout << movies[0].title //access first object

   // we can aslo loop over
for(auto m:movies)
   cout << m.title << endl;

      
// much accuratly
for(const auto& m:movies) // now instead of copying the vecor we are using reference variable
   cout << m.title
return 0;
}
```
#### nested structures
```cpp
#include <vector>

struct Date{
   short year = 1900;
   short month = 1;
   short day = 1;
};
struct Movie {
   string title;
   Date releaseDate;
   bool isPopular;
};
int main(){
vector<Movie> movies;
Movie movie {"Terminator 1",1929} // here the 1929 will be assigned to Date.year automatically
cout movie.realseDate.year; // this will print 1929

return 0;
}
```
```cpp
int main(){

Date date {1992,2,1};
Movie movie = {"temp",date};

// or
Movie movie = {"temp",{1992,2,1}}

return 0;
}
```

#### comparing structures
we have to compare each structre elemnet separatly , directyl == won't work
```cpp
Movie movie1 = {"temp",{1992,2,1}}
Movie movie2 = {"temp",{1992,2,1}}
movie1 == movie2; // is not gonna work
movie1.title == movie2.title // this will work for title compare
// or
if(movie1.title == movie2.title && 
movie1.releaseDate.year == movie2.releaseDate.year && 
movie1.releaseDate.month == movie2.releaseDate.month && 
movie1.releaseDate.day == movie2.releaseDate.day
)
   cout << "Equal";

```


#### working with methods
```cpp

struct Date{
   short year = 1900;
   short month = 1;
   short day = 1;
};
struct Movie {
   string title;
   Date releaseDate;
   bool isPopular;
   
   bool equals(Movie movie){
/*        if (title == movie.title && 
         releaseDate.year == movie.releaseDate.year && 
         releaseDate.month == movie.releaseDate.month && 
         releaseDate.day ==  movie.releaseDate.day)
         return true;
         else
            return false; 
      this is a poor way to write , there is a simpler way i.e just siply return
      */
            return (title == movie.title && 
         releaseDate.year == movie.releaseDate.year && 
         releaseDate.month == movie.releaseDate.month && 
         releaseDate.day ==  movie.releaseDate.day)
   }
};

int main(){

Movie movie1 = {"temp",{1992,2,1}}
Movie movie2 = {"temp",{1992,2,1}}

// here again a bit problem the movie2 object is ge copied so to solve this
if (movie1.equals(movie2))
   cout <<  "Equals";
return 0;

}

```

```cpp

struct Date{
   short year = 1900;
   short month = 1;
   short day = 1;
};
struct Movie {
   string title;
   Date releaseDate;
   bool isPopular;
   // this is more accuratly called method, method is a function part of a structure or a class
   bool equals(const Movie& movie){ // movie now this is passed as refenrence, and also the const will not let it be changed over here  which is better solution
            return (title == movie.title && 
         releaseDate.year == movie.releaseDate.year && 
         releaseDate.month == movie.releaseDate.month && 
         releaseDate.day ==  movie.releaseDate.day)
   }
};

int main(){

Movie movie1 = {"temp",{1992,2,1}}
Movie movie2 = {"temp",{1992,2,1}}

if (movie1.equals(movie2))
   cout <<  "Equals";
return 0;

}

```
#### operator overloading
each operator is essentially a function
for example  ==  can be impelemented as operator== 
```cpp
// this not the accurate solution
struct Date{
   short year = 1900;
   short month = 1;
   short day = 1;
};
struct Movie {
   string title;
   Date releaseDate;
   bool isPopular;
   // here to implement == opererato change it to 
   bool operator==(const Movie& movie){ // but here still it thow error because enen though thow we can't change like movie.title, but changes of title is possile
            title = "a"; /// with current implemetentation we can change current structure elemnt values
            return (title == movie.title && 
         releaseDate.year == movie.releaseDate.year && 
         releaseDate.month == movie.releaseDate.month && 
         releaseDate.day ==  movie.releaseDate.day)
   }
};
```
so you should make this method constant
```cpp
// this not the accurate solution
struct Date{
   short year = 1900;
   short month = 1;
   short day = 1;
}
struct Movie {
   string title;
   Date releaseDate;
   bool isPopular;
   // here to implement == opererato change it to 
   bool operator==(const Movie& movie) const{ // now we can't change , now it is a good solution
            return (title == movie.title && 
         releaseDate.year == movie.releaseDate.year && 
         releaseDate.month == movie.releaseDate.month && 
         releaseDate.day ==  movie.releaseDate.day)
   }
}

int main(){

Movie movie1 = {"temp",{1992,2,1}}
Movie movie2 = {"temp",{1992,2,1}}

if (movie1 == movie2) // now we can compare
   cout <<  "Equals";
return 0;

}

```

but still there is an another way


```cpp
// this not the accurate solution
struct Date{
   short year = 1900;
   short month = 1;
   short day = 1;
}
struct Movie {
   string title;
   Date releaseDate;
   bool isPopular;

}


bool operator==(const Movie& first,const Movie& second) const{
         return (first.title == second.title && 
      first.releaseDate.year == second.releaseDate.year && 
      first.releaseDate.month == second.releaseDate.month && 
      first.releaseDate.day ==  second.releaseDate.day)
}

// 

int main(){

Movie movie1 = {"temp",{1992,2,1}}
Movie movie2 = {"temp",{1992,2,1}}

if (movie1 == movie2) // now we can compare
   cout <<  "Equals";
return 0;

}
```

why the above approache , because the some operators like << (stream insertion operators)  are required to implement outside the structure

so having it outsideis a good approach


```cpp
// this not the accurate solution
struct Date{
   short year = 1900;
   short month = 1;
   short day = 1;
}
struct Movie {
   string title;
   Date releaseDate;
   bool isPopular;

}


bool operator==(const Movie& first,const Movie& second) const{
         return (first.title == second.title && 
      first.releaseDate.year == second.releaseDate.year && 
      first.releaseDate.month == second.releaseDate.month && 
      first.releaseDate.day ==  second.releaseDate.day)
}

// overqrite <<. here ostream means output stream, ostream& means ostream reference
ostream& operator<<(ostream& stream, const Movie& movie){
   stream << movie.title;
   return stream; // always return stream object, so that we can chain the stream insertion opeerator
}

int main(){

Movie movie1 = {"temp",{1992,2,1}}
Movie movie2 = {"temp",{1992,2,1}}

if (movie1 == movie2) // now we can compare
   cout <<  "Equals";
   
 // now we can do like
 cout << movie1;
return 0;

}
```

#### Structures and functions
we need the following function for next topic
```cpp
struct Date{
   short year = 1900;
   short month = 1;
   short day = 1;
}
struct Movie {
   string title;
   Date releaseDate;
   bool isPopular;

}
Movie getMovie(){
return {"new",1998}
}
void showMovie(Movie& movie){
cout << movie.title;
}

int main(){
auto movie = getMovie();
showMovie(movie)

return 0;
}
```
#### pointer to structure
instead of  passign as reference pass as pointer like this
```cpp

void showMovie(Movie* movie){ // change to movie pointer
cout << movie.title; // but you will get error on this as movie is just a memery address , so it has nothing like .titile
}
```
to soleve this first we have to derefrence movie. but again this cause problem as the perriority is high for . so movie.title will execute first istead of *movie
```cpp

void showMovie(Movie* movie){ // change to movie pointer
cout << *movie.title;// again this will not work due to priority order 
}
```
so to solve this wrap this in the (), but you see the code look silghly more complex

```cpp

void showMovie(Movie* movie){ // change to movie pointer
cout << (*movie).title;// now the *move runs first by the compiler
}
int main(){
auto movie = getMovie();
showMovie(&movie); //also herewe have to pass the address of the movie object

return 0;
}

```

we can replaceit with structure pointer operator ->
```cpp

void showMovie(Movie* movie){ // change to movie pointer
cout << movie->title;// this gonna dereference the pointer and gona give the access to title 
}
int main(){
auto movie = getMovie();
showMovie(&movie); //also herewe have to pass the address of the movie object

return 0;
}

```

### Enumerations

```cpp
enum Action { // enum automatically assign a value the to the element like 0 for List , 1 for Add and so on
List,
Add,
Update,
};
// but we can assign a value explicitly
enum Action { 
List=1,
Add=2,
Update=3,
};

// if you do like below the Add , gona be 2 , Update gona be 3 and os on
enum Action { // enum automatically assign a value the to the element like 2 for Add and so on
List=1,
Add,
Update,
};

```
just define one , other iwll be decided, and access usin :: list

```cpp
enum Action { 
List=1,
Add,
Update,
};


int main(){
int intput;
cin >> input;

if (input == Action::List){
   cout << "execute List"
   
   
return 0;
}

```
#### strongly typed Enumerations

we cannot define two enum with same elements like
```cpp
enum Action { 
List=1,
Add,
Update,
};


enum Operation { 
List=1,
Add,
Update,
};

```
so in c++ 11 we have stroly typed Enum
but we have to cast it in comparision as this dosn't eplicitly return int
```cpp
enum class Action { // we should alway use stronly typed enum to avoid name collision
List=1,
Add,
Update,
};


enum class Operation { 
List=1,
Add,
Update,
};



int main(){
int intput;
cin >> input;

if (input == static_cast<int>(Action::List)){
   cout << "execute List"
   
   
return 0;
}

```

### stream


stream  


##### reading from stream
all the cin has the buffer. buffer is like temprary storage memeroy
so what the user enterfirst go to the buffer like

```cpp
   
   // so what the user enterfirst go to the buffer like
   // [10 20]
int main(){
cout << "First ";
int first;
cin >> first;/// if you enter here like 10 20, then what happen is that, so this gonna read all the cracter until hit space [10 , so it will extract 10 and convert it to int


// now our buffer is gona look like this [ 20]

cout << "Second ";
int second;
cin >> second; // but wehn we get to this line ,as we have leftover in buffer the program is not gona wait for the user to enter a value and get the 20 and stre it in second 
cout << "You entered " << first << " and " << second;


return 0;
}
```

all the input stream has the method to clear the buffer


```cpp
   
   // so what the user enterfirst go to the buffer like
   // [10 20]
int main(){
cout << "First ";
int first;
cin >> first;
// ignore next 10 character until you find \n
cin.ignore(10,'\n') number of character to ignore , and the chracter we are looking for , which is when user press enter. so after 10 chareacter untill you find \n



cout << "Second ";
int second;
cin >> second; 
cout << "You entered " << first << " and " << second;


return 0;
}
```
how to cler all the reain character in the buffer we should pass the largest value can represent using using the stream size

```cpp
numeric_limits<streamsize>::max()
cin.ignore(numeric_limits<streamsize>::max(),'\n')
```
##### handling input errors
if user enter invalid value then stream goes in to fail state, we can detect tht using cin.fail()
we can handel that iwht cin.fail()
```cpp

int main(){
cout << "First: ";
int first;
cin >> first; // ausme we enter a 20 here
if(cin.fail()){
cout << "enter a valid number bhaya";
cin.ignore(numeric_limits<streamsize>::max(),'\n')
```

we can handle this with an infinie loop and wait for user to enter valid value
```cpp

int main(){
   int first;
while (true){
   cout << "First: ";

   cin >> first; // asume we enter a 20 here
   if(cin.fail()){ // even after fail there is value in the buffer , due to [a 20]
   cout << "enter a valid number bhaya";
      cin.clear();// clear the fail state, means put the stream in good state
      cin.ignore(numeric_limits<streamsize>::max(),'\n') // and clear the buffer // the [a 20]
   }
   else break;
   

}
```

we can handle this with an infinie loop and wait for user to enter valid value with a function
```cpp

int getNumber(const string& prompt){
   int number;
   while (true){
      cout << "First: ";
   
      cin >> first;
      if(cin.fail()){ // even after fail there is value in the buffer 
         cout << "enter a valid number bhaya";
         cin.clear();// put the stream in good state
         cin.ignore(numeric_limits<streamsize>::max(),'\n') // adn clear the buffer
      }
      else break;
      
   
   }
   return number
}
int main(){
   int first = getNumber("First: ");
   int second = getNumber("Second: ");
   cout << "You entered " << first << " and " << second;
   return 0;
}
```
all stream classes same the interface. 
#### FILE STREAM CLASSES:
=========================

ifstream (input file stream) . we can use to read data from a file
ofstream (output file stream). we can use to write date from a file
fstream () combine the above tow classes functionality. means we can use it for read and write data to a file

##### write to a text file;

```cpp
#include <iostream>
#include <fstream> // this include both ifstream and ofstream
#include <iomanip> // io manipulator
using namespace std;
int main(){
   ofstream file;
   file.open("data.txt"); // if file doesn't exist it gonna created, otherwise its data gonna overwritten
   if (file.is_open()){
      file << "Hello World" << endl;// this will work , but if want more manipulation we can use it wit <iomanip>, like following
      file << setw(20) << "Hello" << setw(20) << "World"  << endl; // setw is allocate 20 character for each word, so that they every like each column
      file.close(); //always call close so the operating system resources to work with file get released, if won't do so, the fiel may not be acceable to other programs
   }
   return 0;
}
```
##### write a csv

diffrence between \n and endl, is that endl aways flushes the buffer, but if we use \n buffer gonna flush only once

```cpp
#include <iostream>
#include <fstream>
using namespace std;
int main(){
   ofstream file;
   file.open("data.csv");
   if (file.is_open()){
      file << "id,title,year\n"
           << "1,Terminator 1,1984\n"
           << "2,Terminator 2,1991\n";
      file.close();
   }
   return 0;
}
```


##### read from a text file;

```cpp
#include <iostream>
#include <fstream> // this include both ifstream and ofstream
#include <iomanip> // io manipulator
using namespace std;
int main(){
   ifstream file;
   file.open("data.txt"); // if file doesn't exist it gonna created, otherwise its data gonna overwritten
   if (file.is_open()){
      string str;
      file >> str; // it will aisgn until it find a diliminator, like \n white space tab
      cout << str; 
      file.close(); 
   }
   return 0;
}
```

so to get all use getline

```cpp
#include <iostream>
#include <fstream> // this include both ifstream and ofstream
#include <iomanip> // io manipulator
using namespace std;
int main(){
   ifstream file;
   file.open("data.txt"); // if file doesn't exist it gonna created, otherwise its data gonna overwritten
   if (file.is_open()){
      string str;
      getline(file, str); // it read all the character until it find \n
      cout << str; 
      file.close(); 
   }
   return 0;
}
```

we have file.eof() . this return true if we are at end of file


```cpp
int main(){
   ifstream file;
   file.open("data.txt"); // if file doesn't exist it gonna created, otherwise its data gonna overwritten
   if (file.is_open()){
      string str;
      getline(file, str); // it read all the character until it find \n
      while(!file.eof()){
      getline(file, str); // this will get each line
      cout << str << endl;
      }
      file.close(); 
   }
   return 0;
}
```


get and save in Movie structure
getine has third parameter which is deleminator
the below code will fail
```cpp

struct Movie{
   int id;
   string title;
   int year;
}


int main(){
   ifstream file;
   file.open("data.txt"); // if file doesn't exist it gonna created, otherwise its data gonna overwritten
   if (file.is_open()){
      string str;
      getline(file, str); // it read all the character until it find \n
      while(!file.eof()){ // run untill it is end of file
      getline(file, str,','); // getline(file, str,'\n') is by default
      Movie movie;
      movie.id = stoi(str);
      cout << str << endl;

      getline(file,str,',');
      movie.title = str;

      getline(file, str); // as we have \n not , 
      movie.year = stoi(str);
      }
      file.close(); 
   }
   return 0;
}
```

the file has a empty line at the end so to handle it write like this

```cpp

struct Movie{
   int id;
   string title;
   int year;
}


int main(){
   ifstream file;
   file.open("data.txt"); // if file doesn't exist it gonna created, otherwise its data gonna overwritten
   if (file.is_open()){
      string str;
      getline(file, str); // it read all the character until it find \n
      while(!file.eof()){ // run untill it is end of file
      getline(file, str,','); // getline(file, str,'\n') is by default
      if(str.empty()) continue;
      Movie movie;
      movie.id = stoi(str);
      cout << str << endl;

      getline(file,str,',');
      movie.title = str;

      getline(file, str); // as we have \n not , 
      movie.year = stoi(str);
      }
      file.close(); 
   }
   return 0;
}
```

we can also store data in binary(images, audio files, pdf), it not human readable , because data store in them are exaclty like stored in memory

```cpp
#include <iostream>
#include <fstream>

using namespace std;

int main(){
   int numbers[] = {1'000'000, 2'000'000, 3'000'000};
   ofstream file("numbers.txt");
   if (file.is_open()){
      for (auto number:numbers)
         file << number << endl;
      file.close();
}
```

if you check its size `ls -lh numbers.txt` it will have 24 bytes
```
1000000  // 7 character + one \n which makes to 8 bytes so in total 24 bytes
2000000
3000000
```

now we are goning to store it in binary to compare sizes
file.write() // requuire two parameter 1. character pointer, 2. no of bytes we want to read from the memory and write to the disk 

```cpp
#include <iostream>
#include <fstream>

using namespace std;

int main(){
   int numbers[] = {1'000'000, 2'000'000, 3'000'000};
   ofstream file("numbers.dat", ios::binary); // bin or dat and the mode of the file
   if (file.is_open()){
      file.write(reinterpret_cast<char*>(&numbers), sizeof(numbers));
      file.close();
      return 0;
}
```

if you check its size `ls -lh numbers.*` it will have 24 bytes for normal but 12 bytes for bin file

as in this machine each integer store 4 bytes of memory. so for 3 integer has the size of 12 bytes

##### reading binary files


```cpp
#include <iostream>
#include <fstream>

using namespace std;

int main(){
      int numbers[3];
      ifstream file("numbers.dat", ios::binary);
      if(file.is_open()){
         file.read(reinterpret_cast<char*>(&numbers), sizeof(numbers));
         // loop over numbers to see them
         cout << numbers << endl;
         file.close();
      }
      return 0;
}
```
here whiout knowing the numbers of file line

```cpp
#include <iostream>
#include <fstream>

using namespace std;

int main(){
      ifstream file("numbers.dat", ios::binary);
      if(file.is_open()){
         int number
         file.read(reinterpret_cast<char*>(&number), sizeof(number));
         // loop over numbers to see them
         cout << number << endl; // thiswill print the first
         file.close();
      }
      return 0;
}
```

put in a loop
```cpp
int main(){
      ifstream file("numbers.dat", ios::binary);
      if(file.is_open()){
         int number
         while(file.read(reinterpret_cast<char*>(&number), sizeof(number)))
            cout << number << endl;
         file.close();
      }
      return 0;
}
```

working with file streams


```cpp
#include <iostream>
#include <fstream>

using namespace std;

int main(){
      fstream file("numbers.txt", ios::in | ios::out); // opening file for both writing and reading. if not fiel then created otherwise content is overwriten
      // but if you want to append then
      fstream file("numbers.txt", ios::in | ios::out | int::app);
      // also to open in binary mode
      fstream file("numbers.txt", ios::in | ios::out | int::app  | int::binary);
      if(file.is_open()){
         // do whatever with file
         file.close();
      }
      return 0;
}
```


string stream

string stream classes

istringstream(for reading a string stream)
ostringstream(for writing a string stream)
stringstream(for reading and writing a string stream)

```cpp
#include <iostream>
using namespace std;
int main(){
      double number = 12.34;
      string str = to_string(number);
   cout << str;// this will print 12.340000 , but if you wat to realy control this then you have to use string stream
      return 0;
}
```

this will give full control over how we get the number to the string
```cpp
#include <iostream>
#include <sstream>
#include <iomanip>

using namespace std;
int main(){
      double number = 12.34;
   stringstream stream;
   stream << fixed << setprecision(2) << number; //fixed noation to see decimal points, 
   string str = stream.str(); // to getting the underline string
   cout << str;// this will print 12.34
      return 0;
}
```

parsing string

```cpp
#include <iostream>
#include <sstream>
#include <iomanip>

using namespace std;
int main(){
   string str = "10 20";
   stringstream stream; // of istringstream stream;
   stream.str(str); // to getting the underline string
   int first;
   stream >> first;// it will get hte value until find a whie space 

   int second;
   stream >> second;
   cout << first + second;
      return 0;
}
```



