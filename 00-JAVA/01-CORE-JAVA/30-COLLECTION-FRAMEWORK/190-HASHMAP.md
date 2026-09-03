# `HashMap`
1. The underlying data structure is **Hash Table**.
2. Insertion order is not preserved and it is based on **hashcode of keys**.
3. Duplicate keys are not allowed but values can be duplicated.
4. Heterogeneous objects are allowed for both keys & values.
5. `null` is allowed for key (only once).
6. `null` is allowed for values (any no. of time).
7. `HashMap` implements `Serializable` & `Cloneable` interfaces but not `RandomAccess` interface.
8. `HashMap` is the best choice if our frequent operation is search operation.
## Constructors
| #   | Syntax                                                             | Explanation                                                                                                              |
| --- | ------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| 1   | `HashMap map = new HashMap();`                                     | Creates an empty `HashMap` object with:<br>- default initial capacity 16.<br>- default Fill Ratio (or Load factor) 0.75. |
| 2   | `HashMap map = new HashMap(int initialCapacity);`                  | Creates an empty `HashMap` object with:<br>- specified initial capacity.<br>- default Fill Ratio 0.75.                   |
| 3   | `HashMap map = new HashMap(int initialCapacity, float fillRatio);` | Creates an empty `HashMap` object with:<br>- specified initial capacity.<br>- specified Fill Ratio.                      |
| 4   | `HashMap map = new HashMap(Map m);`                                | Creates an equivalent `HashMap` for the given `Map` .                                                                    |
**Example-1**:
```java
package collection.map.hashMap;

import java.util.Collection;
import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;
import java.util.Set;

public class HashMapDemo1 {

	public static void main(String[] args) {
		
		HashMap map = new HashMap();
		
		map.put("Alpha", 200);
		map.put("Beta", 150);
		map.put("Charlie", 250);
		map.put("Delta", 500);
		
		System.out.println(map); // {key=Value, Key=value, ...}
		
		System.out.println(map.put("Alpha", 700)); // 200
		
		Set set = map.keySet();
		System.out.println(set); // [key, key, ...]
		
		Collection c = map.values();
		System.out.println(c); // [values, values, ...]

		Set set1 = map.entrySet();
		System.out.println(set1); // [key=Value, Key=value, ...]
		
		Iterator itr = set1.iterator();
		while (itr.hasNext()) {
			Map.Entry map1 = (Map.Entry)itr.next();
			
			System.out.println(map1.getKey() + "------" + map1.getValue());
			
			if (map1.getKey().equals("Delta")) {
				map1.setValue(10_000);
			}
		}
		System.out.println(map);
		
	}

}
```
## Difference between `HashMap` and `Hashtable`

| #   | `HashMap`                                                                                                                                                                                                 | `Hashtable`                                                                                                                                                                                       |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | Every method present in `HashMap` is non-synchronized.                                                                                                                                                    | Every method present in `Hashtable` is synchronized.                                                                                                                                              |
| 2   | At a time mutiple threads are allowed to operate on `HashMap` object and hence it is not thread-safe.<br>![diff-between-arraylist-vs-vector-al-part](diff-between-arraylist-vs-vector-al-part.drawio.svg) | At a time only one thread is allowed to operate on `Hashtable` and hence it is thread-safe.<br>![diff-between-arraylist-vs-vector-vec-part](diff-between-arraylist-vs-vector-vec-part.drawio.svg) |
| 3   | Relatively performance is high because threads are not required to wait to operate on `HashMap` object.                                                                                                   | Relatively performance is low because threads are required to wait to operate on `Hashtable` object.                                                                                              |
| 4   | `null` is allowed for both key & value.                                                                                                                                                                   | `null` is not allowed for keys & values otherwise we will get `NullPointerException`.                                                                                                             |
| 5   | Introduced in Java-1.2V and it is not legacy.                                                                                                                                                             | Introduced in Java-1.0V and it is legacy.                                                                                                                                                         |
## How to get Synchronized version of `HashMap` Object?
By-default `HashMap` is non-synchronized but we can get synchronized version of `HashMap` object by using `synchronizedMap()` method of `Collections` class.
`Map map = Collections.synchronizedMap(m);`
**Example**:
![synchronized-vs-non-synchronized-hashMap](./images/synchronized-vs-non-synchronized-hashMap.drawio.svg)
