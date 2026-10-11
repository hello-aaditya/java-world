# `WeakHashMap`
1. It is exactly same as `HashMap` except the following difference:
	1. In the case of `HashMap`, even though object does not have any reference it is not eligible for GC, if it is associated with `HashMap` i.e., **`HashMap` dominates GC**.
	2. But in the case of `WeakHashMap`, if object does not contain any references it is eligible for GC even though object associated with `WeakHashMap` i.e. **GC dominates `WeakHashMap`**.

**Example-1**  (**`HashMap` dominates GC**)
```java
package collection.weakHashMap;

import java.util.HashMap;

class Temp {
	
	@Override
	public String toString() {
		return "temp";
	}
	
	@Override
	public void finalize() {
		System.out.println("Finalize Method Called");
	}
	
}

public class HashMapDemo {

	public static void main(String[] args) throws InterruptedException {
		
		Temp temp = new Temp();
		
		HashMap map = new HashMap();
		map.put(temp, "Alpha");
		System.out.println(map); // {temp=Alpha}
		
		temp = null;
		
		System.gc();
		
		Thread.sleep(5000);
		
		System.out.println(map); // {temp=Alpha}
	}

}
```
**Example-2**  (**GC dominates `WeakHashMap`**)
```java
package collection.weakHashMap;

import java.util.WeakHashMap;

class Temp {
	
	@Override
	public String toString() {
		return "temp";
	}
	
	@Override
	public void finalize() {
		System.out.println("Finalize Method Called");
	}
	
}

public class WeakHashMapDemo {

	public static void main(String[] args) throws InterruptedException {
		
		Temp temp = new Temp();
		
		WeakHashMap map = new WeakHashMap();
		map.put(temp, "Alpha");
		System.out.println(map); // {temp=Alpha}
		
		temp = null;
		
		System.gc();
		
		Thread.sleep(5000);
		
		System.out.println(map); // {}
	}

}
```
- In the above **Example-1** `Temp` object not eligible for GC because it is associated with `HashMap`.
	In this case output is `{temp=Alpha}` both times.
- In the above **Example-2** we have replaced `HashMap` with `WeakHashMap` then `temp` object eligible for GC.
  In this case output is `{temp=Alpha}` and second time output is `{}`.