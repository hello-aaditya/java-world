# `Collections`
`Collections` class defines several utility class for `Collection` object, like- Sorting, Searching, Reversing etc.
## Sorting elements of `List`
`Collections` class defines the following two sort methods:

| #   | Methods                                             | Explanation                                                                                                                                                                                                                                                                                  |
| --- | --------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | `public static void sort(List list);`               | To sort based on **Default Natural Sorting Order**.<br>- In this case `List` should compulsory contain homogeneous & comparable objects otherwise we will get `RuntimeException` : `ClassCastException`.<br>- `List` should not contain `null` otherwise we will get `NullPointerException`. |
| 2   | `public static void sort(List list, Comparator c);` | To sort based on **Customized Sorting Order**.                                                                                                                                                                                                                                               |
**Example-1:** Program for sorting elements of `List` according to **Default Natural Sorting Order**
```java
package collectionsClass;

import java.util.ArrayList;
import java.util.Collections;

public class CollectionsSortDemo {

	public static void main(String[] args) {
		
		ArrayList list = new ArrayList();
		list.add("Z");
		list.add("A");
		list.add("K");
		list.add("N");
		
//		list.add(new Integer(10)); // CCE
//		list.add(null); // NPE
		
		System.out.println("Before Sorting: " + list); // [Z, A, K, N]
		
		Collections.sort(list);
		
		System.out.println("After Sorting: " + list); // [A, K, N, Z]

	}

}
```
>[!NOTE]
>- The line where we add a **heterogeneous object** will not raise any exception. Even printing the `List` will work, but we will get **`ClassCastException` when we call `Collections.sort()`** because objects cannot be compared with each other.
>- The line where we add a **`null` object** will not raise any exception. Even printing the `List` will work, but we will get **`NullPointerException` when we call `Collections.sort()`** because `null` cannot be compared with other objects during sorting.

**Example-2:** Program for sorting elements of `List` according to **Customized Sorting Order**
```java
package collectionsClass;

import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;

class MyComparator implements Comparator {
	
	@Override
	public int compare(Object obj1, Object obj2) {
		
		String s1 = obj1.toString();
		String s2 = obj2.toString();
		
		return s2.compareTo(s1);
	}
}

public class CollectionsSortDemo2 {

	public static void main(String[] args) {
		
		ArrayList list = new ArrayList();
		list.add("Z");
		list.add("A");
		list.add("K");
		list.add("N");

		System.out.println("Before Sorting: " + list); // [Z, A, K, N]
		
		Collections.sort(list, new MyComparator());
		
		System.out.println("After Sorting: " + list); // [Z, N, K, A]
	}
}
```