# How Static Members Work Inside Memory
##### Program Code:
```java
class Program {
    static int a;
    static int b;
    int p;
    int q;
    
    static {
        System.out.println("Inside static block");
        a = 10;
        b = 20;
    }
    
    {
        System.out.println("Inside Non-Static block");
        p = 100;
        q = 200;
    }
    
    static void staticDisplay() {
        System.out.println("Inside Static method");
        System.out.println("a: " + a);
        System.out.println("b: " + b);
    }
    
    void nonStaticDisplay() {
        System.out.println("Inside Non-Static method");
        System.out.println("p: " + p);
        System.out.println("q: " + q);
    }
    
    public static void main(String[] args) {
        Program p = new Program();
        p.staticDisplay();
        p.nonStaticDisplay();
    }
}
```

#### Memory Segments in JVM
When we execute a Java program, the RAM is divided into **4 segments**:
1. **Code Segment** – Stores the entire program code
2. **Stack Segment** (**Method Area**)– Stores method activation records (method calls)
3. **Static Segment (Static Space)** – Stores static variables, static methods, and static blocks
4. **Heap Segment (Object Space)** – Stores objects created using `new` keyword
![Memory](./images/jvm_memory.pn
---
### Step-by-Step Execution Flow:
- **Step-1:** Program Loading
- **Step-2:** Class Loader Takes Control
- **Step-3:** JVM Starts Execution
- **Step-4:** Executing `main()` Method
- **Step-5:** Calling `p.staticDisplay()`
- **Step-6:** Calling `p.nonStaticDisplay()`
- **Step-7:** Program Termination
#### Step-1: Program Loading
The program is initially stored in the **hard disk**. When we execute the Java program, **Operating System (OS)** loads the entire code from the hard disk into the **Code Segment** inside RAM.

Then, the OS gives control to the **JVM**. Now JVM comes into actions and divides the RAM into 4 logical segments- 
1. **Code Segment** - Stores the entire program code
2. **Stack Segment** (**Method Area**) - Stores method activation records (method calls)
3. **Static Segment (Static Space)** - Stores static variables, static methods, and static blocks
4. **Heap Segment (Object Space)** - Stores objects created using `new` keyword.

Now JVM loads itself into the **Stack Segment**.
#### Step 2: Class Loader Takes Control
JVM hands over the control to the **Class Loader**. The Class Loader has **3 jobs** to do in a specific order:

1. **Job 1:** Search for Static Variables
2. **Job 2:** Search for Static Blocks
3. **Job 3:** Search for Static Methods
###### **Job 1: Loading Static Variables**
Class Loader goes to the **Code Segment** and searches for static variables. It finds:
- `static int a;`
- `static int b;`

The Class Loader allocates memory for `a` and `b` inside the **Static Segment** and initializes them with their default values:
- `a = 0`
- `b = 0`
###### **Job 2: Loading and Executing Static Blocks**
Next, the Class Loader searches for **static blocks** inside the Code Segment. It finds one static block:
```java
static {
    System.out.println("Inside static block");
    a = 10;
    b = 20;
}
```

The Class Loader places the entire static block from the **Code Segment** to the **Static Segment**. But it doesn't just place it – it also **executes** it immediately.
###### Execution of Static Block:
1. The Class Loader creates an **activation record** for the static block in the **Stack Segment**.
2. Control enters the static block inside the stack.
3. **First line:** `System.out.println("Inside static block");`  
    → Prints **"Inside static block"** on the console.
4. **Next line:** `a = 10;`  
    → Control goes to the Static Segment, updates the value of `a` from `0` to `10`, and returns to the stack.
5. **Next line:** `b = 20;`  
    → Control goes to the Static Segment, updates the value of `b` from `0` to `20`, and returns to the stack.
6. The static block execution completes. The **activation record** for the static block is **deleted** from the Stack Segment.
###### **Job 3: Loading Static Methods**
Now, the Class Loader searches for **static methods** inside the Code Segment. It finds:
- `static void staticDisplay() {...}`
- `public static void main(String[] args) {...}` (main is also a static method)

The Class Loader places both methods from the **Code Segment** to the **Static Segment**.

**Important:** Static methods are only **placed** in the Static Segment, **not executed** at this point.
#### Step 3: JVM Starts Execution
After the Class Loader completes its 3 jobs, it hands over control back to the **JVM**.

JVM goes to the **Static Segment** and searches for the **`main()` method**. Once found, JVM places the `main()` method from the Static Segment to the **Stack Segment** and creates an **activation record** for `main()`. Now, execution of `main()` begins.
#### Step 4: Executing `main()` Method
**First line inside `main()`:**
```java
Program p = new Program();
```
JVM sees the `=` operator, so it goes to the **RHS** first. The very first word on the RHS is the **`new` keyword**.

As soon as JVM encounters `new`, it creates a block of memory in the **Heap Segment** for the `Program` object and assigns it an address, let's say **0x1000**.

Then, control enters the `Program` class to initialize the object:
###### **Inside Program class:**
1. **First two lines:** `static int a;` and `static int b;`  
    → Control **skips** these because static variables are already loaded in the Static Segment.
2. **Next two lines:** `int p;` and `int q;` (non-static variables)  
    → Control allocates memory for `p` and `q` **inside the heap block at address 0x1000** and initializes them with default values:
    - `p = 0`
    - `q = 0`
3. **Next line:** Static block  
    → Control **skips** this because the static block has already been executed during class loading.
4. **Next line:** Non-static block
```java
   {
       System.out.println("Inside Non-Static block");
       p = 100;
       q = 200;
   }
```

→ Control finds a **non-static block**. It creates an **activation record** for the non-static block in the **Stack Segment** and starts executing it.
###### Execution of Non-Static Block:
1. Control enters the non-static block in the stack.
2. **First line:** `System.out.println("Inside Non-Static block");`  
    → Prints **"Inside Non-Static block"** on the console.
3. **Next line:** `p = 100;`  
    → Control goes to the Heap Segment (address 0x1000), updates `p` from `0` to `100`, and returns to the stack.
4. **Next line:** `q = 200;`  
    → Control goes to the Heap Segment (address 0x1000), updates `q` from `0` to `200`, and returns to the stack.
5. The non-static block execution completes. The **activation record** for the non-static block is **deleted** from the Stack Segment.

Now, control returns to where it came from – back to the `main()` method.
###### **Back to `main()`:**
Control comes to the **LHS** of `Program p = new Program();`. Here, a **reference variable `p`** of type `Program` is created in the **Stack Segment** (inside the activation record of `main()`). The address **0x1000** is assigned to `p`.

Now, `p` is pointing to the object at address **0x1000** in the Heap Segment.
#### Step 5: Calling `p.staticDisplay()`
###### **Next line in `main()`:**
```java
p.staticDisplay();
```
At this point, `staticDisplay()` is present in two places:
1. Inside the **Code Segment** (original code)
2. Inside the **Static Segment** (loaded by Class Loader)

JVM always chooses the **Static Segment**. So, control takes the `staticDisplay()` method from the Static Segment and creates an **activation record** for `staticDisplay()` in the **Stack Segment**. Then, it starts executing the method.
###### **Execution of `staticDisplay()`:**
1. Control enters the static method inside the activation record.
2. **First line:** `System.out.println("Inside Static method");`  
    → Prints **"Inside Static method"** on the console.
3. **Next line:** `System.out.println("a: " + a);`  
    → Control goes to the Static Segment, reads the value of `a` (which is `10`), and prints **"a: 10"** on the console.
4. **Next line:** `System.out.println("b: " + b);`  
    → Control goes to the Static Segment, reads the value of `b` (which is `20`), and prints **"b: 20"** on the console.
5. The static method execution completes. The **activation record** for `staticDisplay()` is **deleted** from the Stack Segment.

Control returns to the `main()` method.
#### Step 6: Calling `p.nonStaticDisplay()`
```java
p.nonStaticDisplay();
```
JVM goes to the **Code Segment**, takes the `nonStaticDisplay()` method, and places it in the **Stack Segment**. An **activation record** for `nonStaticDisplay()` is created, and execution begins.
###### Execution of `nonStaticDisplay()`:
1. Control enters the non-static method inside the activation record. 
2. **First line:** `System.out.println("Inside Non-Static method");` → Prints **"Inside Non-Static method"** on the console. 
3. **Next line:** `System.out.println("p: " + p);` → Control uses the reference `p` (from `main()`), goes to the Heap Segment (address 0x1000), reads the value of `p` (which is `100`), and prints **"p: 100"** on the console. 
4. **Next line:** `System.out.println("q: " + q);` → Control goes to the Heap Segment (address 0x1000), reads the value of `q` (which is `200`), and prints **"q: 200"** on the console. 
5. The non-static method execution completes. The **activation record** for `nonStaticDisplay()` is **deleted** from the Stack Segment.

Control returns to the `main()` method.
#### Step 7: Program Termination
Now, there are no more statements left to execute inside `main()`. So, control exits the `main()` method. As soon as it exits, the **activation record of `main()`** is deleted, and memory is deallocated from the Stack Segment.

The reference variable `p` (which was in the `main()` activation record) is also deleted. Now, no one is pointing to the object at address **0x1000** in the Heap Segment. This object becomes a **Garbage Object**, and the **Garbage Collector** will eventually de-allocate its memory.

Control returns to the JVM. Since the JVM's work is finished, it exits the Stack Segment and hands over control back to the **Operating System (OS)**.
### Output
```plainText
Inside static block
Inside Non-Static block
Inside Static method
a: 10
b: 20
Inside Non-Static method
p: 100
q: 200
```