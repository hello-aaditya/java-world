# `Vector`
1. The underlying data structure is re-sizable array or growable array.
2. Insertion order is preserved.
3. Duplicate objects are allowed.
4. Heterogeneous objects are allowed.
5. `Null` insertion is possible.
6. It implements `Serializable`, `Cloneable` and `RandomAccess` interfaces.
7. Every method present in `Vector` is synchronized and hence `Vector` object is thread-safe.
## Constructor

| #   | Syntax                                                                       | Explanation                                                                                                                                                                                   |
| --- | ---------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | `Vector vector = new Vector();`                                              | creates an empty vector object with default initial capacity 10.<br>Once `Vector` reaches its max-capacity then a new `Vector` will be created with <br>$NewCapacity = CurrentCapacity * {2}$ |
| 2   | `Vector vector = new Vector(int initialCapacity);`                           | creates an empty `Vector` object with a specified initial capacity.                                                                                                                           |
| 3   | `Vector vector = new Vector(int initialCapacity, int increamentalCapacity);` |                                                                                                                                                                                               |
| 4   | `Vector vector = new Vector(Collection c);`                                  | creates an equivalent `Vector` objects for the given `Collection`.<br>This constructor meant for inter-conversion between `Collection` objects.                                               |
## `Vector` Specific Methods
### 1. To Add Objects
1. `add(addElement)` -- C
2. `add(int index, Object o)` -- L
3. `addElement(Object o)` -- V
### 2. To Remove Objects
1. `remove(Object o)` -- C
2. `removeElement(Object o)` -- V
3. `remove(int index)` -- L
4. `removeElementAt(int index)` -- V
5. `clear()` -- C
6. `removeAllElements()` -- V
### 3. To Get Objects
1. `Object get(int index)` -- L
2. `Object elementAt(int index)` -- V
3. `Object firstElement()` -- V
4. `Object lastElement()` -- V
### 4. miscellaneous Methods
1. `int size()`
2. `int capacity()`
3. `Enumeration elements()`
**Example:**
```java
package collections.list.legacyClasses.vector;

import java.util.Vector;

public class VectorClassDemo {

	public static void main(String[] args) {
		
//		Create a vector
		Vector vector = new Vector();
		
//		print the initial capacity
		System.out.println(vector.capacity()); // 10
		
//		add 10 element (i.e. fill all its initial capacity)
		for (int i=0; i<10; i++) {
			vector.addElement(i);
		}
		
//		print the capacity
		System.out.println(vector.capacity()); // 10
		
//		add a string in 11th-index (add element in initial capacity + 1 index)
		vector.add("Alpha");
		
//		again check the capacity
		System.out.println(vector.capacity()); // 20
		
//		print all element
		System.out.println(vector); // [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, Alpha]
		
//		create a vector with some initial capacity AWA mention incremental capacity
		Vector vector1 = new Vector(10, 5);
		
//		add 10 element (i.e. fill all its initial capacity)
		for (int i=0; i<10; i++) {
			vector1.addElement(i);
		}

//		print the capacity
		System.out.println(vector1.capacity()); // 10
		
//		add a string in 11th-index (i.e. add element in initial capacity + 1 index)
		vector1.add("Beta");
		
//		again check the capacity
		System.out.println(vector1.capacity()); // 15 → because, capacity will increase with its incrementalCapacity which is 5   
		
//		print all element
		System.out.println(vector1); // [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, Beta]
	}

}
```