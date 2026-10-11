---
Subject: Java
Topic: core-java
Tags:
  - variable
  - variable-types
---

# Variable
> A **variable** is a **name given to a memory location (memory address)** used to **store some value**, and that value can be **accessed or changed during program execution**.

### 1. Variable Declaration
**Declaration** means creating a variable by specifying its **data type and name**.
```java
int a;
```
### 2. Variable Initialization
**Initialization** means giving a variable its **first value** (for the first time).
```java
int a = 10;
```
### 3. Variable Assignment
**Assignment** means giving a value to a variable (or updating it).
```java
a = 20;
```
### 4. Variable Declaration & Assigning Together
This means declaring a variable and immediately giving it a value in the same line.
```java
int a = 10;
```
## Rules for Naming Variables in Java
| Rule               | Description                                                            | Valid Example                | Invalid Example              |
| ------------------ | ---------------------------------------------------------------------- | ---------------------------- | ---------------------------- |
| Starting character | A variable name must begin with a letter (`a–z` or `A–Z`), `_`, or `$` | `count`, `_index`, `$price`  | `2total`                     |
| Allowed characters | Only letters, digits, `_`, and `$` are allowed                         | `marks1`, `total_sum`        | `total-sum`, `roll no`       |
| No spaces          | Variable names cannot contain spaces                                   | `totalMarks`                 | `total Marks`                |
| No Java keywords   | Reserved Java keywords cannot be used as variable names                | `value`, `myClass`           | `class`, `int`, `public`     |
| Case sensitivity   | Java treats uppercase and lowercase letters differently                | `score` and `Score`          | —                            |
| Meaningful names   | Variable names should describe their purpose clearly                   | `studentName`, `totalAmount` | `x`, `a1`                    |
| Naming convention  | Use **camelCase** for variable names (standard practice)               | `firstName`, `bankBalance`   | `First_name`, `bank_balance` |
| `$` usage          | `$` is allowed but generally avoided in real projects                  | `$total`                     | —                            |

**[Types of Variables](20-JAVA-VARIABLES.md)**

[**PTO**](80-CONCATENATION.md)