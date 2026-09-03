# `LinkedHashMap`
1. It is the child class of `HashMap`.
2. It is exactly same as `HashMap` (including methods & constructors) except the following difference:

| #   | `HashMap`                                                             | `LinkedHashMap`                                                                        |
| --- | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| 1   | The underlying data-structure is `Hashtable`.                         | the underlying data-structure is `LinkedList` and `Hashtable` (hybrid data-structure). |
| 2   | Insertion order is not preserved and it is based on hashcode of keys. | Insertion order is preserved.                                                          |
| 3   | Introduced in Java-1.2V.                                              | Introduced in Java-1.4V.                                                               |
```java
package collection.map.LinkedHashMap;

import java.util.LinkedHashMap;

public class LinkedHashMapDemo {

	public static void main(String[] args) {
		
		LinkedHashMap map = new LinkedHashMap();
		
		map.put("Alpha", 200);
		map.put("Beta", 150);
		map.put("Charlie", 250);
		map.put("Delta", 500);
		
		System.out.println(map); // {Alpha=200, Beta=150, Charlie=250, Delta=500}

	}

}
```
Insertion order is preserved.
>[!NOTE]
>`LinkeHashSet` and `LinkedHashMap` are commonly used for developing cache-based application.

## Difference between `==` and `.equals()` method
In general `==` meant for reference comparison (Address Comparison) whereas `.equals()` method meant for content comparison.
Example:
```java
public class Driver {

	public static void main(String[] args) {
		
		Integer i1 = new Integer(10);
		Integer i2 = new Integer(10);
		
		System.out.println(i1 == i2); // false
		
		System.out.println(i1.equals(i2)); // true

	}
}
```