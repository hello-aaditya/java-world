# Inter Thread Communication
- Two Threads can communicate with each other by using `wait()`, `notify()` and `notifyAll()` methods.
- The Thread which is expecting **updation** is responsible to call `wait()` method on that required object then, immediately the Thread will enter into WAITING state.
- The Thread which is responsible to perform **updation** of that object, after performing updation, it is responsible to call `notify()` method then WAITING Thread will get that notification and immediately the Thread will enter into RUNNABLE state.

- `wait()`, `notify()`, `notifyAll()` methods present in Object class but not in `Thread` class because Thread can call these methods on any Java object.
- To call `wait()`, `notify()`, `notifyAll()`methods on any object, Thread should be owner of that object. That is- The Thread should has lock of that object means The Thread should be inside `synchronized` area. Hence, we can call `wait()`, `notify()`, `notifyAll()` methods only from `synchronized` area otherwise we will get `RuntimeException : IllegalMonitorStateException`.

- <mark>If a Thread calls `wait()` method on any object, it immediately release the lock of that particular object and entered into WAITING state</mark>.
- If a Thread calls `notify()` method on any object, it release the lock of that object but not immediately except `wait()`, `notify()`, `notifyAll()`there is no other method where Thread releases the lock.

| #   | Methods       | Does Thread release lock? |
| --- | ------------- | ------------------------- |
| 1   | `yield()`     | NO                        |
| 2   | `join()`      | NO                        |
| 3   | `sleep()`     | NO                        |
| 4   | `wait()`      | YES                       |
| 5   | `notify()`    | YES                       |
| 6   | `notifyAll()` | YES                       |

---
Which of the following is valid ?

| #   | Statements                                                                                                                                 | RIGHT / WRONG |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------ | ------------- |
| 1   | If a Thread calls `wait()` method on any object, immediately it will enter into WAITING state without releasing any LOCK.                  | ✕             |
| 2   | If a Thread calls `wait()` method on any object, it releases the lock of that object but may not immediately.                              | ✕             |
| 3   | If a Thread calls `wait()` method on any object, it releases all locks acquired by that Thread and immediately entered into WAITING state. | ✕             |
| 4   | If a Thread calls `wait()` method on any object, it immediately releases lock of that particular object and entered into WAITING state.    | ✓             |
| 5   | If a Thread calls notify() method on any object, it immediately  releases the lock of that particular object.                              | ✕             |
| 6   | If a thread calls notify() method on any object, it releases the lock of that object but may not immediately.                              | ✓             |
1. `public finl void wait() throws InterruptedException;`
2. `public final native void wait(long milliseconds) throws InterruptedException;`
3. `public finl void wait(long milliseconds, int nanoseconds) throws InterruptedException;`

4. `public final native void notify();`
5. `public final native void notifyAll();`
>[!NOTE]
>Every `wait()` method throws `InterruptedException` which is **Checked Exception**. Hence, whenever we are using `wait()` method, compulsory we should handle this InterruptedException either by **try-catch** or by **throws** keyword otherwise we will get Compile-Time Error.

![thread-lifecycle-with-waiting-to-acquire-lock-state](thread-lifecycle-with-waiting-to-acquire-lock-state.drawio.svg)

### Example: (`wait()`, `notify()`)
![wait-notify-example1](wait-notify-example1.drawio.svg)

Best Example of Inter-Thread Communication is **Producer-Consumer Problem**
