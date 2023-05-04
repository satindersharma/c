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

// even the size funtion will not work as it hase interger point er whicui is an memory address number, so function size to int

void printNumbers(int numbers[]){
   for (int i = 0; i <size (numbers); i++)
      cout << numbers[i];



