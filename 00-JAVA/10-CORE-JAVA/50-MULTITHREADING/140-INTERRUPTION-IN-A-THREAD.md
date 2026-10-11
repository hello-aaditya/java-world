# How a Thread can Interrupt another Thread ?
A Thread can interrupt a sleeping or waiting Thread by using `interrupt()` of `Thread` class.

`public void interrupt();`

![interrupt-method-demo](interrupt-method-demo.drawio.svg)
- If we comment line1 then `main` Thread won't interrupt `Thread-0`. In this case `Thread-0` will execute for-loop 10 times.
- If we are not commenting line1 then `main` Thread interrupts `Thread-0` Thread. In this case output is
```text
[main] STARTED...
[main] END...
[Thread-0] 1
[Thread-0] got interrupted
```
>[!NOTE]
>- Whenever we are calling `interrupt()` method, if the target Thread not is SLEEP state or WAIT state then there is no impact of interrupt call immediately. Interrupt call will be waited until target Thread entered into SLEEP or WAIT state.
>- If the target Thread entered into SLEEP state or WAIT state then immediately interrupt call will interrupt the target Thread.
>- If the target Thread never entered into SLEEP or WAIT state in its lifetime then there is no impact of interrupt call, this is the only case where interrupt call will be wasted.

![interrupt-method-demo-example-1](interrupt-method-demo-example-1.drawio.svg)

In the above example `interrupt()` waited until `Thread-0` Thread completes for-loop **10,000 times**.