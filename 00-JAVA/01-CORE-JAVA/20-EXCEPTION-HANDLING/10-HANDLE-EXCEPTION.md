# How do we handle Exception?
An exception is handled by enclosing the risky code inside a `try` block and writing one or more `catch` blocks to handle specific exceptions. This prevents the program from terminating abruptly and allows normal execution to continue.
## `try` block
> A `try` block is a block of code that contains statements which may throw an exception during program execution. If an exception occurs inside the `try` block, the JVM immediately transfers control to the matching `catch` block to handle the exception.

