# CoreJava17Concept
# Pattern matching
Pattern matching for the **instanceof** operator, finalized in Java 16 (JEP 394) and fully available in Java 17, 
streamlines code by combining a type check with the declaration of a pattern variable. </br>

Before pattern matching, you had to explicitly check the type and then cast the object to use its specific methods: </br>
public static void traditionalCheck(Object obj) { </br>
      if (obj instanceof String) { </br>
   &emsp;     String s = (String) obj; // Explicit cast required </br>
   &emsp;     System.out.println("Object length: " + s.length()); </br>
&emsp;    } </br>
}  </br>

Pattern Matching Approach (Java 17) </br>
With pattern matching, a pattern variable is automatically created and assigned if the instanceof check is successful.  </br>
The variable is safely scoped to the block where the check is true. </br>
public static void patternMatchCheck(Object obj) { </br>
    if (obj instanceof String s) { </br>
   &emsp;     // 's' is a pattern variable of type String, automatically cast </br>
  &emsp;      System.out.println("Object length: " + s.length()); </br>
    }  </br>
   &emsp; // 's' is not in scope here </br>
}  </br>


# Text Blocks

A text block starts and ends with **three double quotes (""")**. </br>
**Opening**: The """ must be followed immediately by a line break. </br>
**Closing**: The """ can be on its own line or at the end of the last line.  </br>

Used for multi-line strings. </br>

String json = """ </br>
{ </br>
&emsp;  "name": "John", </br>
&emsp;  "age": 30 </br>
} </br>
"""; </br>

# Switch
Java 17 fully supports enhanced switch expressions and the traditional switch statements, </br>
**1. Arrow Syntax (->)** </br>
The arrow syntax simplifies code by eliminating the need for break statements to prevent fall-through. </br>
Execution automatically exits the switch block after the statement or expression to the right of the arrow is run. </br>
int day = 3; </br>
switch (day) { </br>
 &emsp;   case 1 -> System.out.println("Monday"); </br>
&emsp;    case 2 -> System.out.println("Tuesday"); </br>
&emsp;    case 3 -> System.out.println("Wednesday"); </br>
&emsp;    default -> System.out.println("Invalid day"); </br>
} </br>


**2. Switch Expressions (Returning a Value)**
You can use switch as an expression to directly assign a value to a variable, which results in more concise code. When used as an expression, </br>
it must be exhaustive (cover all possible input values), usually requiring a default case unless switching over all possible enum constants. </br>
String dayString = switch (day) { </br>
&emsp;    case 1 -> "Monday"; </br>
&emsp;    case 2 -> "Tuesday"; </br>
&emsp;    case 3 -> "Wednesday"; </br>
&emsp;    default -> "Invalid day"; </br>
}; </br>

**3. yield Keyword**
For cases that require a multi-statement block but need to return a value in a switch expression, </br>
the yield keyword is used to specify the result.  </br>
int numDays = switch (month) { </br>
&emsp;     case 1, 3, 5, 7, 8, 10, 12 -> 31; </br>
&emsp;     case 4, 6, 9, 11 -> 30; </br>
&emsp;     case 2 -> { </br>
&emsp;         // Complex logic can go here  </br>
&emsp;         if (((year % 4 == 0) && !(year % 100 == 0)) || (year % 400 == 0)) { </br>
&emsp; &emsp;             yield 29; </br>
&emsp;         } else { </br>
&emsp;   &emsp;           yield 28; </br>
&emsp;         }  </br>
&emsp;     } </br>
&emsp;     default -> throw new IllegalArgumentException("Invalid month: " + month); </br>
}; </br>

**4. Multiple Case Labels**
Multiple constants can be combined in a single case label using a comma-separated list, </br>
which cleans up cases where the same code is executed for several inputs. </br>

**5.Pattern Matching (Preview)**
While fully finalized in later versions like Java 21, Java 17 included Pattern Matching for switch as a preview feature. </br>
This allows the switch expression to work with different data types (not just primitives, Enums, and Strings) and match patterns within cases. </br>

Object obj = "Hello"; </br>
String result = switch (obj) { </br>
&emsp;    case Integer i -> "It is an integer"; </br>
&emsp;    case String s -> "It is a string"; </br>
&emsp;    default -> "It is none of the known data types"; </br>
}; </br>


trick question can default be skipped ? </br>
Yes, only when all possible case covered. </br>

enum x = {"first", "second"}; </br>

switch(x){ </br>
case "first" -> system.out.println("first"); </br>
case "second" -> system.out.println("second"); </br>
} </br>

