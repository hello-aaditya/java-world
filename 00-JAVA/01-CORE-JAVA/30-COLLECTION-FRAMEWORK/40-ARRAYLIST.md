# `ArrayList`
- The underlying data structure is resizable array or growable array.
- Duplicates objects are allowed.
- Insertion order is preserved.
- Heterogeneous objects are allowed (Except `TreeSet` and `TreeMap` everywhere heterogeneous objects are allowed)
- `null` insertion is possible.
## Constructors

| #   | Syntax                                                 | Explanation                                                                                                                                                                                                                        |
| --- | ------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | `ArrayList list = new ArrayList();`                    | creates an empty `ArrayList` object with default initial capacity 10.<br>Once `ArrayList` reaches its max capacity then a new `ArrayList` will be created with <br>$NewCapacity = CurrentCapacity + \frac{CurrentCapacity}{2}$<br> |
| 2   | `ArrayList list = new ArrayList(int initialCapacity);` | creates an empty `ArrayList` object with specified initial capacity.                                                                                                                                                               |
| 3   | `ArrayList list = new ArrayList(Collection c);`        | creates an equivalent `ArrayList` object for the given `Collection`.                                                                                                                                                               |
Example
```java
package collections.list.arrayList;

import java.util.ArrayList;

public class ArrayListDemo {

	public static void main(String[] args) {
		
		// create an ArrayList
		ArrayList l = new ArrayList();

		l.add("A"); // add a string
		l.add(10);  // add an integer value
		l.add("A"); // add a existed string (duplicates are allowed)
		l.add(null);// add null
		
		// print ArrayList
		System.out.println(l); // [A, 10, A, null]
		
		l.remove(2); // delete 2nd-index element
		
		System.out.println(l); // [A, 10, null]
		
		l.add(2, "M"); // add an element on 2nd-index
		l.add("N");    // add a string at last position
		
		System.out.println(l); // [A, 10, M, null, N]
		
	}
}
```
- Usually we can use `Collection` to hold and transfer objects from one location to another location (container). to provide support for this requirement every `Collection`-class by-default implements **Serializable** and **Clonable** interfaces.
- `ArrayList` and `Vector` class implements `RandomAccess` interface so that any random element we can access with the same speed.
## `RandomAccess` (I)
- `RandomAccess` interface present in `java.util` package and it doesn't contain any methods. 
- It is a marker interface, where required ability will be provided automatically by the JVM.

```java
ArrayList list1 = new ArrayList();
LinkedList list2 = new LinkedList();

System.out.println(list1 instanceof Serializable); // true
System.out.println(list2 instanceof Serializable); // true

System.out.println(list1 instanceof Cloneable);    // true
System.out.println(list2 instanceof Cloneable);    // true

System.out.println(list1 instanceof RandomAccess); // true 
System.out.println(list2 instanceof RandomAccess); // false
```
- `ArrayList` is the best choice if our frequent operation is retrieval operation (because `ArrayList` implements `RandomAccess` interface).
- `ArrayList` is the worst choice if our frequent operation is insertion or deletion in the middle.
## Difference between `ArrayList` and `Vector`

| #   | `ArrayList`                                                                                                                                                                                                           | `Vector`                                                                                                                                                                                                      |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | Every method present in the `ArrayList` is **non-synchronized**                                                                                                                                                       | Every method present in the `vector` is **synchronized**                                                                                                                                                      |
| 2   | At a time **multiple-threads are allowed** to operate on `ArrayList` objects and hence it is **not thread-safe**.<br>![diff-between-arraylist-vs-vector-al-part](diff-between-arraylist-vs-vector-al-part.drawio.svg) | At a time only **one thread is allowed** to operate on `vector` object and hence **it is thread-safe**.<br>![diff-between-arraylist-vs-vector-vec-part](diff-between-arraylist-vs-vector-vec-part.drawio.svg) |
| 3   | Relatively performance is **high** because thread are not required to wait to operate on `ArrayList` object.                                                                                                          | Relatively performance is **low** becuase threads are required to wait to operate on `vector` object.                                                                                                         |
| 4   | Introduced in **1.2-version** and it is **non-legacy**.                                                                                                                                                               | Introduced in **1.0-version** and it is **legacy**.                                                                                                                                                           |
## How to get Synchronized version of `ArrayList` Object?
By-default `ArrayList` is non-synchronized but we can get synchronized version of `ArrayList` object by using `synchronizedList()` method of `Collections` class.
`public static List synchronizedList(List l)`
Example:
```java
ArrayList list = new ArrayList();
List list1 = Collections.synchronizedList(list);
```
![synchronized-vs-non-synchronized](synchronized-vs-non-synchronized.drawio.svg)

- Similarly we can get synchronized version of `Set` and `Map` objects by using following methods of `Collections` class.
- Example:
	- `public static Set synchronizedSet(Set s)`
	- `public static Map synchronizedMap(Map m)`