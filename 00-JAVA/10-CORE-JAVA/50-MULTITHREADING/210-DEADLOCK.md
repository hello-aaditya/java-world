# Deadlock
> If two Threads are waiting for each-other forever, such type of infinite waiting is called **Deadlock**.

- `synchronized` keyword is the most common reason for Deadlock situation.
	Hence, while using `synchronized` keyword we have to take special care.
- There is no resolution technique but several prevention techniques are available.
![java_deadlock](java_deadlock.drawio.svg)
in the above program, if we remove at least one `synchronized` keyword then the program will not entered into Deadlock. Hence, `synchronized` keyword is only reason for Deadlock situation. Due to this, while using `synchronized` keyword we have to take special care.

## Deadlock vs Starvation

| #   | Deadlock                                                                  | Starvation                                                                                                                                                               |
| --- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1   | Long waiting of a Thread where waiting never ends is called **Deadlock**. | Long waiting of a Thread where waiting ends at certain point is called **Starvation**.                                                                                   |
| 2   | Example: two Threads waiting for each other's lock forever.               | Example: a low-priority Thread has to wait until completion of all high-priority Threads. It may be long waiting, but it ends at certain point, which is **Starvation**. |
