# Java Coding Standard

## 1 Introduction
### 1.1 Layout of the Recommendations. 
The recommendations are grouped by topic and each recommendation is numbered to make it easier to refer to during reviews. 
Layout for the recommendations is as follows: 

- Guideline short description 
```
Example if applicable 
```
Motivation, background and additional information. 


The motivation section is important. Coding standards and guidelines tend to start "religious wars", and it is important to state the background for the recommendation. 
### 1.2 Recommendation Importance 
In the guideline sections the terms must, should and can have special meaning. A must requirement must be followed, a should is a strong recommendation, and a can is a general guideline. 

## 2 General Recommendations 
- Any violation to the guide is allowed if it enhances readability. 
The main goal of the recommendation is to improve readability and thereby the understanding and the maintainability and general quality of the code. It is impossible to cover all the specific cases in a general guide and the programmer should be flexible. 

## 3 Naming Conventions 
### 3.1 General Naming Conventions 
- Names representing packages should be in all lower case. 
```
mypackage, com.company.application.ui 
```
Package naming convention used by Sun for the Java core packages. The initial package name representing the domain name must be in lower case. 

- Names representing types must be nouns and written in mixed case starting with upper case. 
```
Line, AudioSystem 
```
Common practice in the Java development community and also the type naming convention used by Sun for the Java core packages. 

- Variable names must be in mixed case starting with lower case. 
```
line, audioSystem 
```
Common practice in the Java development community and also the naming convention for variables used by Sun for the Java core packages. Makes variables easy to distinguish from types, and effectively resolves potential naming collision as in the declaration Line line; 

- Names representing constants (final variables) must be all uppercase using underscore to separate words. 
```
MAX_ITERATIONS, COLOR_RED 
```
Common practice in the Java development community and also the naming convention used by Sun for the Java core packages. 
In general, the use of such constants should be minimized. In many cases implementing the value as a method is a better choice: 
```
  int getMaxIterations() // NOT: MAX_ITERATIONS = 25
  {
    return 25;
  }
```
This form is both easier to read, and it ensures a uniform interface towards class values. 
- Names representing methods must be verbs and written in mixed case starting with lower case. 
```
getName(), computeTotalWidth() 
```
Common practice in the Java development community and also the naming convention used by Sun for the Java core packages. This is identical to variable names, but methods in Java are already distinguishable from variables by their specific form. 
- Abbreviations and acronyms should not be uppercase when used as name. 
```
exportHtmlSource(); // NOT: exportHTMLSource(); 
openDvdPlayer(); // NOT: openDVDPlayer(); 
```
Using all uppercase for the base name will give conflicts with the naming conventions given above. A variable of this type whould have to be named dVD, hTML etc. which obviously is not very readable. Another problem is illustrated in the examples above; When the name is connected to another, the readability is seriously reduced; The word following the acronym does not stand out as it should. 

- Generic variables should have the same name as their type. 
```
void setTopic(Topic topic) 
// NOT: void setTopic(Topic value) 
// NOT: void setTopic(Topic aTopic) 
// NOT: void setTopic(Topic t) 
```
Reduce complexity by reducing the number of terms and names used. Also makes it easy to deduce the type given a variable name only. 
If for some reason this convention doesn't seem to fit it is a strong indication that the type name is badly chosen. 

Non-generic variables have a role. These variables can often be named by combining role and type: 
```
  Point  startingPoint, centerPoint;
  Name   loginName;
```
- All names should be written in English. 

English is the preferred language for international development. 


- The name of the object is implicit, and should be avoided in a method name. 
```
line.getLength(); // NOT: line.getLineLength(); 
```
The latter might seem natural in the class declaration, but proves superfluous in use, as shown in the example. 

### 3.2 Specific Naming Conventions 

- The terms get/set must be used where an attribute is accessed directly. 
```
employee.getName(); 
employee.setName(name); 
matrix.getElement(2, 4); 
matrix.setElement(2, 4, value); 
```
Common practice in the Java community and the convention used by Sun for the Java core packages. 
- is prefix should be used for boolean variables and methods. 
```
isSet, isVisible, isFinished, isFound, isOpen 
```
This is the naming convention for boolean methods and variables used by Sun for the Java core packages. 
Using the is prefix solves a common problem of choosing bad boolean names like status or flag. isStatus or isFlag simply doesn't fit, and the programmer is forced to chose more meaningful names. 
Setter methods for boolean variables must have set prefix as in: 
```
  boolean isFound();
  void setFound(boolean isFound);
```
- The term compute can be used in methods where something is computed. 
```
valueSet.computeAverage(); matrix.computeInverse() 
```
Give the reader the immediate clue that this is a potential time consuming operation, and if used repeatedly, he might consider caching the result. Consistent use of the term enhances readability. 
- The term find can be used in methods where something is looked up. 
```
vertex.findNearestVertex(); matrix.findSmallestElement(); node.findShortestPath(Node destinationNode); 
```
Give the reader the immediate clue that this is a simple look up method with a minimum of computations involved. Consistent use of the term enhances readability. 
- JFC (Java Swing) variables should be suffixed by the element type. 
```
widthScale, nameTextField, leftScrollbar, mainPanel, fileToggle, minLabel, printerDialog 
```
Enhances readability since the name gives the user an immediate clue of the type of the variable and thereby the available resources of the object. 
- Plural form should be used on names representing a collection of objects. 
```
Collection<Point> points; int[] values; 
```
Enhances readability since the name gives the user an immediate clue of the type of the variable and the operations that can be performed on its elements. 
- No suffix should be used for variables representing an entity number. 
```
tableNo, employeeNo 
```
The notation is taken from mathematics where it is an established convention for indicating an entity number. 
An elegant alternative is to prefix such variables with an i: iTable, iEmployee. This effectively makes them named iterators. 
- Complement names must be used for complement entities [1]. 
```
get/set, add/remove, create/destroy, start/stop, insert/delete, increment/decrement, old/new, begin/end, first/last, up/down, min/max, next/previous, old/new, open/close, show/hide, suspend/resume, etc. 
```
Reduce complexity by symmetry. 
- Abbreviations in names should be avoided.
```
computeAverage();                 // NOT: compAvg(); 
ActionEvent event;                 // NOT: ActionEvent e; 
catch (Exception exception) { // NOT: catch (Exception e) { 
```
There are two types of words to consider. First are the common words listed in a language dictionary. These must never be abbreviated. Never write: 
```
cmd   instead of   command
comp  instead of   compute
cp    instead of   copy
e     instead of   exception
init  instead of   initialize
pt    instead of   point
etc. 
```
Then there are domain specific phrases that are more naturally known through their acronym or abbreviations. These phrases should be kept abbreviated. Never write: 
```
HypertextMarkupLanguage  instead of   html
CentralProcessingUnit    instead of   cpu
PriceEarningRatio        instead of   pe
etc. 
```
- Negated boolean variable names must be avoided. 
```
bool isError; // NOT: isNoError bool isFound; // NOT: isNotFound 
```
The problem arise when the logical not operator is used and double negative arises. It is not immediately apparent what !isNotError means. 
- Associated constants (final variables) should be prefixed by a common type name. 
```
final int COLOR_RED = 1; final int COLOR_GREEN = 2; final int COLOR_BLUE = 3; 
```
This indicates that the constants belong together, and what concept the constants represents. 
An alternative to this approach is to put the constants inside an interface effectively prefixing their names with the name of the interface: 
```
  interface Color
  {
    final int RED   = 1;
    final int GREEN = 2;
    final int BLUE  = 3;
  }
```
- Exception classes should be suffixed with Exception. 
```
class AccessException extends Exception { : } 
```
Exception classes are really not part of the main design of the program, and naming them like this makes them stand out relative to the other classes. This standard is followed by Sun in the basic Java library. 
- Default interface implementations can be prefixed by Default. 
```
class DefaultTableCellRenderer implements TableCellRenderer { : } 
```
It is not uncommon to create a simplistic class implementation of an interface providing default behaviour to the interface methods. The convention of prefixing these classes by Default has been adopted by Sun for the Java library. 
- Singleton classes should return their sole instance through method getInstance. 
```
class UnitManager {
 private final static UnitManager instance_ = new UnitManager();
 private UnitManager() { ... }
 public static UnitManager getInstance() // NOT: get() or instance() or unitManager() etc. 
   { return instance_; } 
} 
```
Common practice in the Java community though not consistently followed by Sun in the JDK. The above layout is the preferred pattern. 
- Classes that creates instances on behalf of others (factories) can do so through method new[ClassName] 
```
class PointFactory { public Point newPoint(...) { ... } } 
```
Indicates that the instance is created by new inside the factory method and that the construct is a controlled replacement of new Point(). 
- Functions (methods returning an object) should be named after what they return and procedures (void methods) after what they do. 

Increase readability. Makes it clear what the unit should do and especially all the things it is not supposed to do. This again makes it easier to keep the code clean of side effects. 


## 4 Files 
- Java source files should have the extension .java. 
```
Point.java 
```
Enforced by the Java tools. 
- Classes should be declared in individual files with the file name matching the class name. Secondary private classes can be declared as inner classes and reside in the file of the class they belong to. 
Enforced by the Java tools. 

- Special characters like TAB and page break must be avoided. 
These characters are bound to cause problem for editors, printers, terminal emulators or debuggers when used in a multi-programmer, multi-platform environment. 

- The incompleteness of split lines must be made obvious [1]. 
```
totalSum = a + b + c + 
                 d + e; 
method(param1, param2, 
            param3); 
setText ("Long line split" + 
             "into two parts."); 
for (int tableNo = 0; tableNo < nTables; 
      tableNo += tableStep) { ... } 
```
Split lines occurs when a statement exceed the 80 column limit given above. It is difficult to give rigid rules for how lines should be split, but the examples above should give a general hint. 
In general: 
```
•	Break after a comma. 
•	Break after an operator.
•	Align the new line with the beginning of the expression on the previous line.
```

## 5 Statements 
### 5.1 Package and Import Statements 
- The package statement must be the first statement of the file. All files should belong to a specific package. 
The package statement location is enforced by the Java language. Letting all files belong to an actual (rather than the Java default) package enforces Java language object oriented programming techniques. 

- The import statements must follow the package statement. import statements should be sorted with the most fundamental packages first, and grouped with associated packages together and one blank line between groups. 
```
import java.util.StringTokenizer;  
import java.util.TreeMap;
import java.util.TreeSet;
                                             
import javax.servlet.http.HttpServletRequest;

import org.apache.commons.beanutils.BeanMap;
import org.springframework.util.StringUtils;
```
The import statement location is enforced by the Java language. The sorting makes it simple to browse the list when there are many imports, and it makes it easy to determine the dependiencies of the present package The grouping reduce complexity by collapsing related information into a common unit. 

- Imported classes should always be listed explicitly. 
```
import java.util.List;                 // NOT: import java.util.*; 
import java.util.ArrayList; 
import java.util.HashSet; 
Importing classes explicitly gives an excellent documentation value for the class at hand and makes the class easier to comprehend and maintain. 
```
Appropriate tools should be used in order to always keep the import list minimal and up to date. 

### 5.2 Classes and Interfaces
- Class and Interface declarations should be organized in the following manner: 
```
1.	Class/Interface documentation. 
2.	class or interface statement. 
3.	Class (static) variables in the order public, protected, package (no access modifier), private.
4.	Instance variables in the order public, protected, package (no access modifier), private.
5.	Constructors. 
6.	Methods (no specific order). 
/* javadoc
 *
 */
public class Test{
    public static String var1;
    protected static String var2;
    public int x;
    private int y;
    public Test(){
    }
    
    public someMethod(){
    }
}
```
Reduce complexity by making the location of each class element predictable. 

### 5.3 Methods 
- Method modifiers should be given in the following order:
```
<access> static abstract synchronized <unusual> final native
```
The <access> modifier (if present) must be the first modifier. 
```
public static double square(double a); // NOT: static public double square(double a); 
```
<access> is one of public, protected or private while <unusual> includes volatile and transient. The most important lesson here is to keep the access modifier as the first modifier. Of the possible modifiers, this is by far the most important, and it must stand out in the method declaration. For the other modifiers, the order is less important, but it make sense to have a fixed convention. 
### 5.4 Types
- Type conversions must always be done explicitly. Never rely on implicit type conversion. 
```
floatValue = (int) intValue; // NOT: floatValue = intValue; 
```
By this, the programmer indicates that he is aware of the different types involved and that the mix is intentional. 

- Array specifiers must be attached to the type not the variable. 
```
int[] a = new int[20]; // NOT: int a[] = new int[20] 
```
The arrayness is a feature of the base type, not the variable. It is not known why Sun allows both forms. 
### 5.5 Variables 
- Variables should be initialized where they are declared and they should be declared in the smallest scope possible. 
This ensures that variables are valid at any time. Sometimes it is impossible to initialize a variable to a valid value where it is declared. In these cases it should be left uninitialized rather than initialized to some phony value. 

- Variables must never have dual meaning. 
Enhances readability by ensuring all concepts are represented uniquely. Reduce chance of error by side effects. 

- Class variables should never be declared public. 
The concept of Java information hiding and encapsulation is violated by public variables. Use private variables and access functions instead. One exception to this rule is when the class is essentially a data structure, with no behavior (equivalent to a C++ struct). In this case it is appropriate to make the class' instance variables public [2]. 

- Arrays should be declared with their brackets next to the type. 
```
double[] vertex; // NOT: double vertex[]; 
int[] count; // NOT: int count[]; 
public static void main(String[] arguments) 
public double[] computeVertex() 
```
The reason for is twofold. First, the array-ness is a feature of the class, not the variable. Second, when returning an array from a method, it is not possible to have the brackets with other than the type (as shown in the last example). 

- Variables should be kept alive for as short a time as possible. 
Keeping the operations on a variable within a small scope, it is easier to control the effects and side effects of the variable. 

### 5.6 Loops
- Only loop control statements must be included in the for() construction. 
```
sum = 0; 
for (i = 0; i < 100; i++)                // NOT: for (i = 0, sum = 0; i < 100; i++) 
    sum += value[i];                     //  sum += value[i]; 
```
Increase maintainability and readability. Make a clear distinction of what controls and what is contained in the loop. 

- Loop variables should be initialized immediately before the loop. 
```
isDone = false;    // NOT: bool isDone = false; 
while (!isDone) { // : 
     :                    // while (!isDone) { 
}                         // : 
                          // } 
```

- The use of do-while loops can be avoided. 
do-while loops are less readable than ordinary while loops and for loops since the conditional is at the bottom of the loop. The reader must scan the entire loop in order to understand the scope of the loop. 
In addition, do-while loops are not needed. Any do-while loop can easily be rewritten into a while loop or a for loop. Reducing the number of constructs used enhance readbility. 

- The use of break and continue in loops should be avoided. 
These statements should only be used if they prove to give higher readability than their structured counterparts. 

### 5.7 Conditionals 
- Complex conditional expressions must be avoided. Introduce temporary boolean variables instead [1]. 
```
bool isFinished = (elementNo < 0) || (elementNo > maxElement); 
bool isRepeatedEntry = elementNo == lastElement; 
if (isFinished || isRepeatedEntry) { : } 

// NOT: if ((elementNo < 0) || (elementNo > maxElement)|| elementNo == lastElement) { : } 
```
By assigning boolean variables to expressions, the program gets automatic documentation. The construction will be easier to read, debug and maintain. 
- The nominal case should be put in the if-part and the exception in the else-part of an if statement [1]. 
```
boolean isOk = readFile(fileName); 
if (isOk) {
 : 
} 
else {
 : 
} 
```
Makes sure that the exceptions does not obscure the normal path of execution. This is important for both the readability and performance. 

- The conditional should be put on a separate line. 
```
if (isDone)                    // NOT: if (isDone) doCleanup(); 
   doCleanup(); 
```
This is for debugging purposes. When writing on a single line, it is not apparent whether the test is really true or not. 

- Executable statements in conditionals must be avoided. 
```
InputStream stream = File.open(fileName, "w"); 
if (stream != null) {
 : 
} 
// NOT: if (File.open(fileName, "w") != null)) { : } 
```
Conditionals with executable statements are simply very difficult to read. This is especially true for programmers new to Java. 

### 5.8 Miscellaneous
- The use of magic numbers in the code should be avoided. Number can be considered declared as named constants instead. 
```
private static final int TEAM_SIZE = 11;
 : 
Player[] players = new Player[TEAM_SIZE]; 
// NOT: Player[] players = new Player[11]; 
```
If the number does not have an obvious meaning by itself, the readability is enhanced by introducing a named constant instead. 

- Floating point constants should always be written with decimal point and at least one decimal. 
```
double total = 0.0; // NOT: double total = 0; 
double speed = 3.0e8; // NOT: double speed = 3e8; 
double sum;
: 
sum = (a + b) * 10.0; 
```
This emphasize the different nature of integer and floating point numbers. Mathematically the two model completely different and non-compatible concepts. 
Also, as in the last example above, it emphasize the type of the assigned variable (sum) at a point in the code where this might not be evident. 
- Floating point constants should always be written with a digit before the decimal point. 
```
double total = 0.5; // NOT: double total = .5; 
```
The number and expression system in Java is borrowed from mathematics and one should adhere to mathematical conventions for syntax wherever possible. Also, 0.5 is a lot more readable than .5; There is no way it can be mixed with the integer 5. 
- Static variables or methods must always be refered to through the class name and never through an instance variable. 
```
Thread.sleep(1000); // NOT: thread.sleep(1000); 
```
This emphasize that the element references is static and independent of any particular instance. For the same reason the class name should also be included when a variable or method is accessed from within the same class. 

## 6 Layout and Comments 
### 6.1 Layout 
- Basic indentation should be 4 spaces (1 tab). 
```
for (i = 0; i < nElements; i++)
  a[i] = 0; 
```
Indentation is used to emphasize the logical structure of the code. Indentation of 1 is to small to acheive this. Indentation larger than 4 makes deeply nested code difficult to read and increase the chance that the lines must be split. Choosing between indentation of 2, 3 and 4; 2 and 4 are the more common, and 2 chosen to reduce the chance of splitting code lines. Note that the Sun recommendation on this point is 4. 

- Block layout should be as illustrated in example 1 below (recommended) or example 2, and must not be as shown in example 3. Class, Interface and method blocks should use the block layout of example 2. 
```
for(…){
    xxxx
    xxxx
}
```
```
for(…)
{
    xxx
    xxx
}	
```
```
//not
for(…)
   {
       xxx
       xxx
    }
```
Example 3 introduce an extra indentation level which doesn't emphasize the logical structure of the code as clearly as example 1 and 2. 

- The if-else class of statements should have the following form: 
```
if (condition) {
  statements;
}
```
```
if (condition) {
  statements;
}
else {
  statements;
}
```
```
if (condition) {
  statements;
}
else if (condition) {
  statements;
}
else {
  statements;
}
```
```
if (condition) {
  statements;
} else {
  statements;
}
```
This follows partly from the general block rule above. However, it might be discussed if an else clause should be on the same line as the closing bracket of the previous if or else clause: 
```
  if (condition) {
    statements;
  } else {
    statements;
  }
```
This is equivalent to the Sun recommendation. The chosen approach is considered better in the way that each part of the if-else statement is written on separate lines of the file. This should make it easier to manipulate the statement, for instance when moving else clauses around. 


- The for statement should have the following form: 
```
for (initialization; condition; update) {
 statements; 
} 
```
This follows from the general block rule above. 

- The while statement should have the following form: 
```
while (condition) {
  statements;
}
```
This follows from the general block rule above. 

- The do-while statement should have the following form: 
```
do {
  statements;
} while (condition);
```
This follows from the general block rule above. 

- The switch statement should have the following form: 
```
switch (condition) {
    case ABC :
        statements;
        // Fallthrough

    case DEF :
        statements;
        break;

    default :
        statements;
        break;
}
```
This differs slightly from the Sun recommendation both in indentation and spacing. In particular, each case keyword is indented relative to the switch statement as a whole. This makes the entire switch statement stand out. Note also the extra space before the : character. The explicit Fallthrough comment should be included whenever there is a case statement without a break statement. Leaving the break out is a common error, and it must be made clear that it is intentional when it is not there. 

- A try-catch statement should have the following form: 
```
try {
  statements;
}
catch (Exception exception) {
  statements;
}
```
```
try {
  statements;
}
catch (Exception exception) {
  statements;
}
finally {
  statements;
}
```
This follows partly from the general block rule above. This form differs from the Sun recommendation in the same way as the if-else statement described above. 

### 6.2 White Space
- Logical units within a block should be separated by one blank line. 
```
// Create a new identity matrix
Matrix4x4 matrix = new Matrix4x4();

// Precompute angles for efficiency
double cosAngle = Math.cos(angle);
double sinAngle = Math.sin(angle);

// Specify matrix as a rotation transformation
matrix.setElement(1, 1,  cosAngle);
matrix.setElement(1, 2,  sinAngle);
matrix.setElement(2, 1, -sinAngle);
matrix.setElement(2, 2,  cosAngle);
```
Enhances readability by introducing white space between logical units. Each block is often introduced by a comment as indicated in the example above. 

### 6.3 Comments
- Tricky code should not be commented but rewritten [1]. 
In general, the use of comments should be minimized by making the code self-documenting by appropriate name choices and an explicit logical structure. 

- All comments should be written in English. 
In an international environment English is the preferred language. 

- There should be a space after the comment identifier. 
```
// comment something          not //comment something
/**
 * comment                          not /**
 *                                                               *comment
 */                                                              */
```
Improves readability by making the text stand out. 

- Use // for all non-JavaDoc comments, including multi-line comments. 
```
// Comment spanning 
// more than one line. 
```
Since multilevel Java commenting is not supported, using // comments ensure that it is always possible to comment out entire sections of a file using /* */ for debugging purposes etc. 

- Comments should be indented relative to their position in the code [1]. 
```
if(something){
   // doSomething
   doSomething
}
```
This is to avoid that the comments break the logical structure of the program. 

- The declaration of anonymous collection variables should be followed by a comment stating the common type of the elements of the collection. 
```
private Vector points_; // of Point 
private Set shapes_; // of Shape 
```
Without the extra comment it can be hard to figure out what the collection consist of, and thereby how to treat the elements of the collection. In methods taking collection variables as input, the common type of the elements should be given in the associated JavaDoc comment. 
Whenever possible one should of course qualify the collection with the type to make the comment superflous: 
```
  private Vector<Point>  points_;
  private Set<Shape>     shapes_;
```

  
Reference : http://geosoft.no/development/javastyle.html
