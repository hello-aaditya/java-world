## Question 1 — Iterator with `List`

### Order Cleanup Using `Iterator`

You are given an `Order` class with the following fields:

```java
long orderId;
String customerName;
Status status;
double amount;
boolean paymentConfirmed;
```
The `Status` enum contains exactly these values:
```java
PLACED
PROCESSING
SHIPPED
CANCELLED
```
A list of orders is maintained using:
```java
List<Order> orders = new ArrayList<>();
```
The list contains the following 10 orders in the given order:
```java
Order o1 = new Order(1001, "Alpha", Status.PLACED, 4599.00, true);
Order o2 = new Order(1002, "Beta", Status.CANCELLED, 2199.50, false);
Order o3 = new Order(1003, "Charlie", Status.PROCESSING, 7899.00, true);
Order o4 = new Order(1004, "Delta", Status.SHIPPED, 12499.00, true);
Order o5 = new Order(1005, "Epsilon", Status.CANCELLED, 1599.00, true);
Order o6 = new Order(1006, "Gamma", Status.PLACED, 3299.75, false);
Order o7 = new Order(1007, "Tango", Status.CANCELLED, 849.00, false);
Order o8 = new Order(1008, "Victor", Status.PROCESSING, 6799.00, true);
Order o9 = new Order(1009, "Peter", Status.SHIPPED, 2499.50, true);
Order o10 = new Order(1010, "Lambda", Status.CANCELLED, 5399.00, false);
```
These objects are added to `orders` in the same sequence from `o1` to `o10`.
### Requirement
Process the `orders` list using an **`Iterator<Order>`**.
During the traversal:
1. An order must be **removed from the list** if:
    - its `status` is `Status.CANCELLED`, **and**
    - its `paymentConfirmed` is `false`.
2. An order must **not be removed** if either of the above conditions is false.
3. Every order that is **not removed** must be printed using exactly this information:
    - Order ID
    - Customer Name
    - Status
    - Amount
    - Payment Confirmed
4. Orders that are removed must **not be printed**.
5. The relative order of all remaining orders must be preserved.
### Restrictions
- You **must** use `Iterator<Order>` for traversal.
- You **must** use the iterator's `remove()` method to remove an order.
- Do not use `List.remove()`.
- Do not use `removeIf()`.
- Do not use Streams.
- Do not create another `List` to store the remaining orders.
- Do not use index-based traversal or index-based removal.
### Expected Result
After processing, `orders` must contain exactly these orders, in this order:
```text
1001 Alpha   PLACED      4599.00   true
1003 Charlie PROCESSING  7899.00   true
1004 Delta   SHIPPED     12499.00  true
1005 Epsilon CANCELLED   1599.00   true
1006 Gamma   PLACED      3299.75   false
1008 Victor  PROCESSING  6799.00   true
1009 Peter   SHIPPED     2499.50   true
```
The orders removed must be:
```text
1002 Beta    CANCELLED   2199.50  false
1007 Tango   CANCELLED    849.00  false
1010 Lambda  CANCELLED   5399.00  false
```

**`Order.java`**
```java
package collection.iterator;

enum Status {
	PLACED,
	PROCESSING,
	SHIPPED,
	CANCELLED
}
public class Order {
	long orderId;
	String customerName;
	Status status;
	double amount;
	boolean paymentConfirmed;
	
	
	public Order(
		long orderId,
		String customerName,
		Status status,
		double amount,
		boolean paymentConfirmed
	) {
		super();
		this.orderId = orderId;
		this.customerName = customerName;
		this.status = status;
		this.amount = amount;
		this.paymentConfirmed = paymentConfirmed;
	}	
	
}
```
**`Driver.java`**
```java
package collection.iterator;

import java.util.ArrayList;
import java.util.List;

import java.util.Iterator;

public class Driver {

	public static void main(String[] args) {
		
		Order o1 = new Order(1001, "Alpha", Status.PLACED, 4599.00, true);
		Order o2 = new Order(1002, "Beta", Status.CANCELLED, 2199.50, false);
		Order o3 = new Order(1003, "Charlie", Status.PROCESSING, 7899.00, true);
		Order o4 = new Order(1004, "Delta", Status.SHIPPED, 12499.00, true);
		Order o5 = new Order(1005, "Epsilon", Status.CANCELLED, 1599.00, true);
		Order o6 = new Order(1006, "Gamma", Status.PLACED, 3299.75, false);
		Order o7 = new Order(1007, "Tango", Status.CANCELLED, 849.00, false);
		Order o8 = new Order(1008, "Victor", Status.PROCESSING, 6799.00, true);
		Order o9 = new Order(1009, "Peter", Status.SHIPPED, 2499.50, true);
		Order o10 = new Order(1010, "Lambda", Status.CANCELLED, 5399.00, false);
		
		List<Order> orders = new ArrayList<>();
		orders.add(o1);
		orders.add(o2);
		orders.add(o3);
		orders.add(o4);
		orders.add(o5);
		orders.add(o6);
		orders.add(o7);
		orders.add(o8);
		orders.add(o9);
		orders.add(o10);
		
		Iterator<Order> itr = orders.iterator();
		
		while (itr.hasNext()) {
			Order o = itr.next();
			
			if (o.status == Status.CANCELLED && o.paymentConfirmed == false) {
				itr.remove();
			} else {
			
				System.out.println(
					"Order ID: " + o.orderId +
					" -> Customer Name: " + o.customerName +
					" -> Status: " + o.status +
					" -> Amount: " + o.amount +
					" -> Is Payment Confirmed: " + o.paymentConfirmed
				);
			}
		}
	}

}
```
## Q2 — `Iterator` with `Set`
### Permission Cleanup Using `Iterator`
You are given an `Permission` class with the following fields:
```java
String permissionCode;
String module;
Environment environment;
boolean active;
```
The `Environment` enum contains exactly these values:
```java
PROD,
TEST,
DEV
```
A set of permissions is maintained using:
```java
Set<Permission> permissions = new LinkedHashSet<>();
```
The following 10 permissions are added to the set in this order:
```java
Permission p1 = new Permission("USER_READ", "USER", Environment.PROD, true);
Permission p2 = new Permission("USER_DELETE", "USER", Environment.PROD, false);
Permission p3 = new Permission("REPORT_CREATE", "REPORT", Environment.TEST, false);
Permission p4 = new Permission("REPORT_EXPORT", "REPORT", Environment.PROD, false);
Permission p5 = new Permission("CONFIG_READ", "CONFIG", Environment.DEV, false);
Permission p6 = new Permission("USER_UPDATE", "USER", Environment.PROD, true);
Permission p7 = new Permission("ORDER_CANCEL", "ORDER", Environment.PROD, false);
Permission p8 = new Permission("ORDER_VIEW", "ORDER", Environment.TEST, true);
Permission p9 = new Permission("AUDIT_READ", "AUDIT", Environment.PROD, false);
Permission p10 = new Permission("SYSTEM_ADMIN", "SYSTEM", Environment.DEV, true);
```
## Requirement
Traverse the `permissions` set using an **`Iterator<Permission>`**.
During traversal:
1. A permission must be removed **only when both conditions are true**:
    - `active` is `false`
    - `environment` is `Environment.PROD`
2. A permission must remain in the set if:
    - it is active, regardless of its environment, **or**
    - its environment is `TEST` or `DEV`, regardless of its active status.
3. Every permission that is **not removed** must be printed.
4. For every printed permission, display:
    - Permission Code
    - Module
    - Environment
    - Active status
5. The relative insertion order of the remaining permissions must be preserved.
## Restrictions
- You **must** use `Iterator<Permission>`.
- You **must** use `Iterator.remove()` to remove permissions.
- Do not use `Set.remove()`.
- Do not use `removeIf()`.
- Do not use Streams.
- Do not create another `Set`, `List`, or other collection to hold the remaining permissions.
- Modify the original `permissions` set directly.
**`Permission.java`**
```java
package collection.iterator;

enum Environment {
	PROD,
	TEST,
	DEV
}
public class Permission {
	String permissionCode;
	String module;
	Environment environment;
	boolean active;
	
	public Permission
	(
		String permissionCode,
		String module,
		Environment environment,
		boolean active
	) {
		super();
		this.permissionCode = permissionCode;
		this.module = module;
		this.environment = environment;
		this.active = active;
	}
}
```
**`Driver.java`**
```java
package collection.iterator;

import java.util.Iterator;
import java.util.LinkedHashSet;
import java.util.Set;


public class Driver {

	public static void main(String[] args) {
		
		Permission p1 = new Permission("USER_READ", "USER", Environment.PROD, true);
		Permission p2 = new Permission("USER_DELETE", "USER", Environment.PROD, false);
		Permission p3 = new Permission("REPORT_CREATE", "REPORT", Environment.TEST, false);
		Permission p4 = new Permission("REPORT_EXPORT", "REPORT", Environment.PROD, false);
		Permission p5 = new Permission("CONFIG_READ", "CONFIG", Environment.DEV, false);
		Permission p6 = new Permission("USER_UPDATE", "USER", Environment.PROD, true);
		Permission p7 = new Permission("ORDER_CANCEL", "ORDER", Environment.PROD, false);
		Permission p8 = new Permission("ORDER_VIEW", "ORDER", Environment.TEST, true);
		Permission p9 = new Permission("AUDIT_READ", "AUDIT", Environment.PROD, false);
		Permission p10 = new Permission("SYSTEM_ADMIN", "SYSTEM", Environment.DEV, true);
		
		Set<Permission> permissions = new LinkedHashSet<>();

		permissions.add(p1);
		permissions.add(p2);
		permissions.add(p3);
		permissions.add(p4);
		permissions.add(p5);
		permissions.add(p6);
		permissions.add(p7);
		permissions.add(p8);
		permissions.add(p9);
		permissions.add(p10);
		
		Iterator<Permission> itr = permissions.iterator();
		
		while (itr.hasNext()) {
			Permission p = itr.next();
			
			if (!p.active && p.environment == Environment.PROD) {
				itr.remove();
			} else {
				System.out.println(
					"Permission Code: " + p.permissionCode +
					" -> Module: " + p.module +
					" -> Environment: " + p.environment +
					" -> Is Active: " + p.active
				);
			}
		}
	}

}
```
## Q3 — Iterator with `Map`
### Scenario: Session Expiration Cleanup
You are given an `Session` class with the following fields:
```java
String sessionId;
long userId;
long lastAccessTime;
boolean active;
```
The application maintains active user sessions in the following map:
```java
Map<String, Session> sessions = new LinkedHashMap<>();
```
The map key is the `sessionId` of the corresponding `Session` object.
Add these 10 sessions to the map in the given order:
```java
Session s1 = new Session("S101", 501, 1200, true);
Session s2 = new Session("S102", 502, 800, false);
Session s3 = new Session("S103", 503, 900, true);
Session s4 = new Session("S104", 504, 700, false);
Session s5 = new Session("S105", 505, 1500, false);
Session s6 = new Session("S106", 506, 600, true);
Session s7 = new Session("S107", 507, 1100, false);
Session s8 = new Session("S108", 508, 400, false);
Session s9 = new Session("S109", 509, 1300, true);
Session s10 = new Session("S110", 510, 750, false);
```
#### Cleanup Rule
The application has already defined the expiration threshold as:
```java
long expiryThreshold = 1000;
```
A session is considered **expired only when both conditions are satisfied**:
```text
active == false
AND
lastAccessTime < expiryThreshold
```
Therefore, with:
```java
expiryThreshold = 1000;
```
a session with `lastAccessTime` exactly `1000` is **not** expired.
### Requirement
Traverse the `sessions` map and remove every expired session.
You must:
1. Iterate through `sessions.entrySet()`.
2. Use `Iterator<Entry<String, Session>>`.
3. Remove expired sessions using `Iterator.remove()`.
4. Print every session that is **not removed**.
5. Print the following information for every remaining session:
    - Session ID
    - User ID
    - Last Access Time
    - Active status
6. Preserve the existing insertion order of the remaining entries.
### Restrictions
Do **not** use:
- `sessions.remove()`
- `removeIf()`
- Streams
- another `Map` 
- another collection for storing the remaining sessions
The original `sessions` map must be modified directly during iteration.
**`Session.java`**
```java
package collection.iterator;

public class Session {
	String sessionId;
	long userId;
	long lastAccessTime;
	boolean active;
	
	public Session(String sessionId, long userId, long lastAccessTime, boolean active) {
		super();
		this.sessionId = sessionId;
		this.userId = userId;
		this.lastAccessTime = lastAccessTime;
		this.active = active;
	}
}
```
**`Driver.java`**
```java
package collection.iterator;

import java.util.Iterator;
import java.util.LinkedHashMap;
import java.util.Map;
import java.util.Map.Entry;
import java.util.Set;

public class Driver {

	public static void main(String[] args) {
		
		Session s1 = new Session("S101", 501, 1200, true);
		Session s2 = new Session("S102", 502, 800, false);
		Session s3 = new Session("S103", 503, 900, true);
		Session s4 = new Session("S104", 504, 700, false);
		Session s5 = new Session("S105", 505, 1500, false);
		Session s6 = new Session("S106", 506, 600, true);
		Session s7 = new Session("S107", 507, 1100, false);
		Session s8 = new Session("S108", 508, 400, false);
		Session s9 = new Session("S109", 509, 1300, true);
		Session s10 = new Session("S110", 510, 750, false);
		
		Map<String, Session> sessions = new LinkedHashMap<>();
		sessions.put(s1.sessionId, s1);
		sessions.put(s2.sessionId, s2);
		sessions.put(s3.sessionId, s3);
		sessions.put(s4.sessionId, s4);
		sessions.put(s5.sessionId, s5);
		sessions.put(s6.sessionId, s6);
		sessions.put(s7.sessionId, s7);
		sessions.put(s8.sessionId, s8);
		sessions.put(s9.sessionId, s9);
		sessions.put(s10.sessionId, s10);
		
		
		Set<Entry<String, Session>> entrySet = sessions.entrySet();
		Iterator<Entry<String, Session>> itr = entrySet.iterator();
		
		long expiryThreshold = 1000;
		
		while (itr.hasNext()) {
			Entry<String, Session> entry = itr.next();
			
			String sessionId = entry.getKey();
			Session s = entry.getValue();
			
			if (!s.active && s.lastAccessTime < expiryThreshold) {
				itr.remove();
			} else {
				System.out.println(
					"Session ID: " + sessionId +
					" -> User ID: " + s.userId +
					", Last Access Time: " + s.lastAccessTime +
					", Active: " + s.active
				);
			}
		}
		
	}

}
```