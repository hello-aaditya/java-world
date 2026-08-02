# Control Flow of Java Programs
Every Java programs start execution from the `main()` method and runs **line by line** — this is known as **sequential execution**.
But, in real-world scenarios, programs rarely follow a straight path.  
They often need to **make decisions**, **repeat certain steps**, or **jump to another part of the code** depending on conditions.

To achieve this, Java provides special programming constructs called **Control Constructs** — they allow us to **control how and when certain parts of the program execute**.

# Control Constructs
- A **control construct** is a mechanism that allows us to **control or modify the flow of execution** in a program based on certain conditions.
- **Control Constructs** helps in decision-making, repeating tasks, or jumping out of loops.
- Control Constructs are classified into three categories:
	1) Conditional Constructs (Selection Statements)
	2) Looping Constructs (Iteration Statements)
	3) Jump Constructs (Branching Statements)

![control constructs.drawio](control%20constructs.drawio.svg)

| Control Constructs | Conditional Constructs (Selection Statements)                                       | Looping Constructs (Iteration Statements) | Jump Constructs (Branching Statements) |
| ------------------ | ----------------------------------------------------------------------------------- | ----------------------------------------- | -------------------------------------- |
| Types              | `if` Statement<br>`if-else` Statement<br>`else if` Ladder<br>`switch` Statement<br> | `for`<br>`while`<br>`do-while`            | `break`<br>`continue`<br>`return`      |

## 1) Conditional Constructs (Selection Statements)
### *`if`* Statement
`if` Statement is used when there is **only one condition** and we want to **perform a single task** _only if_ that condition is true.
##### Syntax:
```java
if (condition) {
    // executes when condition is true
}
```
##### Example:
```java
int age = 20;
if (age >= 18) {
    System.out.println("You are eligible to vote.");
}
```
---
### *`if-else`* Statement
`if-else` Statement is used when we have two possible outcomes— one when the condition is true, and another when it is false. 
##### Syntax:
```java
if (condition) {
    // executes if true
} else {
    // executes if false
}
```
##### Example:
```java
int num = 5;
if (num % 2 == 0) {
    System.out.println("Even number");
} else {
    System.out.println("Odd number");
}
```
---
### *`else-if`* Ladder
- `else-if` ladder is used when we have - **multiple conditions** to check, and we want to **perform different tasks** based on which condition is true.
- Java checks each condition **from top to bottom**, and the **first true condition’s block** gets executed — the rest will be skipped.
##### Syntax:
```java
if (condition1) {
    // code block
} else if (condition2) {
    // code block
} else {
    // default block
}
```
##### Example:
```java
int marks = 85;
if (marks >= 90) {
    System.out.println("Grade A");
} else if (marks >= 75) {
    System.out.println("Grade B");
} else {
    System.out.println("Grade C");
}
```
---
### *`switch`* Statement
- `switch` statements is used when we need to **compare a single variable or expression** against **multiple constant values** and **execute different tasks** based on the match.
- `switch` statements is an alternative of '**else-if**' **ladder**.
##### Syntax:
```java
switch (expression) {
    case value1:
        // block
        break;
    case value2:
        // block
        break;
    default:
        // if no case matches
}
```
##### Example:
```java
int day = 3;
switch (day) {
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    case 3:
        System.out.println("Wednesday");
        break;
    default:
        System.out.println("Invalid day");
}
```

###  Difference between `else-if` and `switch`
**When to Use Which:**
- If you have **multiple conditions** and **multiple tasks**, and all conditions are based on **equality (`==`)** — then use a **`switch` statement**.
- If you have **multiple conditions** and **multiple tasks**, but the conditions involve **relational operators** like `<`, `>`, `<=`, `>=`, or logical operators like `&&`, `||` — then use an **`else-if` ladder**.
---
## 2) Looping Constructs (Iteration Statements)
A **looping construct** (or **iteration statement**) is a mechanism that allows a program to **execute a block of code multiple times**, as long as a specific condition remains true.
### *`for`* loop
- A `for` loop is used when we need to execute a block of code **multiple times**, and we **already know in advance** how many times we want to execute that block.
##### Syntax:
```java
for (initialization; condition; update) {
    // body of the loop
}
```
##### Explanation:
- **Initialization** → runs once at the beginning (sets the starting value).
- **Condition** → checked before every iteration; if `true`, the loop continues.
- **Update** → executes after each iteration (usually increases or decreases the counter).
##### Example:
```java
for (int i = 1; i <= 5; i++) {
    System.out.println("Count: " + i);
}
```
##### Output:
```plaintext
Count: 1  
Count: 2  
Count: 3  
Count: 4  
Count: 5
```
Here, the loop runs **5 times** because the condition `i <= 5` is true for values 1 through 5.

---
### *`while`* loop
A `while` loop is used when we need to execute a block of code **multiple times**, but we **don't know in advance** how many times we want to execute that block.
##### Syntax:
```java
while (condition) {
    // body of the loop
}
```
##### Explanation:
- The condition is **checked before** each iteration.
- If the condition is true → the loop executes.
- If it becomes false → the loop stops immediately.
##### Example:
```java
int i = 1;
while (i <= 5) {
    System.out.println("Count: " + i);
    i++;
}
```
##### Output:
```plaintext
Count: 1  
Count: 2  
Count: 3  
Count: 4  
Count: 5
```
Here, the loop runs until `i <= 5` becomes false.

---
### *`do-while`* loop
A `do-while` loop is used when we need to execute a block of code **at least once**, and then **repeat it as long as the condition remains true**.
##### Syntax:
```java
do {
    // body of the loop
} while (condition);
```
##### Explanation:
- The statements inside the `do` block execute **first**.
- After that, the condition is evaluated.
- If it’s true → the loop repeats.
- If false → the loop stops.
##### Example-1:
```java
int i = 1;
do {
    System.out.println("Count: " + i);
    i++;
} while (i <= 5);
```
##### Output:
```plaintext
Count: 1  
Count: 2  
Count: 3  
Count: 4  
Count: 5
```
The body executes first, then `i <= 5` is checked after each iteration.
##### Example-2:
```java
int x = 10;
do {
    System.out.println("This runs once even though condition is false!");
} while (x < 5);
```
##### Output:
```plaintext
This runs once even though condition is false!
```
---
## 1.3 Jump Constructs (Branching Statements)
**Jump Construct (also known as Branching Statement)** is mechanism that allow a program to **change or transfer the control** from its normal sequence of execution to one of the following:
- **exit from a loop**,
- **skip an iteration**, or
- **return from a method**.
### *`break`* Statement
A `break` statement is used to **terminate the execution of a loop or a switch statement immediately**, and transfer the control to the **next statement after it**.
##### Example-1 (in loop):
```java
for (int i = 1; i <= 5; i++) {
    if (i == 3)
        break;
    System.out.println(i);
}
```
##### Output:
```plaintext
1  
2
```
Here, when `i == 3`, the `break` statement executes and the loop stops immediately.
##### Example-2 (in switch):
```java
int day = 2;
switch (day) {
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    case 3:
        System.out.println("Wednesday");
        break;
}
```
##### Output:
```plaintext
Tuesday

```
Without `break`, control would “fall through” and execute the remaining cases too.

---
### *`continue`* Statement
A `continue` statement is used to **skip the current iteration** of a loop and continue with the **next iteration**, without terminating the loop.
##### Example:
```java
for (int i = 1; i <= 5; i++) {
    if (i == 3)
        continue;
    System.out.println(i);
}
```
##### Output:
```plaintext
1  
2  
4  
5
```
When `i == 3`, the `continue` statement skips that iteration and moves to the next one.

---
### *`return`* Statement
A `return` statement is used to **exit from a method** and optionally **send a value back** to the part of the program that called it.
##### Syntax:
```java
return;          // for void methods
return value;    // for methods that return a value
```
##### Example:
```java
int add(int a, int b) {
    return a + b;   // returns the sum to the caller
}
```
##### Output:
If you call `add(3, 5)`, it returns `8`.

[**PTO**](140-TAKE-USER-INPUT.md)