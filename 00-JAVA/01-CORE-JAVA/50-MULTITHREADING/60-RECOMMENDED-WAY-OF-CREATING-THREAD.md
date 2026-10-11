>We can define a Thread in the following two ways:
>1. By extending `Thread` class
>2. By implementing `Runnable` interface

---
**Which appraoch is best to define a thread?**

Among the two ways of defining a thread, the `implements Runnable` approach is recommended.

In the first appraoch, our class always extend `Thread` class, so there is no chance of extending any other class. Hence, we are missing **inheritance benefit**.

But in the second appraoch, while implementing `Runnable` interface, we can extend any other class. Hence, we won't miss any inheritance benefit.

Because of above reason `implements Runnable` interface approach is **recommended** than extending `Thread` class.

## `extends Thread` vs `implements Runnable`

| #   | `extends Thread`                                                                                                                 | `implements Runnable`                                                                |
| --- | -------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| 1   | `Thread` is a **class**.                                                                                                         | `Runnable` is a **functional interface**.                                            |
| 2   | If my class extends a `Thread` class then we can't extends other classes because<br>Mutiple inheritence is not possible in Java. | If my class implements a `Runnable` interface then we can extends other classes too. |
| 3   | `Thread` provides many methods for **thread creation, control, lifecycle, interruption, etc.**                                   | `Runnable` has only **one abstract method: `run()`**                                 |
| 4   | `MyThread t1 = new MyThread();`                                                                                                  | `MyRunnable task = new MyRunnable();`<br>`Thread t1 = new Thread(task);`             |
