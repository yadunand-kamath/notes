





---
## Basics & Pre-requisites

- **Interface** - a contract that specifies a set of functions that an object or component must implement. It promotes abstraction.
- **API (***Application Programming Interface***) - a set of rules that allow interaction between software, libraries, OS, or services.
- **Library** - a collection of pre-written code (functions, classes, etc.) that can be used by other programs to perform specific tasks. It promotes reusability.
- **Framework** - a collection of tools and libraries that provides a skeletal structure for building applications. It helps standardize development by providing an entire environment and structure for building applications.

### Compilation Process

1. **Preprocessing**
	- Preprocessor performs tasks like including header files, replacing macros with their values, removing comments, etc.
	- It generates a modified source code file.
2. **Compilation**
	- Compiler translates the preprocessed source code into assembly level code specific to target architecture.
3. **Assembly**
	- The assembler converts assembly language code to machine level code (binary instructions).
	- It generates an *object* (`.obj`) file.
4. **Linking**
	- Linker combines object files and required libraries into an *executable* (`.exe`) file.
	- An exe is a standalone program that can be directly run by the OS.

### Libraries

1. **Static Library** (`.lib`)
	- Collection of pre-compiled code that is copied into the executable during the linking phase of compilation.
	- Becomes a permanent part of the exe.
	- Each program has its own copy.
2. **Dynamic Library** (`.dll`)
	- Collection of pre-compiled code that exists as a separate file, whose reference is stored by the program.
	- DLL is loaded into program memory at runtime, when required.
	- Shared by multiple programs.

### Windows related terms

- `winver`: command to check Windows version.
- **Windows API functions** are documented, callable subroutines in the Windows API.
- **Win32 API** is the programming interface that was developed for the *32-bit* versions of Windows OS.
- **Native system services** (or **system calls**) are the undocumented, underlying services in the OS that are callable from *user mode*.
- **Kernel support functions** (or **routines**) are the subroutines inside the Windows OS that can be called only from *kernel mode*.
- **Windows services** are processes started by the *Windows service control manager*.
- **DLLs** are callable subroutines linked together as a binary file that can be dynamically loaded by applications that use the subroutines.
- **Handle** is a special identifier/reference that the program can use to refer to resources managed by the OS.
- In the Windows OS, a **kernel object** is a single, run-time instance of a statically defined object type. An object type comprises a system-defined data type, functions that operate on instances of the data type, and a set of object attributes.
- **Windows Registry** is the system database used to boot and configure the system. It is a useful source of Windows internals information.
- **Kernel debugging** means examining internal kernel data structures and/or stepping through functions in the kernel.

### Access Modes

1. Windows Privilege Level 3 (Ring 3)
	- User Mode 
	- Restricted access to system resources.
2. Windows Privilege Level 0 (Ring 0) 
	- Kernel Mode 
	- Unrestricted access to system resources.

- Each page in virtual memory is tagged to indicate what access mode the processor must be in to read and/or write the page. Pages in system space can be accessed only from kernel mode, whereas all pages in the user address space are accessible from user mode and kernel mode.
- It’s normal for a user thread to spend part of its time executing in user mode and part in kernel mode.
- Graphics intensive applications spend more of their time in kernel mode than in user mode.

### Processes

- A **program** is a static sequence of instructions.
- A **process** is a container for a set of resources used when executing the instance of the program. It is an active instance of a program in execution.
- When the OS executes a program, it creates a process with its own isolated memory and resources. A single program can have multiple processes running in isolation from each other.
- The **Task Manager** (`Ctrl + Shift + Esc` or `Ctrl + Alt + Del`) is used to examine process activity.
- Each process contains:
	1. Private Virtual Address Space 
	2. An Executable Program
	3. Threads (one or more)
	4. List of open handles to kernel objects opened by threads
	5. Access Token - stores the process's security context (identification & credentials)
	6. Process ID
	
#### Threads

- A **thread** is the smallest unit of execution within a process. While the process has the memory and resources, the thread performs the execution.
- Multiple threads can work simultaneously on different tasks, while sharing the same memory and resources within a process.
- Each thread can have the following in its context:
	1. Program Counter (Instruction Pointer)
	2. Two Stacks
		- User mode
		- Kernel mode
	3. CPU Registers representing the state of the processor.
	4. Thread Local Storage
	5. Thread ID
- The threads of a 32-bit application running on a 64-bit version of Windows will contain both 32-bit and 64-bit contexts.

---
## COM (*Component Object Model*)

- Originally developed to exchange data between documents of *Microsoft Office* application.
- **OLE** (***Object Linking and Embedding***) was implemented using **DDE** (***Dynamic Data Exchange***), an old Windows messaging mechanism.
- **WinRT** (***Windows Runtime***), built on top of COM, consists of platform services aimed for Windows Apps development.

### COM Principles

1. Clients communicate with objects (COM server objects) through interfaces.
2. Component implementation is loaded dynamically.

- COM server is **DLL** (***Dynamic Link Library***) or **Executable** (***exe***) where the COM classes are implemented.

---

## System Architecture

- The OS kernel code runs in a privileged processor mode (***kernel mode***), with access to system data and to the hardware.
- Application code runs in a non-privileged processor mode (***user mode***), with a limited set of interfaces available, limited access to system data, and no direct access to hardware.

### Multiprocessing

- **Multitasking** is the OS technique for sharing a single processor among multiple threads of execution. When a computer has more than one processor, however, it can execute multiple threads simultaneously.
- Windows is a SMP OS.

1. **Symmetric Multiprocessing** (***SMP***) 
	- The OS as well as user threads can be scheduled to run on any processor.
	- There is no master processor.
	- All the processors share just one memory space.
2. **Asymmetric Multiprocessing** (***ASMP***)
	- The OS typically selects one processor to execute OS kernel code while other processors run only user code.

### Device Drivers

- Device drivers are loadable kernel-mode modules (files typically ending with the `.sys` extension) that interface between the I/O manager and the relevant hardware.