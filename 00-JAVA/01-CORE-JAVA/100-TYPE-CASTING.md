# Type Casting
**Type casting** means converting a value from **one data type to another data type**.
### There are two types of Type Casting:
1) Implicit Type Casting
2) Explicit Type Casting
## 1) Implicit Type Casting
Converting a **smaller data type into a larger data type automatically** by Java (no data loss normally) is called **Implicit Type Casting**.
It is also known as **Widening Type Casting** or **Intrinsic Type Casting**.
**Example-1:** `int → double`
```java
int a = 10;
double b = a;   // int → double

System.out.println(a); // 10
System.out.println(b); // 10.0
```
**Example-2:** `char → int`
```java
char ch = 'A';
int x = ch;     // char → int

System.out.println(ch); // A
System.out.println(x);  // 65
```
## 2) Explicit Type Casting
converting a **larger data type into a smaller data type manually** using (may cause data loss).
It is also known as **Narrowing Type Casting** or **Extrinsic Type Casting**.
**Example-1:** `double → int`
```java
double a = 99.99;
int b = (int) a;   // double → int

System.out.println(a); // 99.99
System.out.println(b); // 99
```
**Example-2:** `long → short`
```java
long n = 5000;
short s = (short) n;   // long → short

System.out.println(n); // 5000
System.out.println(s); // 5000
```

[**PTO**](120-SUFFIX-FOR-FLOAT-AND-LONG-LITERALS.md)