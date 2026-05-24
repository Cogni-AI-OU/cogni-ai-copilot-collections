# Miscellaneous

## General advice

This section contains some miscellaneous do's and don'ts.

- Don't use floating-point variables where discrete values are
    needed. Using a float for a loop counter is a great way to shoot
    yourself in the foot. Always test floating-point numbers as \<= or
    \>=, never use an exact comparison (== or !=).

- Compilers have bugs. Common trouble spots include structure
    assignment and bit fields. You cannot generally predict which bugs a
    compiler has. You could write a program that avoids all constructs
    that are known broken on all compilers. You won't be able to write
    anything useful, you might still encounter bugs, and the compiler
    might get fixed in the meanwhile. Thus, you should write
    \`\`around'' compiler bugs only when you are forced to use a
    particular buggy compiler.

- Do not rely on automatic beautifiers. The main person who benefits
    from good program style is the programmer him/herself, and
    especially in the early design of handwritten algorithms or
    pseudo-code. Automatic beautifiers can only be applied to complete,
    syntactically correct programs and hence are not available when the
    need for attention to white space and indentation is greatest.
    Programmers can do a better job of making clear the complete visual
    layout of a function or file, with the normal attention to detail of
    a careful programmer (in other words, some of the visual layout is
    dictated by intent rather than syntax and beautifiers cannot read
    minds). Sloppy programmers should learn to be careful programmers
    instead of relying on a beautifier to make their code readable.
    Finally, since beautifiers are non-trivial programs that must parse
    the source, a sophisticated beautifier is not worth the benefits
    gained by such a program. Beautifiers are best for gross formatting
    of machine-generated code.

- Accidental omission of the second \`\`='' of the logical compare
    is a problem. The following is confusing and prone to error.

                if (abool= bbool) { ... }

    Does the programmer really mean assignment here? Often yes, but
    usually no. The solution is to just not do it, an inverse Nike
    philosophy. Instead use explicit tests and avoid assignment with an
    implicit test. The recommended form is to do the assignment before
    doing the test:

               abool= bbool;
               if (abool) { ... }

- Modern compilers will put variables in registers automatically. Use
    the register sparingly to indicate the variables that you think are
    most critical. In extreme cases, mark the 2-4 most critical values
    as register and mark the rest as REGISTER. The latter can be
    #defined to register on those machines with many registers.

## Be Const Correct

C provides the *const* key word to allow passing as parameters objects
that cannot change to indicate when a method doesn't modify its object.
Using const in all the right places is called "const correctness."
It's hard at first, but using const really tightens up your coding
style. Const correctness grows on you.

## Use #if Not #ifdef

Use #if MACRO not #ifdef MACRO. Someone might write code like:

    #ifdef DEBUG
            temporary_debugger_break();
    #endif

Someone else might compile the code with turned-off debug info like:

    cc -c lurker.cc -DDEBUG=0

Always use #if, if you have to use the preprocessor. This works fine, and
does the right thing, even if DEBUG is not defined at all (!)

    #if DEBUG
            temporary_debugger_break();
    #endif

If you really need to test whether a symbol is defined or not, test it
with the defined() construct, which allows you to add more things later
to the conditional without editing text that's already in the program:

    #if !defined(USER_NAME)
     #define USER_NAME "john smith"
    #endif

## Commenting Out Large Code Blocks

Sometimes large blocks of code need to be commented out for testing.

### Using #if 0

The easiest way to do this is with an #if 0 block:

       void
       example()
       {
          great looking code

          #if 0
          lots of code
          #endif

          more code
        }

You can't use **/\*\*/** style comments because comments can't contain
comments and surely a large block of your code will contain a comment,
won't it?

Don't use #ifdef as someone can unknowingly trigger ifdefs from the
compiler command line. #if 0 is that one day later you or anyone else
has no idea why this code is commented out. Is it because a feature
has been dropped? Is it because it was buggy? It didn't compile? Can it
be added back? It's a mystery.

### Use Descriptive Macro Names Instead of #if 0

    #if NOT_YET_IMPLEMENTED

    #if OBSOLETE

    #if TEMP_DISABLED

### Add a Comment to Document Why

Add a short comment explaining why it is not implemented, obsolete or
temporarily disabled.

     

## File Extensions

In short: Use the *.h* extension for header files and *.c* for source
files.

## No Data Definitions in Header Files

Do not put data definitions in header files. for example:

    /*
     * aheader.h
     */
    int x = 0;

1. It's bad magic to have space consuming code silently inserted
    through the innocent use of header files.
2. It's not common practice to define variables in the header file so
    it will not occur to developers to look for this when there are
    problems.
3. Consider defining the variable once in a .c file and use an extern
    statement to reference it.

## Mixing C and C++

In order to be backward compatible with dumb linkers C++'s link time
type safety is implemented by encoding type information in link symbols,
a process called *name mangling*. This creates a problem when linking to
C code as C function names are not mangled. When calling a C function
from C++ the function name will be mangled unless you turn it off. Name
mangling is turned off with the *extern "C"* syntax. If you want to
create a C function in C++ you must wrap it with the above syntax. If
you want to call a C function in a C library from C++ you must wrap in
the above syntax. Here are some examples:

### Calling C Functions from C++

    extern "C" int strncpy(...);
    extern "C" int my_great_function();
    extern "C"
    {
       int strncpy(...);
       int my_great_function();
    };

### Creating a C Function in C++

    extern "C" void
    a_c_function_in_cplusplus(int a)
    {
    }

### *\_\_cplusplus* Preprocessor Directive

If you have code that must compile in a C and C++ environment then you
must use the *\_\_cplusplus* preprocessor directive. For example:

    #ifdef __cplusplus

    extern "C" some_function();

    #else

    extern some_function();

    #endif

## No Magic Numbers

A magic number is a bare naked number used in source code. It's magic
because no-one has a clue what it means including the author inside 3
months. For example:

    if      (22 == foo) { start_thermo_nuclear_war(); }
    else if (19 == foo) { refund_lotso_money(); }
    else if (16 == foo) { infinite_loop(); }
    else                { cry_cause_im_lost(); }

In the above example what do 22 and 19 mean? If there was a number
change or the numbers were just plain wrong how would you know? Instead
of magic numbers use a real name that means something. You can use
*#define* or constants or enums as names. Which one is a design choice.
For example:

    #define   PRESIDENT_WENT_CRAZY  (22)
    const int WE_GOOFED= 19;
    enum  {
       THEY_DIDNT_PAY= 16
    };

    if      (PRESIDENT_WENT_CRAZY == foo) { start_thermo_nuclear_war(); }
    else if (WE_GOOFED            == foo) { refund_lotso_money(); }
    else if (THEY_DIDNT_PAY       == foo) { infinite_loop(); }
    else                                  { happy_days_i_know_why_im_here(); }

Now isn't that better? The const and enum options are preferable
because when debugging the debugger has enough information to display
both the value and the label. The #define option just shows up as a
number in the debugger which is very inconvenient. The const option has
the downside of allocating memory. Only you know if this matters for
your application.

## Error Return Check Policy

- Check every system call for an error return, unless you know you
    wish to ignore errors. For example, *printf* returns an error code
    but rarely would you check for its return code. In which case you
    can cast the return to **(void)** if you really care.
- Include the system error text for every system error message.
- Check every call to malloc or realloc unless you know your versions
    of these calls do the right thing. You might want to have your own
    wrapper for these calls, including new, so you can do the right
    thing always and developers don't have to make memory checks
    everywhere.
