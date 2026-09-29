# Immutable classes
## What is an Immutable Class?
> An immutable class is a class whose object's state cannot be changed after it is created. Once an object is created, its data remains the same throughout its lifetime.

Rules to be a class as an Immutable class:
- All data members must be `private` and `final`.
- class must not contain any setter methods.
- All data members must be initialize through constructor.
- class must not allow inheritance ans we can achieve it by making class as final or make it's constructor as private or make class as sealed (Java 17+).
- If class contains mutable objects(Collections frameworks, StringBuilder, StringBuffer etc.), return their copies instead of the original objects.

#### Product.java
```java
package com.immutableclass;

import java.util.ArrayList;
import java.util.List;

// final class -> cannot be inherited
public final class Product {

    // private + final -> values cannot be modified after object creation
    private final String productId;
    private final String productName;
    private final List<String> tags; // Mutable object

    // Constructor initializes all data members
    public Product(String productId, String productName, List<String> tags) {

        this.productId = productId;
        this.productName = productName;

        /*
         * DEFENSIVE COPY
         * Store a copy instead of the original list.
         */
        this.tags = new ArrayList<>(tags);
    }

    public String getProductId() {
        return productId;
    }

    public String getProductName() {
        return productName;
    }

    public List<String> getTags() {

        /*
         * DEFENSIVE COPY
         * Return a copy instead of the original list.
         */
        return new ArrayList<>(tags);
    }

    public void displayProductDetails() {
        System.out.println("\n===== PRODUCT DETAILS =====");
        System.out.println("Product ID   : " + productId);
        System.out.println("Product Name : " + productName);
        System.out.println("Tags         : " + tags);
        System.out.println("===========================\n");
    }
}
```
#### Driver.java
```java
package com.immutableclass;

import java.util.ArrayList;
import java.util.List;

public class Driver {

    public static void main(String[] args) {

        List<String> productTags = new ArrayList<>();

        productTags.add("Electronics");
        productTags.add("Wireless");

        Product product = new Product(
                "P101",
                "Bluetooth Speaker",
                productTags);

        product.displayProductDetails();

        /*
         * Try to modify the original list.
         */

        productTags.add("Gaming");

        System.out.println("Original List modified.\n");

        product.displayProductDetails();

        /*
         * Try to modify the list returned by getter.
         */

        List<String> copiedTags = product.getTags();

        copiedTags.add("Portable");

        System.out.println("Getter List modified.\n");

        product.displayProductDetails();
    }
}
```
#### Output
```text
===== PRODUCT DETAILS =====
Product ID   : P101
Product Name : Bluetooth Speaker
Tags         : [Electronics, Wireless]
===========================

Original List modified.

===== PRODUCT DETAILS =====
Product ID   : P101
Product Name : Bluetooth Speaker
Tags         : [Electronics, Wireless]
===========================

Getter List modified.

===== PRODUCT DETAILS =====
Product ID   : P101
Product Name : Bluetooth Speaker
Tags         : [Electronics, Wireless]
===========================
```