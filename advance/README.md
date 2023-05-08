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
