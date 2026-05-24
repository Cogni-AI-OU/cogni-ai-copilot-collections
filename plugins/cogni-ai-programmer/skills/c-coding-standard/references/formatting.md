# Formatting

## Brace Placement

Of the three major brace placement strategies one is recommended:

## When Braces are Needed

All if, while and do statements must either have braces or be on a
single line.

### Always Uses Braces Form

All if, while and do statements require braces even if there is only a
single statement within the braces. For example:

    if (1 == somevalue) {
       somevalue = 2;
    }

#### Justification for Always Using Braces Form

It ensures that when someone adds a line of code later there are already
braces and they don't forget. It provides a more consistent look. This
doesn't affect execution speed. It's easy to do.

### One Line Form

    if (1 == somevalue) somevalue = 2;

#### Justification for One Line Form

It provides safety when adding new lines while maintaining a compact
readable form.

## Add Comments to Closing Braces

Adding a comment to closing braces can help when you are reading code
because you don't have to find the begin brace to know what is going
on.

    while(1) {
       if (valid) {

       } /* if valid */
       else {
       } /* not valid */

    } /* end forever */

## Consider Screen Size Limits

Some people like blocks to fit within a common screen size so scrolling
is not necessary when reading code.\

## Parens *()* with Key Words and Functions Policy

- Do not put parens next to keywords. Put a space between.
- Do put parens next to function names.
- Do not use parens in return statements when it's not necessary.

### Justification for Parens Policy

-   Keywords are not functions. By putting parens next to keywords
    keywords and function names are made to look alike.

### Example

        if (condition) {
        }

        while (condition) {
        }

        strcpy(s, s1);

        return 1;

## A Line Should Not Exceed 78 Characters

- Lines should not exceed 78 characters.

## Justification for Line Length Policy

-   Even though with big monitors we stretch windows wide our printers
    can only print so wide. And we still need to print code.
-   The wider the window the fewer windows we can have on a screen. More
    windows is better than wider windows.
-   We even view and print diff output correctly on all terminals and
    printers.

## *If Then Else* Formatting

### Layout

It's up to the programmer. Different bracing styles will yield slightly
different looks. One common approach is:

       if (condition) {
       } else if (condition) {
       } else {
       }

If you have *else if* statements then it is usually a good idea to
always have an else block for finding unhandled cases. Maybe put a log
message in the else even if there is no corrective action taken.

### Condition Format

Always put the constant on the left hand side of an equality/inequality
comparison. For example:

if ( 6 == errorNum ) \...

One reason is that if you leave out one of the = signs, the compiler
will find the error for you. A second reason is that it puts the value
you are looking for right up front where you can find it instead of
buried at the end of your expression. It takes a little time to get used
to this format, but then it really gets useful.

## *switch* Formatting

- Falling through a case statement into the next case statement shall
    be permitted as long as a comment is included.
- The *default* case should always be present and trigger an error if
    it should not be reached, yet is reached.
- If you need to create variables put all the code in a block.

### Example

       switch (...)
       {
          case 1:
             ...
          /* comments */

          case 2:
          {
             int v;
             ...
          }
          break;

          default:
       }

## Use of *goto,continue,break* and *?:*

### Goto

Goto statements should be used sparingly, as in any well-structured
code. The goto debates are boring so we won't go into them here. The
main place where they can be usefully employed is to break out of
several levels of switch, for, and while nesting, although the need to
do such a thing may indicate that the inner constructs should be broken
out into a separate function, with a success/failure return code.

       for (...) {
          while (...) {
          ...
             if (disaster) {
                goto error;

             }
          }
       }
       ...
    error:
       clean up the mess

When a goto is necessary the accompanying label should be alone on a
line and to the left of the code that follows. The goto should be
commented (possibly in the block header) as to its utility and purpose.

### Continue and Break

Continue and break are really disguised gotos so they are covered here.

Continue and break like goto should be used sparingly as they are magic
in code. With a simple spell the reader is beamed to god knows where for
some usually undocumented reason.

The two main problems with continue are:

- It may bypass the test condition
- It may bypass the increment/decrement expression

Consider the following example where both problems occur:

    while (TRUE) {
       ...
       /* A lot of code */
       ...
       if (/* some condition */) {
          continue;
       }
       ...
       /* A lot of code */
       ...
       if ( i++ > STOP_VALUE) break;
    }

Note: "A lot of code" is necessary in order that the problem cannot be
caught easily by the programmer.

From the above example, a further rule may be given: Mixing continue
with break in the same loop is a sure way to disaster.

### ?:

The trouble is people usually try and stuff too much code in between the
*?* and *:*. Here are a couple of clarity rules to follow:

- Put the condition in parens so as to set it off from other code
- If possible, the actions for the test should be simple functions.
- Put the action for the then and else statement on a separate line
    unless it can be clearly put on one line.

### Example

       (condition) ? funct1() : func2();

       or

       (condition)
          ? long statement
          : another long statement;

## One Statement Per Line

There should be only one statement per line unless the statements are
very closely related.

The reasons are:

1.  The code is easier to read. Use some white space too. Nothing better
    than to read code that is one line after another with no white space
    or comments.

### One Variable Per Line

Related to this is always define one variable per line:

    Not:
    char **a, *x;

    Do:
    char **a = 0;  /* add doc */
    char  *x = 0;  /* add doc */

The reasons are:

1.  Documentation can be added for the variable on the line.
2.  It's clear that the variables are initialized.
3.  Declarations are clear which reduces the probability of declaring a
    pointer when you meant to declare just a char.

## To Use Enums or Not to Use Enums

C allows constant variables, which should deprecate the use of enums as
constants. Unfortunately, in most compilers constants take space. Some
compilers will remove constants, but not all. Constants taking space
precludes them from being used in tight memory environments like
embedded systems. Workstation users should use constants and ignore the
rest of this discussion.

In general enums are preferred to *#define* as enums are understood by
the debugger.

Be aware enums are not of a guaranteed size. So if you have a type that
can take a known range of values and it is transported in a message you
can't use an enum as the type. Use the correct integer size and use
constants or *#define*. Casting between integers and enums is very error
prone as you could cast a value not in the enum.

     

## Use Header File Guards

Include files should protect against multiple inclusion through the use
of macros that "guard" the files. Note that for C++ compatibility and
interoperability reasons, do **not** use underscores '\_' as the
first or last character of a header guard (see below)

    #ifndef sys_socket_h
      #define sys_socket_h  /* NOT _sys_socket_h_ */
      #endif

## Macros

### Don't Turn C into Pascal

Don't change syntax via macro substitution. It makes the program
unintelligible to all but the perpetrator.

### Replace Macros with Inline Functions

In C macros are not needed for code efficiency. Use inlines. However,
macros for small functions are ok.

#### Example

    #define  MAX(x,y) (((x) > (y)) ? (x) : (y)) // Get the maximum

The macro above can be replaced for integers with the following inline
function with no loss of efficiency:

       inline int
       max(int x, int y) {
          return (x > y ? x : y);
       }

### Be Careful of Side Effects

Macros should be used with caution because of the potential for error
when invoked with an expression that has side effects.

#### Example

       MAX(f(x),z++);

### Always Wrap the Expression in Parenthesis

When putting expressions in macros always wrap the expression in
parenthesis to avoid potential commutative operation ambiguity.

#### Example

    #define ADD(x,y) x + y

    must be written as

    #define ADD(x,y) ((x) + (y))

### Make Macro Names Unique

Like global variables macros can conflict with macros from other
packages.

1. Prepend macro names with package names.
2. Avoid simple and common names like MAX and MIN.

## Initialize all Variables

- You shall always initialize variables. Always. Every time. gcc with
    the flag -W may catch operations on uninitialized variables, but it
    may also not.

### Justification for Initializing Variables

- More problems than you can believe are eventually traced back to a
    pointer or variable left uninitialized.

## Short Functions

- Functions should limit themselves to a single page of code.

### Justification for Short Functions

- The idea is that the each method represents a technique for
    achieving a single objective.
- Most arguments of inefficiency turn out to be false in the long run.
- True function calls are slower than not, but there needs to a
    thought out decision (see premature optimization).

## Document Null Statements

Always document a null body for a for or while statement so that it is
clear that the null body is intentional and not missing code.

       while (*dest++ = *src++)

      {
          ;

       }

## Do Not Default If Test to Non-Zero

Do not default the test for non-zero, i.e.

       if (FAIL != f())

is better than

       if (f())

even though FAIL may have the value 0 which C considers to be false. An
explicit test will help you out later when somebody decides that a
failure return should be -1 instead of 0. Explicit comparison should be
used even if the comparison value will never change; e.g., **if
(!(bufsize % sizeof(int)))** should be written instead as **if ((bufsize
% sizeof(int)) == 0)** to reflect the numeric (not boolean) nature of
the test. A frequent trouble spot is using strcmp to test for string
equality, where the result should *never* *ever* be defaulted. The
preferred approach is to define a macro *STREQ*.

       #define STREQ(a, b) (strcmp((a), (b)) == 0)

Or better yet use an inline method:

       inline bool
       string_equal(char* a, char* b)
       {
          (strcmp(a, b) == 0) ? return true : return false;
          Or more compactly:
          return (strcmp(a, b) == 0);
       }

Note, this is just an example, you should really use the standard
library string type for doing the comparison.

The non-zero test is often defaulted for predicates and other functions
or expressions which meet the following restrictions:

- Returns 0 for false, nothing else.
- Is named so that the meaning of (say) a **true** return is
    absolutely obvious. Call a predicate is_valid(), not check_valid().

## Usually Avoid Embedded Assignments

There is a time and a place for embedded assignment statements. In some
constructs there is no better way to accomplish the results without
making the code bulkier and less readable.

       while (EOF != (c = getchar())) {
          process the character
       }

The ++ and -- operators count as assignment statements. So, for many
purposes, do functions with side effects. Using embedded assignment
statements to improve run-time performance is also possible. However,
one should consider the tradeoff between increased speed and decreased
maintainability that results when embedded assignments are used in
artificial places. For example,

       a = b + c;
       d = a + r;

should not be replaced by

       d = (a = b + c) + r;

even though the latter may save one cycle. In the long run the time
difference between the two will decrease as the optimizer gains
maturity, while the difference in ease of maintenance will increase as
the human memory of what's going on in the latter piece of code begins
to fade.
