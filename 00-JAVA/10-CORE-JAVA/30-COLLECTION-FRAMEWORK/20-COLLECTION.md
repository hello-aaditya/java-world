# `Collection` (I)
- If we want to represent a group of individual objects as a single entity then we should go for `Collection`.
- `Collection` interface defines the most common method which are applicable for any collection object.
	Example
	1. `boolean add(Object o)`
	2. `boolean addAll(Collection c)`
	3. `boolean remove(Object o)`
	4. `boolean removeAll(Collection c)`
	5. `boolean retainAll(Collection c)` → to remove all objects except those present in c.
	6. `void clear()`
	7. `boolean contains(Object o)`
	8. `boolean containsAll(Collection c)`
	9. `int size();`
	10. `Object[] toArray();`
	11. `Iterator iterator()`

>[!NOTE]
There is no concrete class which implements `Collection` interface directly.
