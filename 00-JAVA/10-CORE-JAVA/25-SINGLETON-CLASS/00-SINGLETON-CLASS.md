# what is singleton class?
for any Java class, if we are allowed to create only one object, such type of class is called Singleton class.
Example- Runtime, BusinessDelegate, ServiceLocator etc.
## Advantage of Singleton Class
if several classes have same requirement then it is not recommended to create separate object for every requirement.
we have to create only one object and we can re-use the same object for every similar requirement so that performance & memory utilization will be improved.

This is the central idea of singleton classes.
## Example
Runtime r1 = Runtime.getRuntime();
Runtime r2 = Runtime.getRuntime();
.
.
.
Runtime r1lakh = Runtime.getRuntime();
## How to create our own Singleton classes?
we can create our own singleton classes for this we have to use private constructor and private static variable and public factor method.

Approach-1:

```java
class Test {
	private static Test t = new test;

	private Test() {

	}

	public static Test getTest() {
		return t;
	}
}
```
Test t1 = Test.getTest();
Test t2 = Test.getTest();
.
.
.
Test t1lakh = Test.getTest();

Runtime class is internally implemented by using this approach.

Approach-2:
```java
class Test {
	private static Test t = null;

	private Test() {

	}

	public static Test getTest() {

		if (t == null) {
			t = new Test();
		}

		return t;
	}
}
```

Test t1 = Test.getTest();
Test t2 = Test.getTest();
.
.
.
Test t1lakh = Test.getTest();

At any point of time for Test class we can only create only one object hence test class is a singleton class.
## class is not final but we are not allowed to create child class, how it is possible?
By declaring every constructor as private we can restrict child class creation.
### Example:

```java
class P {
	
	private t() {

	}
}
```
for the above class it is impossible to create child class.