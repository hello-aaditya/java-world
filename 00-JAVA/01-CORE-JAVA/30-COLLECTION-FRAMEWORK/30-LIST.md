# `List` (I)
- `List` is child interface of `Collection`.
- If we want to represent a group of individual objects as a single entity where duplicates are allowed and insertion order must be preserved then we should go for `List`.
- We can preserve insertion order via index and we can differentiate duplicate objects by using index hence index will play very important role in `List`.
- `List` interface defines the following specific methods:
	1. **`void add(int index, Object o)`**
	2. **`boolean addAll(int index, Collection)`**
	3. **`Object get(int index)`**
	4. **`Object remove(int index)`**
	5. **`Object set(int index, Object newObject)`** → to replace the element present at specified index with provided Object and returns old object
	6. **`int indexOf(Object o)`** → returns index of first occurrence of 'o'
	7. **`int lastIndexOf(Object)`**
	8. **`ListIterator listIterator();`**
	![List](list.drawio.svg)

