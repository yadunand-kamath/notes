
#cpp 

## Contents:



---
## 1. Introduction

- compiled, general purpose language, object-oriented
- Standard Template Library (STL) - contains all basic tools
- Features of Modern C++:
	- smart pointers
	- automatic type inference
	- move semantics
	- threading
	- lambda functions 

---
## 2. C++ Building Process <a name="2"></a>

1. **Preprocessing** 
	- Preprocessor is a tool that processes the program before it is compiled.
	- Preprocessor directives are instructions to the preprocessor.
	- Such statements start with #.

2. **Compilation** 
	- Code is checked for correct syntax.
	- Source code in high level language (`.cpp`) is converted to object code (`.obj`) in machine level language.

3. **Linking** 
	- Individual object codes are linked with standard libraries and each other to create a binary executable file (`.exe`).

### 2.1 C++ using GCC

#### MinGW (*Minimalist GNU for Windows*)

1. `g++ -o filename filname.cpp`: compile the program 
2. `filename.exe`: execute the program

- `g++ -o filename filename.cpp & filename.exe`: shortcut to compile and execute 

#### Linux

1. `gcc -o filename filename.cpp`: compile the program
2. `./filename`: execute the program

---
## C++ Program Components

### Stream I/O

* `<<` sends something to a stream
* `>>` reads something from a stream
* `cout` (console output)
* `cin` (console input): stops reading from console when it encounters a white space.
	- `cin.getline(var,no. of char, delimiter)`: reads with white space until delimiter is encountered.

### Data Types

- The type of value that the variable stores.
#### Fundamental Types
1. Integers - ***short*** {2 bytes}, ***long*** {4 bytes}, ***int*** {4 bytes}
2. Real Numbers - ***float*** {4 bytes}, ***double*** {8 bytes}
3. Characters - ***char*** (-128 to 127) {1 byte}, ***wchar_t*** (1 wide character) {2 bytes}, ***unsigned char*** (0 to 255)
4. Boolean - ***bool*** {1 byte}
5. Auto (*C++11 Automatic Type Inference*): compiler deduces the type.
	- `auto <identifier> = <initializer>;` 
6. Strings - ***string***, ***wstring*** (used for Unicode)
	- *C++11 Raw String Literals*: ignores escape sequences. 
	- `string = r"()";` 
#### User Defined Types
7. Classes and Objects
	- Objects are real-world entities.
	- Classes are blueprints that define the object's attributes and methods.
8. Structures - ***struct***
	- plain old data 
	- default access is public
	- used to implement function objects
	- better to use struct to hold data and class when business logic is involved	
9. Enumerations: `enum EnumName {enumValue1, enumValue2};`
	- creates a restricted range of values called symbolic constants/enumerators
	- internally represented as undefined integral types
	- can implicitly convert to an integer, but not the other way round 
	- default value starts from 0, but users can assign any value 
	- Scoped Enum: `enum class EnumName { values... } ;`
		- prevents clashing of enum values 
		- `EnumName::value`
10. Unions - represents all members in the same memory
	- *Disadvantages*:
		+ no way to know which type it holds 
		+ cannot assign objects of user-defined types directly to union member 
		+ user-defined types are not destroyed implicitly
		+ cannot have base class
		+ cannot derive from a union 

- Modifiers - ***signed, unsigned, long, short*** 

#### Qualifiers
1. ***const***: `const <type> <variable> {initializer} ;`
	- creates a constant variable whose value cannot be modified
	- qualified to a declaration but always requires initializer
	- const variables can only be pointed by const pointers
2. ***volatile*** - prevents compiler optimizations
3. ***static*** - controls scope and lifetime of variables

### Namespaces 

- Libraries are placed here to prevent conflicts if other libraries use same names.
- Classes and functions are grouped together using namespace.

### Scope Resolution (::)

* Used between *namespace* and *class*.
* Used between *namespace* and *functions*.
* Used between *class* and *member functions*.

### Functions

* Blocks of reusable code which needs to be called in order to be used.
* Makes the program modular.
* Accepts values through parameters.
* Can return values.

`<return type> <name> (<parameter list>) { <body> }`

1. **Function Declaration/Prototype/Signature** - Notifies the compiler how the function should be called. It has no implementation.

2. **Function Definition** - Includes function body with code implementation.

* ***Member Functions*** - defined in classes	
* ***Free/non-member functions*** - do not belong to any class

* **Function Overloading**
	- same function name 
	- different number of parameters
	- different types of parameters 
	- return type is ignored 
	- resolved at compile-time (***Static Polymorphism***)
	- **Name Mangling** - compiler generates unique names for functions with same name in order to distinguish them.

* Default Function Arguments
	- Allows some or all function arguments to have default values.
	- Makes it optional to pass arguments to that function.
	- Just initialize the argument with the default values during function definition.

* Inline Functions
	- Marked with `inline` keyword.
	- Requests compiler to replace function call with function body. 
	- Should be defined in a header file if multiple sources have to use it. 
	- Function call overhead is avoided.
	- May not work for functions that are- large, recursive, too many conditional statements.

* Extern C 
	- C does not support function overloading.
	- extern C directive can be applied on one of the overloaded functions to suppress name mangling.
	- This allows C++ functions to be called from C.

### l-value and r-value

* ***l-value*** (locator-value)
	- Refers to memory location which identifies an object.
	- Represented as *identifier* (all variables are l-values).
	- It has a name and can be assigned values.
	- It persists beyond the expression.
	- Functions that return by reference return l-value
	- l-value reference always binds to l-values.
* ***r-value***
	- Refers to a temporary data value that is stored at some address in memory.
	- Can’t have a value assigned to it, because it is the value.
	- No name and does not persist beyond the expression.
	- Functions that return by value return r-value.	
	- r-value reference represents a temporary value. It always binds to temporaries. It's created with `&&` operator.
```C++
int x = 10;
int& lref1 = x; //lvalue ref to lvalue
const int& lref2 = 20; // lvalue ref to rvalue
int&& rref = 5; // rvalue ref to rvalue
```

- `std::move()`: converts lvalue to rvalue.
### Pointers

* Points to another type and holds memory address of the variable.
- Used to indirectly access other variables.
* Initialization is optional.
* Initializer need not be l-value.
* Declared with Dereference (`*`) operator - used for indirect access of variables
* Address Of Operator (`&`): `&variable` - returns the address of the variable.
	- `type *pointerVariable = &typeVariable;`
- `void` type can be used to point to any type of variable.
- `(*pointerVariable).function()` or `pointerVariable->function()`

### Function Pointers

- Pointer that holds address of function.
- Pointer type is same as function signature
- Can be used to indirectly invoke function without function name.
- `<return type> (*fnptr) (args) = &Function ;`
- Calling the function: `(*fnptr)(parameters)` or `fnptr(parameters)`

### Reference Type

* Alias for a previously defined variable. It needs to be initialized during declaration.
* Created with (`&`) operator during declaration.
* Always needs an initializer called *referent* which should be a variable (l-value).
* Always bound to its referent, cannot be reassigned.
* Can be used to indirectly modify referent (just like a pointer) without using dereference operator.
* No storage required, so has the same address as that of referent.
* Variable name and reference are basically identifiers for the same memory.
* Reference can never be null but pointer can.	

### Reference v/s Pointers

- Unlike a pointer, a reference is not a variable, just a name/alias.
- Pointer variable requires storage, but reference does not.
- Reference cannot be NULL but pointers can.

- ==Use Pass-By-Reference over Pass-By-Pointers== because:
	   - References are safer as they don't deal with memory addresses.
	   - References cannot be NULL.
	   - Easier to use without dereference operators.
	   - References clarify ownership of memory. With pointers, there is a confusion about whether the memory needs to be freed at the end of the function. But not with references.

---
## Memory Management

### Memory Lifecycle

1. New memory is allocated.
2. Allocated memory is used.
3. Allocated memory is released	(will lead to memory leaks if not released properly).

### Memory Areas

- All memory is taken from the ***process address space***.

1. **Stack**
	- fast allocations
	- limited space
	- allocated automatically for local variables 

2. **Data Section** - allocated for global and static data.

3. **Heap** (Free Store)
	- slower allocations 
	- larger memory
	- allocated at run time 
	- for longer lived variables 
	- dynamic memory allocation operators:
	- `new`: `<type> *<variable> = new <type> (optional args) ;` 
		- allocates memory on the heap
		- can initialize memory
		- can call constructors
		- can be customized through overloading 
		- needs to be released using delete 
	- `delete`:  `delete <variable> ;`
		- deallocates memory 

### Manual Memory Management

- ***Rule of 5*** - if a class has ownership semantics, then user must provide user defined:
	1. Destructor
	2. Copy Constructor
	3. Copy Assignment Operator
	4. Move Constructor
	5. Move Assignment Operator

- ***Rule of 0*** - if a class has no ownership semantics, then user should not provide anything.

### Copy and Move Semantics

* Copy semantics:
	- obj1 has a value and a pointer pointing to some memory with some value 
	- if we perform deep copy to obj2, 
		1) value gets copied to obj2 
		2) new memory is allocated 
		3) value is moved to the new memory and pointer points to this new memory 

* Move Semantics:
	- obj1 has a value and a pointer pointing to some memory with some value
	- if we perform shallow copy to obj2, the obj2 pointer points to same memory that obj1 is pointing to
	- if any of the objects get destroyed, the other object will be left with a dangling pointer 
	- to avoid this, the pointer of object that needs to be destroyed is pointed to null
	- faster than deep copy 
	- can be used to copy temporaries between objects 
	- temporary can be detected by making copy constructor accept r-value reference 
	- Move Constructor 

### Standard Library Smart Pointers

* Raw Pointers must be manually released. When dynamically allocated memory is freed more than once, it can cause memory corruption, and when dynamically allocated memory is not freed, it can cause memory leaks.
* Smart Pointers are automatically deleted.
* In modern C++, there should be no explicit calls to new and delete.
- Header: `<memory>`
- Resource Manager - automatically releases owned resource when Resource Manager object goes out of scope.

1. `make_unique<>()`: smart pointer that automatically deletes allocated memory.
2. `std::unique_ptr <type> var`: Movable Non-copyable 
	- `destination = std::move(src)`
3. `std::shared_ptr <type> var`: Reference counted 
	- `var.use_count()`: returns count
4. `std::weak_ptr <type> weak_ptr = shared_ptr`
	- Peek at shared pointer without bumping the reference count.
	- Always initialized with `shared_ptr`. 

---

## Modern C++ Features

### C++11 Uniform Initialization

* C++98 provided following ways to initialize types:
	- Scalar types:- `=` or `()`	
		1. ***Copy Initialization***: `datatype variable = value;`
		2. ***Direct Initialization***: `datatype variable(value);`
	- Array types:- `{}` 
		- ***Aggregate Initialization***: `datatype variable[size] = {value1, value2, ...};`
		
* From C++11, curly brackets {} can be used to initialize all types.
- Prefer initialization over assignment.
* *Advantages*:
	- Uniform syntax.
	- It forces initialization.
	- It prevents narrowing conversions.

- ***No Initialization***: `datatype variable;`
- ***Zero/Default Initialization***: `datatype variable{};`
- ***Direct Initialization***: `datatype variable{value};`

### C++11 `std::initializer_list`

* Lightweight proxy object that represents an array of objects.
* Constructed automatically from a braced list of elements.
* Provides access to its elements through iterators.

### C++14 Digit Separator

* Used to improve readability of numbers.
* *APOSTROPHE* (U+0027): `'`
* *Example*: `long x = 10'000'000;`

### C++17 Nested Namespaces

- `namespace n1::n2::n3 { }`	

### User-defined Literals

* Literal is a fixed value that appears directly in the code.
* Literals can be modified through prefixes and suffixes.
* In C++11, users can define their own suffixes.
- `<return type> operator"" _<literal> (<arguments>)`
	- `operator""`: defines a literal operator function.
	- `_<literal>`: always starts with underscore followed by name.
- Literal functions can only be global functions.

### C++14 Binary Literal

* Can store binary values.
* *Usage*: `0b` (or) `0B` followed by binary value 		
* *Example*: `auto x = 0b0010011010;`

### C++14 Automatic Return Type Deduction

* Compiler can automatically deduce return type for a function 

```C++
auto function(parameters...) {
	return result;
}
```

### C++17 Variable Declarations

* Local variables can be declared inside if statement.
* for loops can have same loop iteration variable name.
 
### C++17 Structured Bindings
	
* single-statement multiple-variable declarations
* from pair/tuple/struct

### C++11 `constexpr`

* Represents an expression that is constant.
* It can be applied to *variable declarations* and *functions*.
* Evaluated at compile-time.
* All `constexpr` variables are `const` but not the other way round.
* `const` keyword is used to indicate value cannot be modified, but `constexpr` is used to evaluate expressions at compile-time.

### C++17 `if constexpr`

-  `if constexpr(condition) {}`: condition is evaluated at compile-time

### C++11 Null Pointers

- Pre-C++11, `NULL` macro was used.
- `nullptr`
	- Points to nothing.
	- Type safe. 
	- Throws Read/Write Access Violation on trying to access a variable.

### C++14 Relaxed `constexpr` Functions

* Compile-time computations improve run-time execution speed.
* Ordinary functions are executed at run-time.
* `constexpr` functions are executed at compile-time.
- `constexpr returntype function() {}`

### Chrono Library

* Header: `<chrono>`
* Provides literal suffix for unit of measurement.
* ***Time Duration Classes*** - automatic unit conversions
	- hours (h)
	- minutes (min)
	- seconds (s)
	- milliseconds (ms)
	- microseconds (us)
	- nanoseconds (ns)

### C++11 Lambdas

* Unnamed anonymous functions.
* Syntactic shortcut for a function object.
* Replaces function objects.

```C++
[](parameter list) {
	body
}
```

* `[]` is called Lambda Introducer - contains Capture List.

### C++14 `[[deprecated]]` Attribute

* Used to mark entities as deprecated.
* Compiler gives warning while trying to use these entities.

```C++
[[deprecated("custom message")]]
void someFunction() {}
```

### Warning Levels

* Default warning levels are too tolerant.
* Warning levels can be changed.
*  On Command Line:
	- `-Wall`
	- `-Wextra`
	- `-Wpedantic`
	- Treat warning as errors: `-Werror`


---
## Templates

* powerful way to write a library
* reusable component that works on any type without giving up type safety
* resolved at compile time
* template only acts as blueprint
* template instantiation occurs at compile-time only after template argument deduction

### Standard Template Library (STL)

- Provides fast and reusable containers and algorithms.
- Core components: *container classes, algorithms, iterators*. 
- Container classes represent data, and algorithms represent operations on data.

#### Container Types

##### Sequential Containers:
- stores elements in a linear sequence
1. **array**
	+ thin wrapper over C-style static arrays 
	+ supports iterators
	+ provides random access 
	+ cannot grow 
2. **vector** 
	+ dynamic array
	+ grows automatically
	+ efficient for insertion/removal at the end 
	+ provides random access
3. **list** 
	+ implemented as a 2-way linked list 
	+ efficient for insertion/deletion anywhere
	+ does not provide random access
4. **deque**
	+ efficient for addition/removal at both ends
	+ not good for insertion and removal 
	+ grows automatically
	+ provides random access

##### Associative Containers:
1. **set/multiset** (type, comparator, allocator)
	+ implemented as binary tree
	+ elements are stored in sorted order 
	+ fast search
	+ no random access 
	+ elements cannot be modified directly
2. **map/multimap**
	+ implemented as binary tree 
	+ stores key-value pairs
	+ elements stored in sorted order based on key
	+ fast search
	+ no random access
	+ keys cannot be modified directly

##### Derived Containers:
1. **stack**
2. **queue**
3. **priority_queue**

##### Unordered Containers:
- Implemented as hash tables.
- Values are hashed and stored in undefined order.
- Iterators are constants. 
1. `unordered_set`
2. `unordered_map` 

- Common functions: `size()`, `clear()`, `begin()`, `end()`
### Iterators

- Pointer like objects used to access elements by their position.
- Created through begin() and end() functions.

### C++14 Variable Templates:

- `template <typename T>`
- `constexpr T variable = T(value);`

---

## Object-Oriented Programming

* Objects are used as fundamental blocks for building code.
* Objects are instances of some class.

- **Class**
	* blueprint that defines the kind of data and functions an object can hold 
	* represents an abstraction
	* can have multiple independent objects 
	* classes are united via inheritance 

- Access Modifiers:
1. **private** - only accessible inside the class.
2. **public** - accessible everywhere.
3. **protected** - accessible only to the class and its child classes

### Constructors

- **Constructor**
	* invoked automatically during object instantiation
	* used for object initialization
	* no return type
	* can be overloaded 
	* cannot be virtual

#### Types of Constructors

1. **Default Constructor**
	- no arguments
	- automatically defined and invoked by compiler 
	- only used when no other user-defined constructors exist 
2. **Parameterized Constructor**
	- has one or more arguments
	- used to initialize object
	- blocks auto generation of default constructor
3. **Destructor** 
	- invoked automatically when object is destroyed 
	- cannot be overloaded
	- used to release resources or perform any other final activities
	- no arguments
	- can be virtual (as a rule of thumb, must always be virtual)
	- `~Classname()`: called when object goes out of scope 
4. **Copy Constructor** 
	- copies state of one object into another 
	- default implementation copies values (shallow copy)
5. **Move Constructor**

#### Order of Construction

1. The base class, if any, is constructed.
2. Non-static data members are constructed in the order in which they were declared.
3. The body of the constructor is executed.

- Order of Destruction is exactly the opposite.

### OOP Principles

1. **Encapsulation** - bundling of data and functions into a single unit (*class*). 
2. **Abstraction** - showing necessary features while hiding unwanted details.
3. **Inheritance** - objects of one class acquire the properties of another class to promote code reusability. Classes are related through '*Is-a'* relationship.
	- `class <child class> : <access modifier> <base class> {};`
	- Child class inherits all members of parent class as access modifier mentioned.
	* Object Construction and Destruction:
		- Constructors execute from base to child
		- Destructors execute from child to base
		- Base data members will be part of child object
	* Any base class function can be called through a base reference to a derived instance.
	- **Virtual function** - derived class function executes. They cannot be static.
	- **Non-Virtual function** - base class function executes
	* Can't create a derived class reference that refers to a base class instance as some derived class members could be missing.
	* **Virtual base class** - used to solve the diamond problem.
	* An object can be cast or assigned to its parent class. If the cast or assignment is performed on a plain old object, this results in **slicing** because the resulting object is a *Base* object that lacks the additional functionality defined in the *Derived* Class.
	* However, slicing does not occur if a derived object is assigned to a pointer or reference to its base class.

4. **Polymorphism** - represents common behavior with different implementations. Objects of different types behave differently when the same method is called. It is implemented via function overloading, templates, virtual functions.
	- **Compile-time Polymorphism**: *function overloading* & *operator overloading* through ***static binding***. Static binding means that an object is bound to its function during compile-time. 
	- **Runtime Polymorphism**: *function overriding* using *virtual functions* through ***late/dynamic binding***. Object pointers and virtual functions are used to implement dynamic binding.

5. **Composition** - signifies relationship between objects (object composed in another object). It is  related through '*Has-a*' relationship. It promotes reuse of objects.

### C++11 Delegating Constructors

* allows a constructor to invoke another constructor
* used to reduce duplicate initialization code in multiple constructors

### C++11 Inheriting Constructors

* If child class does not need constructor definition and implementation, base class constructor can be invoked from child class.
-  `using <base class> :: <base class constructor>;`

### C++11 Non-Static Data Member Initializers

* Can be used to initialize member variables during declaration.
* Auto cannot be used.

```
class Class {
	<type1> <variable1> {<initializer>};
	...
};
```

* initialization in a user-defined constructor takes precedence.
- `this` Pointer:
	- hidden pointer passed to member function
	- points to the object which invoked the member function

- Static Members:
	* qualified with static keyword
	* belongs to the class, not to the object
	* only one copy exists that is shared between objects
	* static member variables cannot be initialized inside the class 
	* static member functions can be invoked using class name and cannot access non-static members 

### C++11 Default and Deleted Functions:

* **Default** - compiler provides default implementation
* **Delete** - compiler ensures no implementation is provided and that function cannot be called 
- `Function(args) = default/delete;`

		-- Virtual Keyword:
		
			* sometimes, even though pointer points to derived class object, compiler calls base class function
			* to avoid this, those functions must be marked virtual in base class 
			* How Virtual works:
				- a Virtual Table [Vtable] stores addresses of virtual functions 
				- starting address of Vtable is stored in a virtual pointer [Vptr]
				- when function is invoked:
					+ get object address
					+ get vptr
					+ find position of function in vtable
					+ get address of function
					+ invoke function
					
		-- Final Keyword:
		
			* a class marked final cannot be inherited
			* a function marked final cannot be overridden
			
		-- typeid Operator:
		
			* queries information of a type 
			
		-- Abstract Class:
		
			* has atleast one pure virtual function
			* cannot be instantiated 
			
			> virtual <return type> <function name> (<arguments>) = 0;
				- marking with =0 makes it a pure virtual function
				- does not provide function implementation (optional)
				- must be overridden by derived classes 
			> const std::type_info &ti = typeid(var);
			
			> class <class_name> final {};
			
				
				
		-- Operator Overloading:
		
			* custom implementation for primitive operators
			* allows usage of user-defined objects in mathematical expressions
			* overloaded as functions
			* uses operator keyword
			
			> <return type> operator <#> (<args>)
			
	
		-- Type Conversions:
		
			* conversion between types
			* performed through casts 
			* explicit conversions through casting operators
			* conversion between:
				- basic & basic
				- basic & user-defined
				- user-defined & basic
				- user-defined & user-defined
				
			> (type) var 
				- C-style cast
				- discards qualifiers 
				- not preferred
				
			> static_cast <type> (var)
				- better than C-style cast because it checks the validity of the cast
				- evaluated at compile-time

			> reinterpret_cast <type> (var) 
				- allows cast between different types
				- does not discard qualifiers
				- evaluated at compile-time
				
			> const_cast <type> (var)
			
			> operator <type> ()
				- Type Conversion Operator
				- no arguments
				- no return type 

--------------------------------------------------------------------------------------------------------------------------

## Exception Handling

- Exception is a runtime anomaly or an unusual condition encountered during program execution.

- `try` 
	- creates a scope where exception causing code can be added
	- can contain other try-catch statements	

- `throw` 
	- throws an exception from try block 
	- exception is an object constructed in throw statement

- catch 
	- handler that catches exception object
	- appears right after try block
	- multiple catch blocks can exist 

---

## Multithreading

- **Thread**: An execution unit within a process that shares memory space.
- **Concurrency**: Threads progress in an interleaved fashion by switching between each other (context switching). Occurs when threads use single processor core.
- **Parallelism**: Multiple threads work simultaneously and at the same time. Occurs when threads use multiple processor cores.

- A thread starts executing when created. **Creating a thread**: 
	`std::thread thread_name(function_name/functionPtr, params...);`
- Use `std::ref` to pass values by reference to thread function when creating threads.
- **Joining a thread**: The calling thread waits for thread object to finish execution.
- **Detaching a thread**: The calling thread continues execution without waiting for thread object to finish.
- `std::this_thread`: provides access to current thread.

### Thread Synchronization

- **Race Condition** - occurs when multiple threads try to modify shared data simultaneously.
- **Deadlock** - occurs when threads wait forever for locks held by each other.
- *If multiple threads access shared data, and at least one modifies it, synchronization is required.*

- **Mutex**: Used to ==lock/unlock resources== accessed by multiple threads.
```C++
std::mutex mtx;

void thread_fun() {
	std::lock_guard<std::mutex> guard(m);  // unlocks automatically at end of scope
}
```

- **Atomics**: Allows ==thread-safe operations without locks==. It is only good for single variable synchronization. Faster than mutex due to lesser overheads.
```C++
std::atomic<int> count{0};

void increment() {
	count++;  
}
```

- **Thread-local variables**: Each thread instance can have their own local variables as static/global inside thread scope. This is the fastest compared to mutex and atomics but ==cannot be used for shared data==. 
```C++
void increment() {
	thread_local var = 0;
	var++;
}
```

- Avoid shared state as much as possible.

### Inter-Thread Communication

- **Condition Variables** - used to make a thread wait until a certain condition is satisfied.
- `cv.wait(lock, predicate)`: releases mutex, puts thread to sleep, and re-acquires lock when woken up if condition is true
- `cv.notify_one()` & `cv.notify_all()`: wake up the sleeping threads that are waiting on the condition variable.

---

## Coding guidelines
	
1> Use pragma once instead of include guard 
2> Use const to define values rather than macros for magic numbers 
	> constexpr static auto VAR = value;
3> Use static_cast 
4> Use enum class instead of enum to avoid clashing of values
5> Avoid unnamed namespace, inline namespace and using directive to include all. Use namespace alias.
6> Use g_, l_, m_, f_ at the start of variable names to help identify its scope 
7> Make member variables private and use getter setter to access them 