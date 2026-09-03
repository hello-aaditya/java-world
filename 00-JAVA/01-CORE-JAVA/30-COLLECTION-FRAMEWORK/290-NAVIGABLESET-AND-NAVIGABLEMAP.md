# Java-1.6 enhancements in Collection Framework
As a part of Java-1.6 version the following two concepts introduced in Collection Framework:
1. `NavigableSet`
2. `NavigableMap`
# 1. `NavigableSet`
![NavigableSet](./images/NavigableSet.drawio.svg)
- It is the child interface of `SortedSet` (I) and it defines several methods for navigation purposes.
## `NavigableSet` Specific Methods

| #   | Methods            | Explanation                                 |
| --- | ------------------ | ------------------------------------------- |
| 1   | `floor(e);`        | It returns highest elements which is <= e.  |
| 2   | `lower(e);`        | It returns highest element which is < e.    |
| 3   | `ceiling(e);`      | It returns lowest element which is >= e.    |
| 4   | `higher(e);`       | It returns lowest element which is > e.     |
| 5   | `pollFirst();`     | It removes and returns first element.       |
| 6   | `pollLast();`      | It removes and returns last element.        |
| 7   | `descendingSet();` | It returns `NavigableSet` in reverse order. |

**Example-1:**
```java
package collection.navigableSet;

import java.util.TreeSet;

public class NavigableSetDemo {

	public static void main(String[] args) {
		
		TreeSet<Integer> set = new TreeSet<Integer>();
		set.add(1000);
		set.add(2000);
		set.add(3000);
		set.add(4000);
		set.add(5000);
		
		System.out.println(set); // [1000, 2000, 3000, 4000, 5000]
		
		System.out.println(set.ceiling(2000)); // 2000
		
		System.out.println(set.higher(2000)); // 3000
		
		System.out.println(set.floor(3000)); // 3000
		
		System.out.println(set.lower(3000)); // 2000
		
		System.out.println(set.pollFirst()); // 1000
		
		System.out.println(set.pollLast()); // 5000
		
		System.out.println(set.descendingSet()); // [4000, 3000, 2000]
		
		System.out.println(set); // [2000, 3000, 4000]

	}

}
```
# 2. `NavigableMap`
![navigableMap](./images/navigableMap.drawio.svg)
- `NavigableMap` (I) is the child interface `SortedMap` (I) and It defines several methods for navigation purposes.
## `NavigableMap` Specific Methods

| #   | Methods            | Explanation                                               |
| --- | ------------------ | --------------------------------------------------------- |
| 1   | `floorKey(e)`      | It returns the highest **key** which is `<= e`.           |
| 2   | `lowerKey(e)`      | It returns the highest **key** which is `< e`.            |
| 3   | `ceilingKey(e)`    | It returns the lowest **key** which is `>= e`.            |
| 4   | `higherKey(e)`     | It returns the lowest **key** which is `> e`.             |
| 5   | `pollFirstEntry()` | It removes and returns the **first key-value entry**.     |
| 6   | `pollLastEntry()`  | It removes and returns the **last key-value entry**.      |
| 7   | `descendingMap()`  | It returns a `NavigableMap` in **reverse order of keys**. |
**Example-1:**
```java
package collection.navigableMap;

import java.util.TreeMap;

public class NavigableMapDemo {

	public static void main(String[] args) {
		
		TreeMap<String, String> map = new TreeMap<String, String>();
		map.put("b", "banana");
		map.put("c", "cat");
		map.put("a", "apple");
		map.put("d", "dog");
		map.put("g", "gun");
		
		System.out.println(map); // {a=apple, b=banana, c=cat, d=dog, g=gun}
		
		System.out.println(map.ceilingKey("c")); // c
		
		System.out.println(map.higherKey("e")); // g
		
		System.out.println(map.lowerKey("e")); // d
		
		System.out.println(map.pollFirstEntry()); // a=apple
		
		System.out.println(map.pollLastEntry()); // g=gun
		
		System.out.println(map.descendingMap()); // {b=banana, c=cat, d=dog}
		
		System.out.println(map); // {b=banana, c=cat, d=dog}
	}

}
```
