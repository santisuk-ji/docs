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
