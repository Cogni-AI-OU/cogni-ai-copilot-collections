# Documentation

## Comments Should Tell a Story

Consider your comments a story describing the system. Expect your
comments to be extracted by a robot and formed into a man page. Class
comments are one part of the story, method signature comments are
another part of the story, method arguments another part, and method
implementation yet another part. All these parts should weave together
and inform someone else at another point of time just exactly what you
did and why.

## Document Decisions

Comments should document decisions. At every point where you had a
choice of what to do place a comment describing which choice you made
and why.

## Use Headers

Use a document extraction system like [Doxygen](http://www.doxygen.org)
. Other sections in this document describe how to use ccdoc to document
a class and method.

These headers are structured in such a way as they can be parsed and
extracted. They are not useless like normal headers. So take time to
fill them out. If you do it right once no more documentation may be
necessary.

## Make Gotchas Explicit

Explicitly comment variables changed out of the normal control flow or
other code likely to break during maintenance. Embedded keywords are
used to point out issues and potential problems. Consider a robot will
parse your comments looking for keywords, stripping them out, and making
a report so people can make a special effort where needed. For a
complete list of Gotcha Keywords, please refer to
[Doxygen](http://www.doxygen.org/) . Here are some useful ones:

### Gotcha Keywords

-   **\@author:**\
    specifies the author of the module
-   **\@version:**\
    specifies the version of the module
-   **\@param:**\
    specifies a parameter into a function
-   **\@return:**\
    specifies what a function returns
-   **\@deprecated:**\
    says that a function is not to be used anymore
-   **\@see:**\
    creates a link in the documentation to the file/function/variable to
    consult to get a better understanding on what the current block of
    code does.
-   **\@todo:**\
    what remains to be done
-   **\@bug:**\
    report a bug found in the piece of code

### Gotcha Formatting

-   Make the gotcha keyword the first symbol in the comment.
-   Comments may consist of multiple lines, but the first line should be
    a self-containing, meaningful summary.
-   The writer's name and the date of the remark should be part of the
    comment. This information is in the source repository, but it can
    take a quite a while to find out when and by whom it was added.
    Often gotchas stick around longer than they should. Embedding date
    information allows other programmer to make this decision. Embedding
    who information lets us know who to ask.

### Example

       // :TODO: tmh 960810: possible performance problem
       // We should really use a hash table here but for now we'll
       // use a linear search.

       // :KLUDGE: tmh 960810: possible unsafe type cast
       // We need a cast here to recover the derived type. It should
       // probably use a virtual method or template.

## Commenting function declarations

Functions headers should be in the file where they are declared. This
means that most likely the functions will have a header in the .hh file.
However, functions like main() with no explicit prototype declaration in
the .hh file, should have a header in the .cn file.

## Include Statement Documentation

Include statements should be documented, telling the user why a
particular file was included. If the file includes a class used by the
class then it's useful to specify a class relationship:

-   ISA
-   HASA
-   USES

### Example

    #ifndef XX_h
    #define XX_h

    // SYSTEM INCLUDES
    //
    #include                              
    #include 

# Using Use Cases

A *use case* is a generic description of an entire transaction involving
several objects. A use case can also describe the behaviour of a set of
objects, such as an organization. A use case model thus presents a
collection of use cases and is typically used to specify the behavior of
a whole application system together with one or more external actors
that interact with the system.

An individual use case may have a name (although it is typically not a
simple name). Its meaning is often written as an informal text
description of the external actors and the sequences of events between
objects that make up the transaction. Use cases can include other use
cases as part of their behaviour.

## Requirements Capture

Use cases attempt to capture the requirements for a system in an
understandable form. The idea is by running through a set of use case we
can verify that the system is doing what it should be doing.

Have as many use cases as needed to describe what a system needs to
accomplish.

## The Process

-   Start by understanding the system you are trying to build.
-   Create a set of use cases describing how the system is to be used by
    all its different audiences.
-   Create a class and object model for the system.
-   Run through all the use cases to make sure your model can handle all
    the cases. Update your model and create new use cases as necessary.

# Unified Modeling Language

The Unified Modeling Language is too large to present here. Fortunately
you can see it at [Rational's](http://www.rational.com/ot/uml.html) web
site. Since you do need a modeling language UML is a safe choice. It
combines features from several methods into one unified language.
Remember all languages and methods are open to local customization. If
their language is too complex then use the parts you and your project
feel they need and junk the rest.

# OPEN Method

[OPEN](http://www.markv.com/OPEN/) stands for **Object-oriented Process,
Environment and Notation** and is a worthy if not superior competitor to
UML. It is another group effort composed of basically all the people not
in the UML group :-) Their web site has a good comparison of OPEN and
UML.

My guess is UML will win out for marketing reasons. But it is good to
have some competition going.

# Open/Closed Principle

The Open/Closed principle states a class must be open and closed where:

-   open means a class has the ability to be extended.
-   closed means a class is closed for modifications other than
    extension. The idea is once a class has been approved for use having
    gone through code reviews, unit tests, and other qualifying
    procedures, you don't want to change the class very much, just
    extend it.

The Open/Closed principle is a pitch for stability. A system is extended
by adding new code not by changing already working code. Programmers
often don't feel comfortable changing old code because it works! This
principle just gives you an academic sounding justification for your
fears :-)

In practice the Open/Closed principle simply means making good use of
our old friends abstraction and polymorphism. Abstraction to factor out
common processes and ideas. Inheritance to create an interface that must
be adhered to by derived classes. In C++ we are talking about using
[abstract base classes](CppCodingStandard.html#abstract) . A lot.

# Design by Contract

The idea of design by contract is strongly related to
[LSP](CppCodingStandard.html#liskov) . A contract is a formal statement
of what to expect from another party. In this case the contract is
between pieces of code. An object and/or method states that it does X
and you are supposed to believe it. For example, when you ask an object
for its volume that's what you should get. And because volume is a
verifiable attribute of a thing you could run a series of checks to
verify volume is correct, that is, it satisfies its contract.

The contract is enforced in languages like Eiffel by pre and post
condition statements that are actually part of the language. In other
languages a bit of faith is needed.

Design by contract when coupled with language based verification
mechanisms is a very powerful idea. It makes programming more like
assembling spec'd parts.

