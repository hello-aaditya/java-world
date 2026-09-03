# `LinkedHashSet`
1. It is the child class of `HashSet`.
2. It is exactly same as `HashSet` (including constructors & methods) except the following differences:

| #   | `HashSet`                                       | `LinkedHashSet`                                                                  |
| --- | ----------------------------------------------- | -------------------------------------------------------------------------------- |
| 1   | The underlyiing data structure is 'Hash Table'. | The underlying data structure is a combination of `LinkedList` and 'Hash Table'. |
| 2   | Insertion order not preserved.                  | Insertion order preserved.                                                       |
| 3   | Introduced in 1.2v.                             | Introduced in 1.4v.                                                              |
**Example**:
```java
package collection.set.linkedHashSet;

import java.util.LinkedHashSet;

public class LinkedHashSetDemo {

	public static void main(String[] args) {
//		create a LinkedHashSet
		LinkedHashSet set = new LinkedHashSet();
		
		set.add("B");  // add a string
		set.add("C");  // add a string
		set.add("D");  // add a string
		set.add("Z");  // add a string
		set.add(null); // add null
		set.add(10);   // add an integer
		
		System.out.println(set.add("Z")); // false

// 		insertion order is preserved
		System.out.println(set); // [B, C, D, Z, null, 10]

	}

}
```
>[!NOTE]
>In general we can use `LinkedHashSet` to develop cache-based application where duplicates are not allowed and insertion order preserved.
