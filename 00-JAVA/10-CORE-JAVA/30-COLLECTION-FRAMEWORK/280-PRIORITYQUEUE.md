# `PriorityQueue`
1. if we want to represent a group of individual objects prior to processing according to some priority then we should go for `PriorityQueue`.
2. The priority can be either default natural sorting order or customized sorting order defined by `Comparator`.
3. Insertion order is not preserved and it is based on some priority.
4. Duplicate objects are not allowed.
5. If we are depending on default natural sorting order compulsory object should be homogeneous and comparable otherwise we will get `RuntimeException` : `ClassCastException`.
6. If we are defining our own sorting by `COmparator` then objects need not be homogeneous and comparable.
7. `null` is not allowed even as the first element also.
# Constructors

| #   | Constructor                                                                | Explanation                                                                                                                                    |
| --- | -------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | `PriorityQueue pq = new PriorityQueue();`                                  | Creates an empty `PriorityQueue` with default initial capacity 11 and all objects will be inserted according to default natural sorting order. |
| 2   | `PriorityQueue pq = new PriorityQueue(int initialCapacity);`               |                                                                                                                                                |
| 3   | `PriorityQueue pq = new PriorityQueue(int initialCapacity, Comparator c);` |                                                                                                                                                |
| 4   | `PriorityQueue pq = new PriorityQueue(SortedSet s);`                       |                                                                                                                                                |
| 5   | `PriorityQueue pq = new PriorityQueue(Collection c);`                      |                                                                                                                                                |
**Example-1:**
```java
import java.util.PriorityQueue;

public class PriorityQueueDemo {

	public static void main(String[] args) {
		
		PriorityQueue pq = new PriorityQueue();
		
		System.out.println(pq.peek()); // null
//		System.out.println(pq.element()); // RE : NSEE
		
		for (int i=0; i<=10; i++) {
			pq.offer(i);
		}
		
		System.out.println(pq); // [0, 1, 2, ..., 10]
		
		System.out.println(pq.poll()); // 0
		
		System.out.println(pq); // [1, 2, ..., 10]
	}
}
```
>[!NOTE]
Some platforms won't provide proper support for thread priority and PriorityQueue.

**Example-2:**
```java
package collection.queue.priorityQueue;

import java.util.Comparator;
import java.util.PriorityQueue;

class MyComparator implements Comparator {
	
	@Override
	public int compare(Object obj1, Object obj2) {
		String s1 = (String)obj1;
		String s2 = (String)obj2;
		
		return -s1.compareTo(s2);
	}
}

public class PriorityQueueDemo2 {

	public static void main(String[] args) {
		
		PriorityQueue pq = new PriorityQueue(15, new MyComparator());

		pq.offer("A");
		pq.offer("X");
		pq.offer("L");
		pq.offer("B");
		
		System.out.println(pq); // [X, B, L, A]
	}

}
```