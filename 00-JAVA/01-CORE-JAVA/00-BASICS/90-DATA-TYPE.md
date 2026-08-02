# Data Type
> A **Data type** is a mechanism to describe the kinds of data a variable can hold (like *numbers*, *decimals* or *characters*).

## Types of Data Type in Java
1. Primitive Data Types
2. Non-Primitive (Reference) Data Types
### 1. Primitive Data Types
- In Java **Built-in** data types are known as **Primitive Data Types**.
- Primitive Data Types are **not considered as Objects**.
- Examples: `int`, `char`, `boolean`, `float`, etc.
- Primitive Data Types are stored in **Stack Segment** because they hold the actual value directly.
- Example:
	```JAVA
	int x = 10;   // value 10 stored directly in stack
	```
### 2. Non-Primitive (Reference) Data Types
- Data Types that are created by programmers are known as **Non-Primitive Data Types**.
- Non-Primitive Data Types are **considered as Objects**.
- Examples: `String`, `Array`, `Class`, *Object*, etc.
- The **reference (address)** of Non-Primitive Data Types is stored inside **Stack Segment** and the actual object/data is stored in the **Heap Segment**.
- Example:
	```JAVA
	String name = "Raghav";
	```
	- The reference variable `name` is in Stack.
	- The `"Raghav"` object lives in SCP (String Constant Pool).
- That's why **Non-Primitive Data Types** are also known as **Reference Data Types**.
![Java-Data-Types](data-types.jpg)

There are 8 types of Primitive data types-
##### For Non-Floating Point Numbers
1. `byte`
2. `short`
3. `int`
4. `long`
##### For Floating Point Numbers
5. `float`
6. `double`
##### For Characters
7. `char`
##### For Boolean Numbers
8. `boolean`

| **Type**  |     **Size**      | **Default Value** |      **Example**      |       **Category**        |
|:---------:|:-----------------:|:-----------------:|:---------------------:|:-------------------------:|
|  `byte`   |  1 byte (8 bits)  |         0         |    `byte a = 100;`    |       Whole Number        |
|  `short`  | 2 bytes (16 bits) |         0         |  `short s = 20000;`   |       Whole Number        |
|   `int`   | 4 bytes (32 bits) |         0         |   `int x = 50000;`    |  Whole Number (default)   |
|  `long`   | 8 bytes (64 bits) |        0L         |  `long l = 100000L;`  |       Whole Number        |
|  `float`  | 4 bytes (32 bits) |       0.0f        |  `float f = 3.14f;`   |          Decimal          |
| `double`  | 8 bytes (64 bits) |       0.0d        | `double d = 3.14159;` | Decimal (Double, default) |
|  `char`   | 2 bytes (16 bits) | `'\u0000'` (null) |    `char c = 'A';`    |         Character         |
| `boolean` |      ~1 bit*      |       false       |  `boolean b = true;`  |   Logical (true/false)    |
Note: `boolean` size is JVM-dependent, but logically it’s treated as **1 bit** (true/false).
##### Formula for Range
> Range = $-2^{(n-1)}$ to $2^{(n-1)} - 1$
where `n` = number of bits (1 Byte = 8 bit).

## Java is Strongly Typed
> Java is a **strongly typed language**, which means every variable and expression has a type that is **fixed and known at compile time**, and the compiler **strictly enforces** rules about which operations and assignments are valid for that type.

```java
int x = "Hello";   // Compile-time error — String cannot be assigned to int
```
