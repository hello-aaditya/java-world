# `LinkedList`
- The underlying data structure is doubly LinkedList.
- Insertion order is preserved.
- Duplicate objects are allowed.
- Heterogeneous objects are allowed.
- `Null` insertion is possible.
- `LinkedList` implements `Serializable` and `Cloneable` interfaces but not `RandomAccess` interface.
- `LinkedList` is the best choice if our frequent operation is insertion or deletion in the middle.
- `LinkedList` is the worst choice if our frequent operation is retrieval operation.
## Constructor
- `LinkedList list = new LinkedList();` creates an empty `LinkedList` object.
- `LinkedList list = new LinkedList(Collection c);` creates an equivalent `LinkedList` object for the given `Collection`.
## `LinkedList` class specific methods
- Usually we can use `LinkedList` to develop stacks and queues.
   To provide support for this requirement `LinkedList` class defines the following specific methods:
   1. `void addFirst(Object o)`
   2. `void addLast(Object o)`
   3. `Object getFirst()`
   4. `Object getLast()`
   5. `Object removeFirst()`
   6. `Object removeLast()`
Example:
```java
package collections.list.linkedList;

import java.util.LinkedList;

public class LinkedListDemo {

	public static void main(String[] args) {
		
		// create a LinkedList
		LinkedList list = new LinkedList();
		
		list.add("Charlie"); // add a string
		list.add(30);        // add an integer
		list.add(null);      // add null
		list.add("Charlie"); // add a string
		list.add(0, "Beta"); // add a string at 0th-index
		list.add(0, "Alpha");// add a string at 0th-index
		list.removeLast();   // remove the last element
		list.addFirst(10);   // add an integer at first index (0th-index)
		
		System.out.println(list); // [10, Alpha, Beta, Charlie, 30, null]

	}

}
```
## Difference between `ArrayList` and `LinkedList`

| #   | `ArrayList`                                                                                                                                                 | `LinkedList`                                                                                                                     |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| 1   | `ArrayList` is the best choice if our frequent operation is retrieval operation.                                                                            | `LinkedList` is the best choice if our frequent operation is insertion and deletion in middle.                                   |
| 2   | `ArrayList` is the worst choice if our frequent operation is insertion or deletion in the middle because internally several shift operations are performed. | `LinkedList` is the worst choice if our frequent operation is retrieval operation.                                               |
| 3   | In `ArrayList` the elements will be stored in consecutive memory locations and hence retreival operation will become easy.                                  | In `LinkedList` the elements won't be store in consecutive memory locations and hence retrieval operation will become difficult. |
