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
 
 size_t = unsigned int
 size_t =  unsigned long long
 
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
#### contanct pointer
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

below assum that the pointer address is 100(actully it is hexa decimal, but for sipllicity we are takeing decimal), so when we do ptr++ it will become 104,
because on most of the machine int take 4 bytes so the first element in the array takes from 100 - 103 (4 byte space)
so on ptr++ it gona increate like sizeof(data)  size of data type
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


{10,20,30} create a pointer and print in reverse
```cpp
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
Unique pointers
Shared pointers



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

using make_unique<>

```cpp
#include <memory>

// make_unique<int> // to create interger pointer , this return an instance of unique_ptr class , so we can write it as
unique_ptr<int> y = make_unique<int>;
// as above we can see th that it gona return unique pointer of int , then we can eaily use auto keyword, so we are letting the compiler infer the type of 
auto y = make_unique<int>;

```
we are not limited to only int , we can create any datatype , for eg

```cpp
#include <memory>
auto numners = make_unique<int[]>(10); // int array wit intitial size of 10
numbers[0] = 10;
cout << numbers[0];
```

##### shared pointer










