

## Introduction

- MFC is a collection of C++ classes for Microsoft Windows OS
- Object class is derived from `CObject` class
- Application class is derived from `CWinApp`
- Windows class is derived from `CWnd` base class
- `<afxwin>` is the header file for MFC

---
## MFC Programming

 3 main classes:

1. `CWinApp` 
	- Base class from which you derive a Windows application object.
	- Contains code to setup application and establishes document and view architecture.
	- Each application that uses the Microsoft Foundation classes can only contain one object derived from `CWinApp`.
	- `InitInstance` member function is called every time a new instance of the application starts. Override the `InitInstance` member function to create your application's main window object.
2. `CDocument` 
	- Provides the basic functionality for user-defined document classes.
	- Holds application data and responsible for serializing data (saving and loading).
	- The document template specifies what type of view and frame window are used to display each type of document.
3. `CView` 
	- Provides the basic functionality for user-defined view classes. Users interact with a document through the `CView` object(s) associated with it.
	- A view is attached to a document and acts as an intermediary between the document and the user: the view renders an image of the document in a frame window and interprets user input as operations upon the document.
	- Responsible for retrieving application data and drawing it to the window.
	- A view can be attached to only one document, but a document can have multiple views attached to it at once

- The **Document** holds the data, the **View** shows it to you, and the **Frame** holds everything together and lets you interact with it.
- The **Document Template** manages the complex process of creating documents with their associated views and frame windows.

- MFC App variants:
	1. Single View Doc 
		- shows only one view at a time. Might have `CMainFrame` but no `CChildFrame`.
		- `CMainFrame` represents Main Window of application, which contains the View.
	2. Multi View Doc - mainframe will host many Child Windows.

| Creator            | Creates           |
| ------------------ | ----------------- |
| Application object | Document template |
| Document template  | Document          |
| Document template  | Frame window      |
| Frame window       | View              |

### VC++ GUI

- CDialog: 
	- The CDialog class is the base class used for displaying dialog boxes on the screen. 
	- Dialog boxes are of two types: 
		1. Modal - must be closed by the user for the application to continue. 
		2. Modeless - allows the user to display the dialog box and return to another task without canceling or removing the dialog box.
		
- CEdit: 
	- The CEdit class provides the functionality of a Windows edit control. 
	- An edit control is a rectangular child window in which the user can enter text.
	
- CFrameWnd: 
	- The CFrameWnd class provides the functionality of a Windows Single Document Interface (SDI) overlapped or pop-up frame window, along with members for managing the window.
	
- CDocument: 
	- The CDocument class provides the basic functionality for user-defined document classes. 
	- A document represents the unit of data that the user typically opens with the File->Open command and saves with the File->Save command.
	
- CView: 
	- The CView class provides the basic functionality for user-defined view classes. 
	- A view is attached to a document and acts as an intermediary between the document and the user. 
	- The view renders an image of the document on the screen or printer and interprets user input as operations upon the document.
	
- CPen: 
	- The CPen class encapsulates a Windows graphics device interface (GDI) pen.

- CRect: 
	- A CRect contains member variables that define the top-left and bottom-right points of a rectangle.

- CPoint: 
	- The CPoint class is similar to the Windows POINT structure. 
	- It also includes member functions to manipulate CPoint and POINT structures.

- CMenu: 
	- The CMenu class is an encapsulation of the Windows HMENU. 
	- It provides member functions for creating, tracking, updating, and destroying a menu.
	
- CDC:
	- CDC is the most fundamental class to draw in MFC.
	- The CDC object provides member functions to perform the basic drawing steps, as well as members for working with a display context associated with the client area of a window.
	
### Window Resources

- A resource is a text file that allows the compiler to manage objects such as pictures, sounds, mouse cursors, dialog boxes, etc. 
- An application can use various resources that behave independently of each other, and these resources are grouped into a text file that has the *.rc extension.

### Windows GDI 

- **GDI**(***Graphics Device Interface***) is an API for creating and displaying graphical objects in Windows.
- **Device Context** - defines the attributes of objects being displayed. 
- **HDC**(***Handle to Device Context***) - before an object can be drawn, a handle (pointer) to the display output must be obtained.


- CPaintDC - responds to WM_PAINT message events that trigger the OnPaint() message handler function.
- CClientDC - created when only the device context of the client area of a Window is desired.
- Invalidate() - invalidates a specified area or object, marking it for repaint the next time WM_PAINT triggers OnPaint message handler.
- CRect - builds a rectangular region of a specified size 
- DrawText() - allows to draw text directly on a CDialog window's background

---
## Message Maps 

- MS Windows is a message oriented OS
- Every event in Windows involves Message Handling.
- Message Maps connect messages to their handler functions. They are a list of macros where programmer specifies which event is handled by which function.
- A large part of your programming task is choosing which messages to map to which objects and then implementing that mapping.

### Message Categories

1. Windows Messages
	- begin with prefix "WM_" 
	- handled by objects derived from CWnd and views
	
2. Control Messages
	- WM_COMMAND notifications
	- sent from controls and child windows to their parent windows
	- handled by a single object
	
3. Command Messages
	- WM_COMMAND messages from UI objects 
	- handled by many objects
	
### Important Macros

- DECLARE_MESSAGE_MAP - specifies that the class defines a message map
- BEGIN_MESSAGE_MAP - marks the beginning of the message map
- END_MESSAGE_MAP - marks the end of the message map
- ON_COMMAND - command message
- ON_CONTROL - control-notification message
- ON_MESSAGE - user-defined message
- ON_COMMAND_RANGE - range of specified command IDs

### Command Targets and Command Routes

- Each framework class that can receive messages or commands has its own message map.
- Windows messages are usually sent to main frame window but command messages are routed to other objects, called command targets.
- When a command target receives a command message, it is redirected as follows:
	Active child command targets -> Self -> Other command targets 

---