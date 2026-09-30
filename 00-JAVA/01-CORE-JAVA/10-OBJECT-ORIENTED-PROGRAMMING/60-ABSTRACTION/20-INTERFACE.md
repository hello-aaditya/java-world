# Interface
> An **Interface** is like a **blueprint** that defines what a class should do but not how it should do it.
## Syntax
```java
public interface IInterfaceName {

	// DATA-MEMBERS (OPTIONAL) ARE BY DEFAULT- public static final
	dataType VARIABLE_NAME = value; 
	
	// MEMBER-METHODS ARE BY DEFAULT public & abstract
	returnType methodname();
}
```
## Rules
1. An Interface provides 100% abstraction means it contains **only abstract methods** (before Java 8) by only providing **method declaration and no implementations**. those methods are by default **public** & **abstract** .
2. In Java 8, along with abstract methods interface also contains variables which are by default- **public**, **static** and **final**.
3. Any class that implements an interface must provide implementations for all its method otherwise the class will become abstract class.
4. An Interface cannot be instantiated directly.