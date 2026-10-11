# `synchornized` Keyword
`synchronized` defines as- 
> One Thread at a time on a particular shared object.

- `synchronized` is a keyword which is applicable for methods and blocks only.
- If a method or block is declared with `synchronized` then - <mark>At a time only one Thread is allow to execute that method or block on a particular shared object</mark>.
- The main advantage of `synchronized` keyword is- **"It resolves data inconsistency problem"**.
- The main disadvantage of `synchronized` keyword is- **"It increases waiting time of Threads and creates performance problems."**

	Hence, if there is no specific requirement then never recommended to use `synchronized` keyword.
1. [`synchronized` Method](./180-SYNCHRONIZED-METHOD.md)
2. [`synchronized` Block](./190-SYNCHRONIZED-BLOCK.md)