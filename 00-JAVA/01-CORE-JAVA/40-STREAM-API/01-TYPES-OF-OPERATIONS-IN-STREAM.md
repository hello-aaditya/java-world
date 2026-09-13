# Types of Operations in Stream
There are two types of operations in Stream:
1. Intermediate Operation
2. Terminal Operation
![types-of-operations](./images/types-of-operations.drawio.svg)
## 1. Intermediate Operation
Operation which is taking stream as an input, process them and return another stream is called Intermediate operation.
- Intermediate Operations generate chains of operations means it can be called multiple times. (Stream 1 -> filter -> Stream 2 -> map -> Stream 3)
- Intermediate Operations are lazy in nature means they cannot be executed until a terminal operation is called.
- Some of the 
	