#structure #union 
## STRUCTURES
![[Pasted image 20251007162337.png]]

Out defined structure
`struct Point { 
	`int x=0; 
	`int y=0;
	`int sum(){`
		`return x+y;`
	}`
}`

### 1. structure variable and init members
**Variable**
`struct_name var_name`

**Initialize structure members**
 `struct Point p1 = {0,1};`

### 2. Access and Modify members
Structure members are accessed using dot operator and a new value can also be assigned using assignment operator.
`p1.x = 5;`

### 3.Member Functions
In C struct, functions are not allowed inside the structure but in C++ we can declare the function inside the structure. They are called **member functions** while the variables are called **data members**
It also supports: **constructor; destructor; access specifiers(private,public)**

### 4. size of structure
The size of a structure is determined by the sum of the sizes of its individual members, with additional padding added by the compiler to ensure proper memory alignment.

`#include <iostream>
`using namespace std;
`struct GfG
`{
 `   char c;
  `  int x, y;
`};

`int main()
`{
 `   // Finding the size
  `  cout << sizeof(GfG);
`   return 0;
`}`
we have **sizeof(char)+2sizeof(int)=8** but we got 12 bytes because of **structure paddings**.
###  5. typedef
typedef is used to create alias for variable and structures (so we don't have to call struct Point)
`typedef struct Point{int x=0;int y=0} Point;`

### 6. Pointer to structure
We can use pointer to point to a structure. We access its data members or function members by using **arrow operator (->)** 

### 7. Self-referential Structures
Self-referential structures are those structures that contains the pointer to the same type as a member
`struct dat{int val; dat* next};`
**NOTE:** a structure can only contain pointer to the same type but not variable to them same type. It is because it is impossible to derive the size information in the structure before complete definition

### 8. Structure with Function
Structures work similarly like other variables with functions. We can pass a structure to a function or return structure from a function. The recommended approach is to pass a structure by reference, as making a copy of structure is costly operation

### 9. C++ Bit Fields
When we declare the members in a struct and classes, a pre-determined size is allocated for the member variables. In C++ we can compress that allocated size using bit fields

`struct StructName{`
	`dataType fieldName: width;`
`};`

`class ClassName{`
`public:`
	`dataType fieldName: width;`
`};`
**NOTE** : the number for bit fields can be larger than the default size of that datatype we specified; we cannot create pointer point to bit fields because they might start at a byte boundary;

**APPLICATION**
- it is used for **memory optimization**
- design hardware registers that have specific bit structure