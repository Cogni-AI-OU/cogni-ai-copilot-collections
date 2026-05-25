# Required Methods for a Class

To be good citizens almost all classes should implement the following
methods. If you don't have to define and implement any of the
"required" methods they should still be represented in your class
definition as comments.

-   **Default Constructor**

    If your class needs a constructor, make sure to provide one. You
    need one if during the operation of the class it creates something
    or does something that needs to be undone when the object dies. This
    includes creating memory, opening file descriptors, opening
    transactions etc.

    If the default constructor is sufficient add a comment indicating
    that the compiler-generated version will be used.

    If your default constructor has one or more optional arguments, add
    a comment indicating that it still functions as the default
    constructor.

-   **Virtual Destructor**

    If your class is intended to be derived from by other classes then
    make the destructor virtual.

-   **Copy Constructor**

    If your class is copyable, either define a copy constructor and
    assignment operator or add a comment indicating that the
    compiler-generated versions will be used.

    If your class objects should not be copied, make the copy
    constructor and assignment operator private and don't define bodies
    for them. If you don't know whether the class objects should be
    copyable, then assume not unless and until the copy operations are
    needed.

-   **Assignment Operator**

    If your class is assignable, either define a assignment operator or
    add a comment indicating that the compiler-generated versions will
    be used.

    If your objects should not be assigned, make the assignment operator
    private and don't define bodies for them. If you don't know
    whether the class objects should be assignable, then assume not.

## Justification

-   Virtual destructors ensure objects will be completely destructed
    regardless of inheritance depth. You don't have to use a virtual
    destructor when:
    -   You don't expect a class to have descendants.
    -   An object must have a certain data layout and size.
-   A default constructor allows an object to be used in an array.
-   The copy constructor and assignment operator ensure an object is
    always properly constructed.

## The Law of The Big Three

A class with any of (destructor, assignment operator, copy constructor)
generally needs all 3. For more information see
http://www.parashift.com/c++-faq-lite/coding-standards.html#\[25.9\].

## Example

An example using default values:

    class Planet
    {
    public:
      // The following is the default constructor if
      // no arguments are supplied:
      //
      Planet(int radius= 5);

      // Use compiler-generated copy constructor, assignment, and destructor.
      // Planet(const Planet&);
      // Planet& operator=(const Planet&);
      // ~Planet();
    };

# Classes

## Naming Class Files

### Class Definition in One File

Each class definition should be in its own file where each file is named
directly after the class's name:

       ClassName.hh

### Implementation in One File

In general each class should be implemented in one source file:

       ClassName.cc   // or whatever the extension is: cpp, c++

### But When it Gets Really Big\...

If the source file gets too large or you want to avoid compiling
templates all the time then add additional files named according to the
following rule:

       ClassName_section.C

**section** is some name that identifies why the code is chunked
together. The class name and section name are separated by '\_'.

## Class Layout

A common class layout is critical from a code comprehension point of
view and for automatically generating documentation. C++ programmers,
through a new set of tools, can enjoy the same level generated
documentation Java programmers take for granted.

### Class and Method Documentation

It is recommended a program like [Doxygen](https://github.com/doxygen) be
used to document C++ classes, method, variables, functions, and macros.
The documentation can be extracted and put in places in a common area
for all programmers to access. This saves programmers having to read
through class headers. Documentation generation should be integrated
with the build system where possible.

### Required Methods Placeholders

This template has placeholders for [required methods](https://users.ece.cmu.edu/~eno/coding/CppCodingStandard.html#req) . You can delete them or implement
them.

## Ordering is: public, protected, private

Notice that the public interface is placed first in the class, protected
next, and private last. The reasons are:

-   programmers should care about a class's interface more than
    implementation
-   when programmers need to use a class they need the interface not the
    implementation

It makes sense then to have the interface first. Placing implementation,
the private section, first is a historical accident as the first
examples used the private first layout. Over time emphasis has switched
deemphasizing a class's interface over implementation details.

### LIFECYCLE

The life cycle section is for methods that control the life cycle of an
object. Typically these methods include constructors, destructors, and
state machine methods.

### OPERATORS

Place all operators in this section.

### OPERATIONS

Place the bulk of a class's non access and inquiry method methods here.
A programmer will look here for the meat of a class's interface.

### ACCESS

Place attribute accessors here.

### INQUIRY

These are the *Is\** methods. Whenever you have a question to ask about
an object it can be asked via in *Is* method. For example: IsOpen() will
indicate if the object is open. A good strategy is instead of making a
lot of access methods you can turn them around to be questions about the
object thus reducing the exposure of internal structure. Without the
IsOpen() method we might have had to do: if (STATE_OPEN == State())
which is much uglier.

## What should go in public/protected/private?

### Public Section

Only put an object's interface in the public section. **DO NOT** expose
any private data items in the public section. At least encapsulate
access via access methods. Ideally your method interface should make
most access methods unnecessary. Do not put data in the public
interface.

### Protected and Private Section

What should go into the protected section versus the private section is
always a matter of debate.

#### All Protected

Some say there should be no private section and everything not in the
public section should go in the protected section. After all, we should
allow all our children to change anything they wish.

#### All Private

Another camp says by making the public interface virtual any derived
class can change behavior without mucking with internals.

#### Wishy Washy

Rationally decide where elements should go and put them there. Not very
helpful.

#### And the Winner Is\...

Keeping everything all private seems the easiest approach. By making the
public methods virtual flexibility is preserved.

## Method Layout

 The approach used is to place a comment block before each
method that can be extracted by a tool and be made part of the class
documentation. Here we'll use [Doxygen](https://github.com/doxygen) . See
the Doxygen documentation for a list of attributes supported by the
document generator.

### Method Header

Follow Doxygen's way.

## Use of Namespaces

Namespaces are now commonly implemented by compilers. They should be
used if you are sure your compiler supports them completely.

### Naming Policy

There are two basic strategies for naming: root that name at some naming
authority, like the company name and division name; try and make names
globally independent.

### Don't Globally Define using

Don't place "using namespace" directive at global scope in a header
file. This can cause lots of magic invisible conflicts that are hard to
track. Keep using statements to implementation files.

## Use Header File Guards

Include files should protect against multiple inclusion through the use
of macros that "guard" the files.

### When Not Using Namespces

    #ifndef filename_h
    #define filename_h

    #endif

The new line after the endif if is required by some compilers.

When Using Namespaces

If namespaces are used then to be completely safe:

    #ifndef namespace_filename_h
    #define namespace_filename_h

    #endif

1.  Replace *filename* with the name of the file being guarded. This
    should usually be the name of class contained in the file. Use the
    exact class name. Some standards say use all upper case. This is a
    mistake because someone could actually name a class the same as
    yours but using all upper letters. If the files end up be included
    together one file will prevent the other from being included and you
    will be one very confused puppy. It has happened!
2.  Most standards put a leading **\_** and trailing **\_**. This is no
    longer valid as the C++ standard reserves leading \_ to compiler
    writers.
3.  When the include file is not for a class then the file name should
    be used as the guard name.
4.  Compilers differ on how comments are handled on preprocessor
    directives. Historically many compilers have not accepted comments
    on preprocessor directives.
5.  Historically many compilers require a new line after last endif.

## Different Accessor Styles

### Why Accessors?

Access methods provide access to the physical or logical attributes of
an object. Accessing an object's attributes directly as we do for C
structures is greatly discouraged in C++. We disallow direct access to
attributes to break dependencies, the reason we do most things. Directly
accessing an attribute exposes implementation details about the object.

To see why ask yourself:

-   What if the object decided to provide the attribute in a way other
    than physical containment?
-   What if it had to do a database lookup for the attribute?
-   What if a different object now contained the attribute?

If any of the above changed code would break. An object makes a contract
with the user to provide access to a particular attribute; it should not
promise how it gets those attributes. Accessing a physical attribute
makes such a promise.

### Accessors Considered Somewhat Harmful

At least in the public interface having accessors many times is an
admission of failure, a failure to make an object's interface complete.
At the protected or private level accessors are fine as these are the
implementation levels of a class.

### Implementing Accessors

There are three major idioms for creating accessors.

#### Get/Set

       class X
       {
       public:
          int    GetAge() const     { return aAge; }
          void   SetAge(int age)    { aAge= age; }
       private:
          int aAge;
       }

The problem with Get/Set is twofold:

-   It's ugly. Get and Set are strewn throughout the code cluttering it
    up.
-   It doesn't treat attributes as objects in their own right. An
    object will have an assignment operator. Why shouldn't age be an
    object and have its own assignment operator?

One benefit, that it shares with the *One Method Name*, is when used
with messages the set method can transparently transform from native
machine representations to network byte order.

#### One Method Name

       class X
       {
       public:
          int    Age() const     { return aAge; }
          void   Age(int age)    { aAge= age; }
       private:
          int aAge;
       }

Similar to Get/Set but cleaner. Use this approach when not using the
*Attributes as Objects* approach.

#### Attributes as Objects

       class X
       {
       public:
          int              Age() const     { return aAge; }
          int&             rAge()          { return aAge; }

          const String&    Name() const    { return aName; }
          String&          rName()         { return aName; }
       private:
          int              aAge;
          String           aName;
       }

The above two attribute examples shows the strength and weakness of the
Attributes as Objects approach.

When using an int type, which is not a real object, the int is set
directly because *rAge()* returns a **reference**. The object can do no
checking of the value or do any representation reformatting. For many
simple attributes, however, these are not horrible restrictions. A way
around this problem is to use a class wrapper around base types like
int.

When an object is returned as reference its *=* operator is invoked to
complete the assignment. For example:

       X x;
       x.rName()= "test";

This approach is also more consistent with the object philosophy: the
object should do it. An object's *=* operator can do all the checks for
the assignment and it's done once in one place, in the object, where it
belongs. It's also clean from a name perspective.

When possible use this approach to attribute access.

## Initialize all Variables

-   You shall always initialize variables. Always. Every time.

### Justification

-   More problems than you can believe are eventually traced back to a
    pointer or variable left uninitialized. C++ tends to encourage this
    by spreading initialization to each constructor.

## Think About What Work to do in Constructors

Should you do work that can fail in constructors? If you have a compiler
that does not support exceptions (or thread safe exceptions if it
matters to you) then the answer is definitely no.

### Do Work in Open

Do not do any real work in an object's constructor. Inside a
constructor initialize variables only and/or do only actions that can't
fail.

Create an Open() method for an object which completes construction.
Open() should be called after object instantiation.

#### Example

       class Device
       {
       public:
          Device()    { /* initialize and other stuff */ }
          int Open()  { return FAIL; }
       };

       Device dev;
       if (FAIL == dev.Open()) exit(1);

### Use Open Reasons

1.  It is difficult to write exception safe code in constructor. It's
    possible to throw an exception and not destruct objects allocated in
    the constructor. Use of **auto_ptr** can help prevent this problem.
2.  Some compilers do not support thread safe exceptions on all
    platforms.
3.  Virtual methods are not available in base classes. If the base class
    is expecting a virtual method implemented by derived classes to be
    available during construction then initialization must follow
    construction. This is common in frameworks.
4.  Larger scale state machines may dictate when initialization should
    occur. An object may contain numerous other objects that may have
    complex initialization conditions. In this case we could wait to
    construct objects but then we always have to worry about null
    pointers.
5.  If deletion is needed to free resources we still may want to keep
    the state around for debugging or statistics or as a supplier of
    information for other objects.

### Do Work in Constructor

With exceptions work done in the constructor can signal failure so it is
fine to perform real work in the constructor. This is the guru endorced
approach as a matter of fact.

The constructor code must still be very careful not to leak resources in
the constructor. It's possible to throw an exception and not destruct
objects allocated in the constructor.

There is a pattern called **Resource Acquisition as Initialization**
that says all initialization is performed in the constructor and
released in the destructor. The idea is that this is a safer approach
because it should reduce resource leaks.

## Be Careful Throwing Exceptions in Destructors

An object is presumably created to do something. Some of the changes
made by an object should persist after an object dies (is destructed)
and some changes should not. Take an object implementing a SQL query. If
a database field is updated via the SQL object then that change should
persist after the SQL objects dies. To do its work the SQL object
probably created a database connection and allocated a bunch of memory.
When the SQL object dies we want to close the database connection and
deallocate the memory, otherwise if a lot of SQL objects are created we
will run out of database connections and/or memory.

The logic might look like:

    Sql::~Sql()
    {
       delete connection;
       delete buffer;
    }

Let's say an exception is thrown while deleting the database
connection. Will the buffer be deleted? No. Exceptions are basically
non-local gotos with stack cleanup. The code for deleting the buffer
will never be executed creating a gaping resource leak.

Special care must be taken to catch exceptions which may occur during
object destruction. Special care must also be taken to fully destruct an
object when it throws an exception.
