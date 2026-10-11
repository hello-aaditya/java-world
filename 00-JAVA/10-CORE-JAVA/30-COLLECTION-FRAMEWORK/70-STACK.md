# Stack
- It is the child class of `Vector`.
- It is a specially designed class for Last-In-First-Out order (LIFO).
## Constructor
`Stack stack = new Stack();`
## `Stack` Specific Methods
1. `Object push(Object o)` → to insert an object into the stack.
2. `Object pop()` → to remove and return top of the stack.
3. `Object peek()` → to return top element of the stack without removal.
4. `Boolean empty()` → returns true if the stack is empty.
5. `int search(Object o)` → returns offset if the element is available otherwise returns -1.
	![stack-search-method](stack-search-method.drawio.svg)
**Example**:
```java
package collections.list.legacyClasses.stack;

import java.util.Stack;

public class StackClassDemo {

	public static void main(String[] args) {
		
//		create a stack
		Stack stack = new Stack();
		
//		push elements inside stack
		stack.push("A");
		stack.push("B");
		stack.push("C");
		
//		print all element
		System.out.println(stack); // [A, B, C]
		
//		search offset of element "A" 
		System.out.println(stack.search("A")); // 3
		
//		search offset of element "Z"
		System.out.println(stack.search("Z")); // -1
	}

}
```