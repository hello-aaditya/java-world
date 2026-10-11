# Functional Interface
> A Functional Interface is an interface that contains only one abstract method. 
> it serves as a blueprint for a lambda expression or method reference. 

## Features of Functional Interface
1. FI contains a SAM.
2. FI may contain `@FunctionalInterface`.
	The `@FunctionalInterface` annotation ensures that an interface can contain only SAM. if more than one abstract method is present, the compiler gives an error:
	**`Unexpected @FunctionalInterface annotation`**. Although this annotation is optional.
3. Along with SAM, FI can also contain default & static methods.
