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
and why. Archeologists will find this the most useful information.

## Use Headers

Use a document extraction system like [Doxygen](https://github.com/doxygen).

These headers are structured in such a way as they can be parsed and
extracted. They are not useless like normal headers. So take time to
fill them out. If you do it right once no more documentation may be
necessary.

## Comment Layout

Each part of the project has a specific comment layout.
[Doxygen](https://github.com/doxygen) has the recommended format for the
comment layouts.

## Make Gotchas Explicit

Explicitly comment variables changed out of the normal control flow or
other code likely to break during maintenance. Embedded keywords are
used to point out issues and potential problems. Consider a robot will
parse your comments looking for keywords, stripping them out, and making
a report so people can make a special effort where needed.

### Gotcha Keywords

- **\@author:**\
    specifies the author of the module
- **\@version:**\
    specifies the version of the module
- **\@param:**\
    specifies a parameter into a function
- **\@return:**\
    specifies what a function returns
- **\@deprecated:**\
    says that a function is not to be used anymore
- **\@see:**\
    creates a link in the documentation to the file/function/variable to
    consult to get a better understanding on what the current block of
    code does.
- **\@todo:**\
    what remains to be done
- **\@bug:**\
    report a bug found in the piece of code

### Gotcha Formatting

- Make the gotcha keyword the first symbol in the comment.
- Comments may consist of multiple lines, but the first line should be
    a self-containing, meaningful summary.
- The writer's name and the date of the remark should be part of the
    comment. This information is in the source repository, but it can
    take a quite a while to find out when and by whom it was added.
    Often gotchas stick around longer than they should. Embedding date
    information allows other programmer to make this decision. Embedding
    who information lets us know who to ask.

## Commenting function declarations

Functions headers should be in the file where they are declared. This
means that most likely the functions will have a header in the .h file.
However, functions like main() with no explicit prototype declaration in
the .h file, should have a header in the .c file.

## Include Statement Documentation

Include statements should be documented, telling the user why a
particular file was included.\
/\*\
\* Kernel include files come first.\
\*/\
/\* Non-local includes in brackets. \*/\
/\*\
\* If it's a network program, put the network include files next.\
\* Group the includes files by subdirectory.\
\*/\
/\*\
\* Then there's a blank line, followed by the /usr include files.\
\* The /usr include files should be sorted!\
\*/
