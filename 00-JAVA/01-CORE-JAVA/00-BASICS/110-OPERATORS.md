# Operators
Operators are special symbols used to perform operations on variables and values (known as **operands**).

On the basis of number of operands, operators are classified into 3 types:
1. **Unary Operator**
2. **Binary Operator**
3. **Ternary Operator**
### 1. Unary Operator
A **Unary Operator** is an operator that performs an operation on **only one operand**.
### 2. Binary Operator
A **Binary Operator** is an operator that performs an operation on **two operands**
### 3. Ternary Operator
A **Ternary Operator** is an operator that works on **three operands** and is mainly used as a **short form of if-else**.

## 1. Unary Operator
|Sl No.|Operator Name|Symbol|Working|
|--:|---|---|---|
|1|Unary Plus|`+`|Keeps the value positive (no change)|
|2|Unary Minus|`-`|Converts the value into negative (changes sign)|
|3|Increment|`++`|Increases value by `1`|
|4|Decrement|`--`|Decreases value by `1`|
|5|Logical NOT|`!`|Reverses boolean result (`true ↔ false`)|
|6|Bitwise NOT / One’s Complement|`~`|Flips all bits (`0 ↔ 1`)|
## 2. Binary Operator
Types of Binary Operators:
1. **Arithmetic Operators**
2. **Relational / Comparison Operators**
3. **Logical Operators**
4. **Bitwise Operators**
5. **Shift Operators**
6. **Assignment Operators**
7. **Special Operator (`instanceof`)**
> **A**ngry **R**aju **L**oves **B**ig **S**picy **A**loo **S**amosa
>
>**A**ngry → Arithmetic
>
>**R**aju → Relational
>
>**L**oves → Logical
>
>**B**ig → Bitwise
>
>**S**picy → Shift
>
>**A**loo → Assignment
>
>**S**amosa → Special
#### 1. Arithmetic Operators
**Arithmetic operators** are operators that take **two numeric values** (integer or floating point) as input, perform **mathematical operations** on them, and produce a **numeric value** (integer or floating point).
#### 2. Relational / Comparison Operators
**Relational operators** are operators that take **two numeric, char or boolean values** as input, compare them and produce a boolean output.
#### 3. Logical Operators
Logical Operators are operators that take two boolean values/conditions as input and produce a boolean output.
#### 4. Bitwise Operators
**Bitwise Operators** are operators that take **two non-floating point integer values** (`byte`, `short`, `int`, `long`, `char`) as input, perform operations **bit-by-bit** on their binary representation, and produce an **integer-type result** (generally `int`, or `long` if operands are long).
#### 5. Shift Operators
Shift Operators are operators that take one non-floating point integer value** (`byte`, `short`, `int`, `long`, `char`) as input and one **shift count** and shift the bits left/right to produce an **integer result**.
#### 6. Assignment Operators
Assignment Operators are operators that take a **variable** on the left side and a **value/expression of compatible type** on the right side  
and assign/update the value of that variable.
#### 7. `instanceof` Operator
An operator that takes an **object reference** and - and a **class/interface type** and checks whether the object is an instance of that type, returning **boolean** (`true/false`).

### 1.1) Arithmetic Operators
|Sl No.|Name of Operator|Symbol|Working|
|--:|---|---|---|
|1|Addition|`+`|Adds two numbers|
|2|Subtraction|`-`|Subtracts right value from left value|
|3|Multiplication|`*`|Multiplies two numbers|
|4|Division|`/`|Divides left value by right value|
|5|Modulus (Remainder)|`%`|Gives remainder after division|
### 1.2) Relational / Comparison Operators
|Sl No.|Name of Operator|Symbol|Working|
|--:|---|---|---|
|1|Greater Than|`>`|Checks if left value is greater than right|
|2|Less Than|`<`|Checks if left value is less than right|
|3|Greater Than or Equal To|`>=`|Checks if left value is greater than or equal to right|
|4|Less Than or Equal To|`<=`|Checks if left value is less than or equal to right|
|5|Equal To|`==`|Checks if both values are equal|
|6|Not Equal To|`!=`|Checks if both values are not equal|
### 1.3) Logical Operators
| Sl No. | Name of Operator | Symbol | Working                                      |
| -----: | ---------------- | ------ | -------------------------------------------- |
|      1 | Logical AND      | `&&`   | True only if both conditions are true        |
|      2 | Logical OR       | \|\|   | True if at least one condition is true       |
|      3 | Logical NOT      | `!`    | Reverses the boolean result (`true ↔ false`) |
### 1.4) Bitwise Operators
| Sl No. | Name of Operator               | Symbol | Working                                                                                                |
| -----: | ------------------------------ | ------ | ------------------------------------------------------------------------------------------------------ |
|      1 | Bitwise AND                    | `&`    | If **both bits are `1`**, result bit becomes **`1`**, otherwise **`0`**.                               |
|      2 | Bitwise OR                     | \|     | If **any one bit is `1`**, result bit becomes **`1`**, otherwise **`0`**.                              |
|      3 | Bitwise XOR                    | `^`    | If **both bits are different** (`0 and 1` / `1 and 0`), result bit becomes **`1`**, otherwise **`0`**. |
|      4 | Bitwise NOT (One’s Complement) | `~`    | Flips all bits (0 ↔ 1)                                                                                 |
### 1.5) Shift Operators
|Sl No.|Name of Operator|Symbol|Working|
|--:|---|---|---|
|1|Left Shift|`<<`|Shifts bits to the left|
|2|Right Shift|`>>`|Shifts bits to the right (keeps sign)|
|3|Unsigned Right Shift|`>>>`|Shifts bits right (fills 0, ignores sign)|
### 1.6) Shift Operators
|Sl No.|Name of Operator|Symbol|Working|
|--:|---|---|---|
|1|Assignment|`=`|Assigns value to a variable|
|2|Add and Assign|`+=`|Adds and assigns|
|3|Subtract and Assign|`-=`|Subtracts and assigns|
|4|Multiply and Assign|`*=`|Multiplies and assigns|
|5|Divide and Assign|`/=`|Divides and assigns|
|6|Modulus and Assign|`%=`|Remainder and assigns|
|7|AND and Assign|`&=`|Bitwise AND and assigns|
|8|OR and Assign|`|=`|
|9|XOR and Assign|`^=`|Bitwise XOR and assigns|
|10|Left Shift and Assign|`<<=`|Left shift and assigns|
|11|Right Shift and Assign|`>>=`|Right shift and assigns|
|12|Unsigned Right Shift and Assign|`>>>=`|Unsigned right shift and assigns|
### 1.7) instanceof Operators
| Sl No. | Name of Operator       | Symbol       | Working                                              |
| -----: | ---------------------- | ------------ | ---------------------------------------------------- |
|      1 | Type Checking Operator | `instanceof` | Checks object belongs to a class/type (`true/false`) |

# Operator Precedence
**Operator precedence** defines the **priority/order** in which operators are evaluated in an expression when **multiple operators are present**.  
The operator with **higher precedence** is evaluated **first**.
# Operator Associativity
Operator Associativity defines the **direction of execution** when **two or more operators of same precedence** come together in an expression.  
It decides whether evaluation will happen **Left to Right** or **Right to Left**.

# Difference between `==` and `=`

| `==` (Assignment Operator)                                      | `=` (Equality / Comparison Operator)                                                |
| --------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `=` is used to **assign a value** to a variable.                | `==` is used to **compare two values** and check whether they are **equal or not**. |
| It **stores** the right-side value into the left-side variable. | It returns a **boolean result**: `true` or `false`.                                 |

[**PTO**](90-DATA-TYPE.md)