# The 3-Cursors of Java
- If we want to get objects one-by-one from the `Collection` then we should go for **Cursor**.
- There are 3 types of cursors available in Java-
	 1. Enumeration
	 2.  Iterator
	 3. ListIterator
## 1. `Enumeration`
1. We can use `Enumeration` to get objects one-by-one from legacy collection object.
2. We can create `Enumeration` object by `elements()` method of `Vector` class.
	**Syntax**:
	`public Enumeration elements();`
	**Example**:
	`Enumeration e = vector.elements();`
### `Enumeration` Specific Methods

| #   | Methods                            |
| --- | ---------------------------------- |
| 1   | `public boolean hasMoreElements()` |
| 2   | `public Object nextElement();`     |

**Example**:
```java
package collection.cursors.enumeration;

import java.util.Enumeration;
import java.util.Vector;

public class EnumerationDemo {

	public static void main(String[] args) {
		
//		create a vector
		Vector vector = new Vector();
		
//		add elements
		for (int i=0; i<=10; i++) {
			vector.addElement(i);
		}
		
//		print all elements at once
		System.out.println(vector);

//		create an enumeration
		Enumeration e = vector.elements();
		
//		traverse through the elements and print only even numbers
		while (e.hasMoreElements()) {
			Integer i = (Integer)e.nextElement();
			if (i % 2 == 0) {
				System.out.println(i);
			}
		}
	}

}
```
### `Limitations of Enumeration`
1. We can apply `Enumeration` concept only for Legacy-Classes and it is not a universal cursor.
2. By using `Enumeration` we can get only read access and we can't perform remove operation.

To overcome above limitations we should go for `Iterator`.
## 2. `Iterator`
1. We can apply `Iterator` concept for any `Collection` object and hence it is universal cursor.
2. By using `Iterator` we can perform both read & remove operations.
3. We can create `Iterator` object by using `iterator()` method of `Collection` interface.
	> `public Iterator iterator();`
	
Example:
`Iterator itr = c.iterator();` → where 'c' is any `Collection` object.	
### `Iterator` Specific Methods

| #   | Methods                     |
| --- | --------------------------- |
| 1   | `public boolean hasNext();` |
| 2   | `public Object next();`     |
| 3   | `public void remove();`     |
**Example**:
```java
package collection.cursors.iterator;

import java.util.ArrayList;
import java.util.Iterator;

public class IteratorDemo {

	public static void main(String[] args) {
		
//		create an ArrayList
		ArrayList list = new ArrayList();
		
//		insert elements inside ArrayList
		for (int i=0; i<=10; i++) {
			list.add(i);
		}
		
//		print all element
		System.out.println(list); // [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
		
//		create an iterator to traverse inside ArrayList
		Iterator itr = list.iterator();
		
//		traverse through the elements, print only even numbers and remove odd numbers
		while (itr.hasNext()) {
			Integer i = (Integer)itr.next();
			if (i % 2 == 0) {
				System.out.println(i);
			} else {
				itr.remove();
			}
		}
		
		System.out.println(list); // [0, 2, 4, 6, 8, 10]
	}

}
```
### Limitations of `Iterator`
1. By using `Enumeration` and `Iterator` we can only move only towards forward direction and we can't move towards backward direction. these are single direction cursors but not bidirectional cursor.
2. By using `Iterator` we can perform only read & remove operations and we can't perform replacement & addition of new objects.

To overcome above limitations we should go for `ListIterator`
## 3. `ListIterator` (I)
1. By using `ListIterator` we can move either to the forward direction or to the back direction and hence it is bidirectional cursor.
2. By using `ListIterator` we can perform **Replacement** & **Addition** of new objects in addition to **Read** & **Remove** operations.
3. We can create `ListIterator` object by using `listIterator()` method of `List` interface.
> `public ListIterator listIterator();`

Example:
`ListIterator itr = l.listIterator();` → where 'l' is any `List` object.
### `ListIterator` Specific Methods
- `ListIterator` is the child interface of `Iterator` and hence all methods present in `Iterator` by-default available to the `ListIterator`.
	![ListIterator-is-child-of-Iterator](ListIterator-is-child-of-Iterator.drawio.svg)
- `ListIterator` defines the following 9 methods:
	

| #   | Operation Type    | Syntax                          |
| --- | ----------------- | ------------------------------- |
| 1   | Forward Movement  | `public boolean hasNext();`     |
| 2   | Forward Movement  | `public Object next();`         |
| 3   | Forward Movement  | `public int nextIndex();`       |
|     |                   |                                 |
| 4   | Backward Movement | `public boolean hasPrevious();` |
| 5   | Backward Movement | `public Object previous();`     |
| 6   | Backward Movement | `public int previousIndex();`   |
|     |                   |                                 |
| 7   | Extra operations  | `public void remove();`         |
| 8   | Extra operations  | `public void add(Object o);`    |
| 9   | Extra operations  | `public void set(Object o);`    |
**Example**:
```java
package collection.cursors.ListIterator;

import java.util.LinkedList;
import java.util.ListIterator;

public class ListIteratorDemo {

	public static void main(String[] args) {
		
//		create an LinkedList
		LinkedList list = new LinkedList();
		
//		insert elements inside LinkedList
		list.add("Alpha");
		list.add("Beta");
		list.add("Charlie");
		list.add("Delta");
		
		System.out.println(list); // [Alpha, Beta, Charlie, Delta]
		
//		create a ListIterator to traverse inside LinkedList
		ListIterator itr = list.listIterator();
		
//		traverse through the elements and perform several operations
		while (itr.hasNext()) {
			String name = (String)itr.next();
			
			if (name.equals("Beta")) {
				itr.remove();       // [Alpha, Charlie, Delta]
			} else if (name.equals("Charlie")) {
				itr.add("Gamma");   // [Alpha, Charlie, Gamma, Delta]
			} else if (name.equals("Delta")) {
				itr.set("Epsilon"); // [Alpha, Charlie, Gamma, Epsilon]
			}
		}
		
		System.out.println(list); // [Alpha, Charlie, Gamma, Epsilon]
	}

}
```
- The most powerful cursor is `ListIterator` but its limitation is- it is applicable only for `List` objects.
## Comparison Table of 3 cursors-

| #   | Property           | `Enumeration`                                                   | `Iterator`                                                       | `ListIterator`                                                                                                                                                                                   |
| --- | ------------------ | --------------------------------------------------------------- | ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1   | Where we can apply | Only for Legacy Classes                                         | for any `Collection `object                                      | only for `List` objects                                                                                                                                                                          |
| 2   | Is it legacy?      | Yes (1.0v)                                                      | No (1.2v)                                                        | No (1.2v)                                                                                                                                                                                        |
| 3   | Movement           | Single Direction<br>(only forward direction)                    | Single Direction<br>(only forward direction)                     | Bi-directional                                                                                                                                                                                   |
| 4   | Allowed Operations | only read                                                       | Read & Remove                                                    | Read, Remove, Replace, Add                                                                                                                                                                       |
| 5   | How we can get?    | By using `.elements()` of `Vector` class                        | By using `.iterator()` of `Collection` (I)                       | By using `.listIterator()` of `List` (I)                                                                                                                                                         |
| 6   | Methods            | 2 Methods:<br><br>- `hasMoreElements();`<br>- `nextElements();` | 3 Methods:<br><br>- `hasNext();`<br>- `next();`<br>- `remove();` | 9 Methods:<br><br>-`hasNext();`<br>- `next();`<br>- `nextIndex();`<br>- `hasPrevious();`<br>- `previous();`<br>- `previousIndex();`<br>- `remove();`<br>- `add(Object o);`<br>- `set(Object o);` |

## Internal Implementation of Cursors
```java
package collection.cursors;

import java.util.Enumeration;
import java.util.Iterator;
import java.util.ListIterator;
import java.util.Vector;

public class CursorsDemo {

	public static void main(String[] args) {
		
		Vector vector = new Vector();
		
		Enumeration e = vector.elements();
		Iterator itr = vector.iterator();
		ListIterator listItr = vector.listIterator();
		
		System.out.println(e.getClass().getName()); // java.util.Vector$1
		
		System.out.println(itr.getClass().getName()); // java.util.Vector$Itr
		
		System.out.println(listItr.getClass().getName()); // java.util.Vector$ListItr

	}

}
```