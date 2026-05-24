# Names

## Include Units in Names

If a variable represents time, weight, or some other unit then include
the unit in the name so developers can more easily spot problems. For
example:

    uint32 mTimeoutMsecs;
    uint32 mMyWeightLbs;

Better yet is to make a variable into a class so bad conversions can be
caught.

## Class Names

-   Use upper case letters as word separators, lower case for the rest
    of a word
-   First character in a name is upper case
-   No underbars ('\_')

### Justification

-   Of all the different naming strategies many people found this one
    the best compromise.

### Example

       class NameOneTwo
      
       class Name
      

### **Class Names**

### 

-   Name the class after what it is. If you can't think of what it is
    that is a clue you have not thought through the design well enough.
-   Compound names of over three words are a clue your design may be
    confusing various entities in your system. Revisit your design. Try
    a CRC card session to see if your objects have more responsibilities
    than they should.
-   Avoid the temptation of bringing the name of the class a class
    derives from into the derived class's name. A class should stand on
    its own. It doesn't matter what it derives from.
-   Suffixes are sometimes helpful. For example, if your system uses
    agents then naming something DownloadAgent conveys real information.

## Class Library Names

-   Now that name spaces are becoming more widely implemented, name
    spaces should be used to prevent class name conflicts among
    libraries from different vendors and groups.
-   When not using name spaces, it's common to prevent class name
    clashes by prefixing class names with a unique string. Two
    characters is sufficient, but a longer length is fine.
-   It is strongly recommended to use namespaces

### Example

John Johnson's complete data structure library could use *JJ* as a
prefix, so classes would be:

       class JjLinkList
       {
       }

## Method Names

-   Use the same rule as for class names.

### Justification

-   Of all the different naming strategies many people found this one
    the best compromise.

### Example

       class NameOneTwo
       {
       public:
          int                   DoIt();
          void                  HandleError();
       }

### Method Names

-   Usually every method and function performs an action, so the name
    should make clear what it does: CheckForErrors() instead of
    ErrorCheck(), DumpDataToFile() instead of DataFile(). This will also
    make functions and data objects more distinguishable.

    Classes are often nouns. By making function names verbs and
    following other naming conventions programs can be read more
    naturally.

-   Suffixes are sometimes useful:

    -   *Max* - to mean the maximum value something can have.
    -   *Cnt* - the current count of a running count variable.
    -   *Key* - key value.

    For example: RetryMax to mean the maximum number of retries,
    RetryCnt to mean the current retry count.

-   Prefixes are sometimes useful:

    -   *Is* - to ask a question about something. Whenever someone sees
        *Is* they will know it's a question.
    -   *Get* - get a value.
    -   *Set* - set a value.

    For example: IsHitRetryLimit.

## Class Attribute Names

-   Attribute names should be prepended with the character 'a'.
-   After the 'a' use the same rules as for class names.
-   'a' always precedes other name modifiers like 'p' for pointer.

### Justification

-   Prepending 'a' prevents any conflict with method names. Often your
    methods and attribute names will be similar, especially for
    accessors.

### Example

       class NameOneTwo
       {
       public:
          int                   VarAbc();
          int                   ErrorNumber();
       private:
          int                   aVarAbc;
          int                   aErrorNumber;
          String*               apName;
       }

## Method Argument Names

-   The first character should be lower case.
-   All word beginnings after the first letter should be upper case as
    with class names.

### Justification

-   You can always tell which variables are passed in variables.
-   You can use names similar to class names without conflicting with
    class names.

### Example

       class NameOneTwo
       {
       public:
          int                   StartYourEngines(
                                   Engine& rSomeEngine, 
                                   Engine& rAnotherEngine);
       }

## C++ File Extensions

In short: Use the *.hh* extension for header files and *.cc* for source
files.

## C Function Names

-   In a C++ project there should be very few C functions.
-   For C functions use the GNU convention of all lower case letters
    with '\_' as the word delimiter.

### Justification

-   It makes C functions very different from any C++ related names.

### Example

       int
       some_bloody_function() {
       }

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

### No All Upper Case Abbreviations

-   When confronted with a situation where you could use an all upper
    case abbreviation instead use an initial upper case letter followed
    by all lower case letters. No matter what.

#### Justification

-   People seem to have very different intuitions when making names
    containing abbreviations. It's best to settle on one strategy so
    the names are absolutely predictable.

    Take for example *NetworkABCKey*. Notice how the C from ABC and K
    from key are confused. Some people don't mind this and others just
    hate it so you'll find different policies in different code so you
    never know what to call something.

#### Example

       class FluidOz             // NOT FluidOZ
       class NetworkAbcKey       // NOT NetworkABCKey

## Variable Names on the Stack

-   use all lower case letters
-   use '\_' as the word separator.

### Justification

-   With this approach the scope of the variable is clear in the code.
-   Now all variables look different and are identifiable in the code.

### Example

       int NameOneTwo::HandleError(int errorNumber) {
          int            error= OsErr();
          Time           time_of_error;
          ErrorProcessor error_processor;
       }

## Pointer Variables

-   pointers should be prepended by a 'p' in most cases
-   place the *\** close to variable name not pointer type

### Example

      String *pName= new String;

      String *pName, name, address; // note, only pName is a pointer.

## Reference Variables and Functions Returning References

-   References should be prepended with 'r'.
-   Const refs should not have 'r'.

### Justification

-   The difference between variable types is clarified.
-   It establishes the difference between a method returning a
    modifiable object and the same method name returning a
    non-modifiable object.

### Example

       class Test
       {
       public:
          void               DoSomething(StatusInfo& rStatus);

          StatusInfo&        rStatus();
          const StatusInfo&  Status() const;

       private:
          StatusInfo&        arStatus;
       }

## Global Variables

-   Global variables should be prepended with a 'g'.

### Justification

-   It's important to know the scope of a variable.

### Example

        Logger  gLog;
        Logger* gpLog;

## Global Constants

-   Global constants should be all caps with '\_' separators.

### Justification

It's tradition for global constants to named this way. You must be
careful to not conflict with other global *#define*s and enum labels.

### Example

        const int A_GLOBAL_CONSTANT= 5;

## Static Variables

-   Static variables may be prepended with 's'.

### Justification

-   It's important to know the scope of a variable.

### Example

       class Test
       {
       public:
       private:
          static StatusInfo msStatus;
       }

## Type Names

-   When possible for types based on native types make a typedef.
-   Typedef names should use the same naming policy as for a class with
    the word *Type* appended.

### Justification

-   Of all the different naming strategies many people found this one
    the best compromise.
-   Types are things so should use upper case letters. *Type* is
    appended to make it clear this is not a class.

### Example

       typedef uint16  ModuleType;
       typedef uint32  SystemType;

## Enum Names

### Labels All Upper Case with '\_' Word Separators

This is the standard rule for enum labels.

#### Example

       enum PinStateType {
          PIN_OFF,
          PIN_ON
       };

### Enums as Constants without Class Scoping

Sometimes people use enums as constants. When an enum is not embedded in
a class make sure you use some sort of differentiating name before the
label so as to prevent name clashes.

#### Example

       enum PinStateType  {          If PIN was not prepended a conflict 
                                   would occur as OFF and ON are probably
          PIN_OFF,                  already defined.
          PIN_ON
       };

### Enums with Class Scoping

Just name the enum items what you wish and always qualify with the class
name: Aclass::PIN_OFF.

### Make a Label for an Error State

It's often useful to be able to say an enum is not in any of its
*valid* states. Make a label for an uninitialized or error state. Make
it the first label if possible.

#### Example

    enum { STATE_ERR,  STATE_OPEN, STATE_RUNNING, STATE_DYING};

## #define and Macro Names

-   Put #defines and macros in all upper using '\_' separators.

### Justification

This makes it very clear that the value is not alterable and in the case
of macros, makes it clear that you are using a construct that requires
care.

Some subtle errors can occur when macro names and enum labels use the
same name.

### Example

    #define MAX(a,b) blah
    #define IS_ERR(err) blah

