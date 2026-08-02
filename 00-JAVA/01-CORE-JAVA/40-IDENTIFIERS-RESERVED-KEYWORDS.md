## Identifiers
> In Java An identifier is a name given to program elements such as variables, classes, methods, packages, interfaces etc. which are used to uniquely identify them during programming.
![Identifiers](./images/identifiers.drawio.svg)
### Rules for Identifiers
|     # | Rule                                                                                                             | ✔ Valid                                                      | ✘ Invalid                                                       |
| ----: | ---------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ | --------------------------------------------------------------- |
| **1** | An Identifier can contain **alphabets (`A-Z`, `a-z`), digits (`0-9`), underscore (`_`), and dollar sign (`$`)**. | `student`<br>`student1`<br>`student_name`<br>`$salary`       | `student-name`<br>`student@name`<br>`student#1`                 |
| **2** | An Identifier **must not start with a digit**. It can start only with an alphabet, `_`, or `$`.                  | `student1`<br>`_rollNo`<br>`$balance`                        | `1student`<br>`9rollNo`                                         |
| **3** | **Spaces are not allowed** inside an Identifier.                                                                 | `studentName`<br>`student_Name`                              | `student name`<br>`roll no`                                     |
| **4** | **Special characters are not allowed**, except `_` and `$`.                                                      | `employee_id`<br>`$amount`                                   | `employee-id`<br>`employee@id`<br>`employee%`                   |
| **5** | **Java Keywords cannot be used** as Identifiers because they have predefined meanings in Java.                   | `student``totalMarks`                                        | `class`<br>`int`<br>`public`<br>`return`                        |
| **6** | Identifiers are **Case-Sensitive**, so changing the case creates a different Identifier.                         | `student`<br>`Student`<br>`STUDENT`<br>_(all are different)_ | Assuming `Student` and `student` are the same Identifier.       |
| **7** | There is **no length limit** for an Identifier, but it should be meaningful and readable.                        | `student`<br>`employeeSalary`<br>`calculateInterest()`       | `a`<br>`x`<br>`temp123` <br>_(valid, but poor naming practice)_ |

---
## Reserved Words
> In Java Reserved words (keywords) **are predefined words that have a special meaning to the compiler and are reserved for specific purposes in the language. Since they are already part of Java's syntax, they cannot be used as identifiers (i.e., cannot be used to name variables, classes, methods, etc.).**

| #   | Category                   | Keywords                                                                                                                                                                |
| --- | -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | **Access Modifiers**       | `private`, `protected`, `public`                                                                                                                                        |
| 2   | **Control Flow Statement** | `break`, `case`, `continue`, `default`, `do`, `else`, `for`, `if`, `switch`, `while`                                                                                    |
| 3   | **Class-related**          | `abstract`, `class`, `enum`, `extends`, `final`, `implements`, `instanceof`, `interface`, `new`, `super`, `this`                                                        |
| 4   | **Exception Handling**     | `assert`, `catch`, `finally`, `throw`, `throws`, `try`                                                                                                                  |
| 5   | **Package related**        | `import`, `package`                                                                                                                                                     |
| 6   | **Multi-threading**        | `synchronized`, `volatile`                                                                                                                                              |
| 7   | **Others**                 | `boolean`, `byte`, `char`, `const`_, `double`, `float`, `goto`_, `int`, `long`, `native`, `return`, `short`, `static`, `strictfp`, `transient`, `void`, `true`, `false` |
*`const` and `goto` are reserved but unused in Java.
