# SerDe
## Serialization
Serialization is a process of converting the state of an object into byte stream which can be saved into a file or stored in a DB or transmit over a network.
**`Product.java`**
```java
package serDe.serialization;

import java.io.Serializable;

public class Product implements Serializable {
	private static final long serialVersionUID = 1L;
	
	public int id;
	public String name;
	
	public Product (int id, String name) {
		this.id = id;
		this.name = name;
	}
}
```
**`Driver.java`**
```java
package serDe.serialization;

import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.ObjectOutputStream;

public class Driver {

	public static void main(String[] args) throws FileNotFoundException, IOException {
		
		Product p1 = new Product(156, "iPhone16");
		
		ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("Product.ser"));
		oos.writeObject(p1);
		System.out.println("=== Serialization Done ===");
	}

}
```
## Deserialization
DeSerialization is a process of converting byte stream into a Java object. It is the a reverse process of Serialization.
**`Driver1.java`**
```java
package serDe.serialization;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.io.ObjectInputStream;

public class Driver1 {

	public static void main(String[] args) throws FileNotFoundException, IOException, ClassNotFoundException {
		
		ObjectInputStream ois = new ObjectInputStream(new FileInputStream("Product.ser"));
		Product product = (Product)ois.readObject();
		
		System.out.println(
			"Product ID: " + product.id +
			" -> Product Name: " + product.name
		);
	}
}
```
### `SerialVersionUID`
```java
private static final long serialVersionUID = 1L;
```
1. **What is `serialVersionUID`?**
	`serialVersionUID` is a unique version number of a Serializable class, When we deserialize an object, JVM compares the `serialVersionUID` of serialized object with the current class, if both matches means deserialization successful,
	if doesn't match means deserialization fail.
---
2. **Why do we need `serialVersionUID`?**
	Suppose I have serialized an `Account` object. Later, somebody modifies the `Account` class. Now I am trying to deserialize the old serialized object using the modified class. So JVM needs some way to check whether the serialized object and current class are compatible. That's where `serialVersionUID` is used.
---
3. **What happens if `serialVersionUID` does not match?**
	If the `serialVersionUID` of the serialized object and the current class are not matching, **deserialization fails** and we get an `InvalidClassException`.
---
4. **If deserialization fails because `serialVersionUID` doesn't match, what is the solution?**
	deserialization fails because `serialVersionUID` doesn't match, this situation only occurs when developer does not write `serialVersionUID` explicitly in Serializable class before serialization.
	
	The solution is- Before serialization developer must **write** `serialVersionUID` in the Serializable class.
	
	Now JVM doesn't create it implicitly.
	
	If somebody modifies the fields of that class, instead of getting `InvalidClassException` JVM provides default values for that newly added fields.
---
### `transient`
In Java, **`transient`** is a keyword which is used to ignore an attribute (Instance variable) from being serializing an object.
For example:
```java
class Account implements Serializable {

    int accountNo;
    String name;
    transient double balance;
}
```
when I serialize the `Account` object:
```text
accountNo  → serialized
name       → serialized
balance    → NOT serialized
```
---
1. **What happens to the `transient` field after deserialization?**
	Since `transient` keyword is used to ignore an attribute (Instance variable) from being serializing an object therefore during deserialization `transient` fields get their default value.
---	
2. **Can we use `transient` with a method?**
	No. `transient` is used with an attribute (Instance variable).
---
3. **Can we use `transient` with a `static` variable?**
	`transient` works only for object variables or we can say **Instance Variables**. Since static belongs to class and if we use static for a variable so it is not serialized along with the object.
	
	Therefore, there is no need to use `transient` with a static variable.
---
4. **What happens if the class has a constructor during serialization, but we remove that constructor before deserialization? Will deserialization fail?**
	constructor is not require during deserialization even if serialized class had the constructor.
	Therefore, if the object was serialized successfully and later we remove the constructor of that class, deserialization can still work.
	
	**Why?**
	Because during deserialization, Java **does not call the constructor of the Serializable class to recreate the object**. The object's serialized state is restored from the serialized data.
	> [!NOTE]
	> Make sure the class has `serialVersionUID` then removing constructor before deserialization does not give any error.
	
	---
	