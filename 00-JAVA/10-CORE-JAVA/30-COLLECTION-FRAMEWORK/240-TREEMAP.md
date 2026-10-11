# `TreeMap`
1. The underlying data-structure is `Red-Black` tree.
2. Insertion order is not preserved and it is based on some sorting order of keys.
3. Duplicate keys are not allowed but values can be duplicated.
4. 
	- If we are depending on default natural sorting order then keys should be homogeneous and comparable otherwise we will get `RuntimeException` saying: `ClassCastException`.
	- If we are defining our own sorting by `Comparator` then keys need not be homogeneous and comparable. we can take heterogeneous non-comparable objects also.
5. Whether we are depending on default natural sorting order or customized sorting order there are no restriction for values, we can take heterogeneous non-comparable objects also.
## `null` acceptance
1. For non-empty `TreeMap` if we are trying to insert an entry with `null` key then we will get `RuntimeException` saying `NullPointerException`.
2. For empty `TreeMap` as the first entry with `null` key is allowed but after inserting that entry if we are trying to insert any other entry then we will get `RuntimeException` saying `NullPointerException`.
>[!NOTE]
>The above `null` acceptance rule applicable until Java-1 .6 only.
>From Java-1.7 onwards `null` is not allowed for key.
3. For values, we can use `null` any no. of times, there is no restriction whether it is Java-1.6 or Java-1.7 version.
## Constructor

| #   | Syntax                                     | Explanation                                                                                                                                            |
| --- | ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1   | `TreeMap map = new TreeMap();`             | Creates an empty `TreeMap` object where the keys will be inserted according to default natural sorting order.                                          |
| 2   | `TreeMap map = new TreeMap(Comparator c);` | Creates an empty `TreeMap` object where the keys will be inserted according to customized sorting order specified by `Comparator` object.              |
| 3   | `TreeMap map = new TreeMap(Map m);`        | Creates a `TreeMap` object containing the **mappings of the specified `Map`**, where the keys are maintained according to their natural sorting order. |
| 4   | `TreeMap map = new TreeMap(SortedMap m);`  | Creates a `TreeMap` object containing the **mappings of the specified `SortedMap`**, using the same key ordering as the specified `SortedMap`.         |
**Example-1 (Default Natural Sorting Order):**
```java
package collection.treeMap;

import java.util.TreeMap;

public class TreeMapDemo1 {

	public static void main(String[] args) {
		
		TreeMap map = new TreeMap();
		
//		keys should be homogeneous
//		but values can be heterogeneous
		map.put(100, "ZZZ");
		map.put(103, "YYY");
		map.put(101, "XXX");
		map.put(104, 160);
		
		System.out.println(map); // {100=ZZZ, 101=XXX, 103=YYY, 104=160}
		
//		inserting heterogeneous keys will give ClassCastException
//		map.put("FFFF", "AAAA");
		
//		map.put(null, "BBB"); // NullPointerException

	}

}
```
**Example-2 (Customized Sorting Order):**
```java
package collection.treeMap;

import java.util.Comparator;
import java.util.TreeMap;

class MyComparator implements Comparator {
	
	public int compare(Object obj1, Object obj2) {
		String s1 = obj1.toString();
		String s2 = obj2.toString();
		
		return -s1.compareTo(s2);
	}
}

public class TreeMapDemo2 {

	public static void main(String[] args) {
		
		TreeMap map = new TreeMap(new MyComparator());
		
		map.put("XXX", 10);
		map.put("AAA", 20);
		map.put("ZZZ", 30);
		map.put("LLL", 40);
		
		System.out.println(map); // {ZZZ=30, XXX=10, LLL=40, AAA=20}
	}

}
```