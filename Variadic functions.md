### [Variadic functions](https://en.cppreference.com/w/c/variadic) 
- These functions are the ones which can accept variable number of arguments.Only prototyped function declarations may be variadic. This is indicated by the parameter of the form `...` which must appear last in the parameter list and must follow at least one named parameter.

#### Type
##### [va_list](https://en.cppreference.com/w/c/variadic/va_list)
- holds the information needed by va_start, va_arg, va_end, and va_copy
```cpp
/* unspecified */ va_list;
```

#### Macros

##### [va_start](https://en.cppreference.com/w/c/variadic/va_start)
- enables access to variadic function arguments.
```cpp
void va_start( va_list ap, parmN );

void va_start( va_list ap, ... );
```
- Parameters
	- ap - an instance of the va_list type
	- parmN	- the named parameter preceding the first variable parameter
- Expanded value
	- (none)

##### [va_arg](https://en.cppreference.com/w/c/variadic/va_arg)
- accesses the next variadic function argument
```cpp
T va_arg( va_list ap, T );
```
- Parameters
	- ap - an instance of the va_list type
	- T - the type of the next parameter in ap
- Expanded value
	- the next variable parameter in ap

##### [va_copy](https://en.cppreference.com/w/c/variadic/va_copy)
- makes a copy of the variadic function arguments.
```cpp
void va_copy( va_list dest, va_list src );
```
- Parameters
	- dest - an instance of the va_list type to initialize
	- src - the source va_list that will be used to initialize dest
- Expanded value
	- (none)

##### [va_end](https://en.cppreference.com/w/c/variadic/va_end)
- ends traversal of the variadic function arguments.
```cpp
 void va_end( va_list ap );
```
- Parameters
	- ap - an instance of the va_list type to clean up
- Expanded value
	- (none)

##### Example : 
```cpp
#include <cstdarg>
#include <iostream>
 
using namespace std;
 
// this function will take the number of values to average
// followed by all of the numbers to average
double average ( int num, ... )
{
  va_list arguments;                     // A place to store the list of arguments
  double sum = 0;
 
  va_start ( arguments, num );           // Initializing arguments to store all values after num
  for ( int x = 0; x < num; x++ )        // Loop until all numbers are added
    sum += va_arg ( arguments, double ); // Adds the next value in argument list to sum.
  va_end ( arguments );                  // Cleans up the list
 
  return sum / num;                      // Returns the average
}
int main()
{
    // this computes the average of 13.2, 22.3 and 4.5 (3 indicates the number of values to average)
  cout<< average ( 3, 12.2, 22.3, 4.5 ) <<endl;
    // here it computes the average of the 5 values 3.3, 2.2, 1.1, 5.5 and 3.3
  cout<< average ( 5, 3.3, 2.2, 1.1, 5.5, 3.3 ) <<endl;
}
```
