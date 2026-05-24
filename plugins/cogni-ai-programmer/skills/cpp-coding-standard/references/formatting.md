# Formatting

## Braces *{}* Policy

### Brace Placement

Of the three major brace placement strategies the recommended one is
here:

-   Traditional Unix policy of placing the initial brace on the same
    line as the keyword and the trailing brace inline on its own line
    with the keyword:

           if (condition) {      while (condition) {
              ...                   ...
           }                     }

### When Braces are Needed

All if, while and do statements must either have braces or be on a
single line.

#### Always Uses Braces Form

All if, while and do statements require braces even if there is only a
single statement within the braces. For example:

    if (1 == somevalue) {
       somevalue = 2;
    }

#### Justification

It ensures that when someone adds a line of code later there are already
braces and they don't forget. It provides a more consistent look. This
doesn't affect execution speed. It's easy to do.

### One Line Form

    if (1 == somevalue) somevalue = 2;

#### Justification

It provides safety when adding new lines while maintainng a compact
readable form.

### Add Comments to Closing Braces

Adding a comment to closing braces can help when you are reading code
because you don't have to find the begin brace to know what is going
on.

    while(1) {
       if (valid) {
      
       } // if valid
       else {
       } // not valid

    } // end forever

## Parens *()* with Key Words and Functions Policy

-   Do not put parens next to keywords. Put a space between.
-   Do put parens next to function names.
-   Do not use parens in return statements when it's not necessary.

### Justification

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

-   Lines should not exceed 78 characters.

### Justification

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

-   Falling through a case statement into the next case statement shall
    be permitted as long as a comment is included.
-   The *default* case should always be present and trigger an error if
    it should not be reached, yet is reached.
-   If you need to create variables put all the code in a block.

### Example

       switch (...)
       {
          case 1:
             ...
          // FALL THROUGH

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

-   It may bypass the test condition
-   It may bypass the increment/decrement expression

Consider the following example where both problems occur:

    while (TRUE) {
       ...
       // A lot of code
       ...
       if (/* some condition */) {
          continue;
       }
       ...
       // A lot of code 
       ...
       if ( i++ > STOP_VALUE) break;
    }

Note: \"A lot of code\" is necessary in order that the problem cannot be
caught easily by the programmer.

From the above example, a further rule may be given: Mixing continue
with break in the same loop is a sure way to disaster.

## ?:

The trouble is people usually try and stuff too much code in between the
*?* and *:*. Here are a couple of clarity rules to follow:

-   Put the condition in parens so as to set it off from other code
-   If possible, the actions for the test should be simple functions.
-   Put the action for the then and else statement on a separate line
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
    char **a = 0;  // add doc
    char  *x = 0;  // add doc

The reasons are:

1.  Documentation can be added for the variable on the line.
2.  It's clear that the variables are initialized.
3.  Declarations are clear which reduces the probablity of declaring a
    pointer when you meant to declare just a char.

## Alignment of Declaration Blocks

-   Block of declarations should be aligned.

### Justification

-   Clarity.
-   Similarly blocks of initialization of variables should be tabulated.
-   The '&' and '\*' tokens should be adjacent to the the name, not the
    type.

### Example

       DWORD       aDword
       DWORD      *apDword
       char       *apChar
       char        aChar

       aDword   = 0;
       apDword  = NULL;
       apChar   = NULL;
       aChar    = 0;

