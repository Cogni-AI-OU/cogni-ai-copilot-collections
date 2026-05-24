# Names

## Make Names Fit

Names are the heart of programming. In the past people believed knowing
someone's true name gave them magical power over that person. If you
can think up the true name for something, you give yourself and the
people coming after power over the code. Don't laugh!

A name is the result of a long deep thought process about the ecology it
lives in. Only a programmer who understands the system as a whole can
create a name that \"fits\" with the system. If the name is appropriate
everything fits together naturally, relationships are clear, meaning is
derivable, and reasoning from common human expectations works as
expected.

If you find all your names could be Thing and DoIt then you should
probably revisit your design.

## Function Names

-   Usually every function performs an action, so the name should make
    clear what it does: check_for_errors() instead of error_check(),
    dump_data_to_file() instead of data_file(). This will also make
    functions and data objects more distinguishable.

    Structs are often nouns. By making function names verbs and
    following other naming conventions programs can be read more
    naturally.

-   Suffixes are sometimes useful:

    -   *max* - to mean the maximum value something can have.
    -   *cnt* - the current count of a running count variable.
    -   *key* - key value.

    For example: retry_max to mean the maximum number of retries,
    retry_cnt to mean the current retry count.

-   Prefixes are sometimes useful:

    -   *is* - to ask a question about something. Whenever someone sees
        *Is* they will know it's a question.
    -   *get* - get a value.
    -   *set* - set a value.

    For example: is_hit_retry_limit.

## Include Units in Names

If a variable represents time, weight, or some other unit then include
the unit in the name so developers can more easily spot problems. For
example:

    uint32 timeout_msecs;
    uint32 my_weight_lbs;

## Structure Names

-   Use underbars ('\_') to separate name components
-   When declaring variables in structures, declare them organized by
    use in a manner to attempt to minimize memory wastage because of
    compiler alignment issues, then by size, and then by alphabetical
    order. E.g, don't use \`\`int a; char \*b; int c; char \*d''; use
    \`\`int a; int b; char \*c; char \*d''. Each variable gets its own
    type and line, although an exception can be made when declaring
    bitfields (to clarify that it's part of the one bitfield). Note
    that the use of bitfields in general is discouraged. Major
    structures should be declared at the top of the file in which they
    are used, or in separate header files, if they are used in multiple
    source files. Use of the structures should be by separate
    declarations and should be \"extern\" if they are declared in a
    header file. It may be useful to use a meaningful prefix for each
    member name. E.g, for \`\`struct softc'' the prefix could be
    \`\`sc\_''.

### Example

       
    struct foo {
        struct foo *next;   /* List of active foo */
        struct mumble amumble;  /* Comment for mumble */
        int bar;
        unsigned int baz:1, /* Bitfield; line up entries if desired */
                 fuz:5,
                 zap:2;
        uint8_t flag;
    };
    struct foo *foohead;        /* Head of global foo list */

## Variable Names on the Stack

-   use all lower case letters
-   use '\_' as the word separator.

### Justification

-   With this approach the scope of the variable is clear in the code.
-   Now all variables look different and are identifiable in the code.

### Example

       
       int handle_error (int error_number) {
          int            error= OsErr();
          Time           time_of_error;
          ErrorProcessor error_processor;
       }

## Pointer Variables

-   place the *\** close to the variable name not pointer type

### Example

      char *name= NULL;

      char *name, address; 

## Global Variables

-   Global variables should be prepended with a 'g\_'.
-   Global variables should be avoided whenever possible.

### Justification

-   It's important to know the scope of a variable.

### Example

        Logger  g_log;
        Logger* g_plog;

## Global Constants

-   Global constants should be all caps with '\_' separators.

### Justification

It's tradition for global constants to named this way. You must be
careful to not conflict with other global *#define*s and enum labels.

### Example

        const int A_GLOBAL_CONSTANT= 5;

## #define and Macro Names

-   Put #defines and macros in all upper using '\_' separators. Macros
    are capitalized, parenthesized, and should avoid side-effects.
    Spacing before and after the macro name may be any whitespace,
    though use of TABs should be consistent through a file. If they are
    an inline expansion of a function, the function is defined all in
    lowercase, the macro has the same name all in uppercase. If the
    macro is an expression, wrap the expression in parenthesis. If the
    macro is more than a single statement, use \`\`do { \... } while
    (0)'', so that a trailing semicolon works. Right-justify the
    backslashes; it makes it easier to read.

### Justification

This makes it very clear that the value is not alterable and in the case
of macros, makes it clear that you are using a construct that requires
care.

Some subtle errors can occur when macro names and enum labels use the
same name.

### Example

    #define MAX(a,b) blah
    #define IS_ERR(err) blah
    #define MACRO(v, w, x, y)                       \
    do {                                    \
        v = (x) + (y);                          \
        w = (y) + 2;                            \
    } while (0)

## Enum Names

### Labels All Upper Case with '\_' Word Separators

This is the standard rule for enum labels. No comma on the last element.

#### Example

       enum PinStateType {
          PIN_OFF,
          PIN_ON
       };

### Make a Label for an Error State

It's often useful to be able to say an enum is not in any of its
*valid* states. Make a label for an uninitialized or error state. Make
it the first label if possible.

#### Example

    enum { STATE_ERR,  STATE_OPEN, STATE_RUNNING, STATE_DYING};

