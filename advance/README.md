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

  second = first; // this will also not work, we can;t directly compy array in c


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

