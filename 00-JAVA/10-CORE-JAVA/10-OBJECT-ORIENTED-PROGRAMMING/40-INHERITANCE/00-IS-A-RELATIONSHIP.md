# IS-A Relationship
- IS-A relationship is also known as Inheritance.
- The main advantage of IS-A relationship is Code-Reusability.
- By using **`extends`** we can implement IS-A relationship.
![IS-A-relationship-demo1](IS-A-relationship-demo1.drawio.svg)

**Conclusions:**
1. Whatever methods a Parent has, by-default available to Child. Hence, using Child reference we can call both Parent and Child class methods.
2. Whatever methods a Child has, by-default not available to the Parent. Hence, on the Parent reference, we can't call Child-specific methods.
3. Parent reference can be used to hold Child object. But using that reference we can't call Child specific methods but we can call the methods present in Parent class.
4. Parent reference can be used to hold Child object but Child reference can't be used to hold Parent object.
![inheritance-demo-example1](inheritance-demo-example1.drawio.svg)

>[!NOTE]
>- The most common methods which are applicable for any type of Child, we have to define in Parent class.
>- The specific methods which are applicable for a particular Child, we have to define in Child class.

![object-class-inheritance](object-class-inheritance.drawio.svg)

- Total Java API is implemented based on inheritence concept.
- The most common methods which are applicable for any Java object are defined in **Object** class and Hence, every class in Java is a Child class of Object either directly or indirectly. So that, Object class methods by-default available to every Java class without rewriting. Due to this, **`Obejct`** class acts as root for all Java classes.
- `Throwable` class defines the most common methods which are required for every `Exception` and `Error` classes. Hence, this class acts as root for Java Exception hierarchy.
## Multiple Inheritance
![multiple-inheritance-not-supported](multiple-inheritance-not-supported.drawio.svg)
A Java class can't extend more than one class at a time. Hence, Java won't provide support for **Multiple Inheritance** in class.

![multiple-inheritance-extended-by-object-also](multiple-inheritance-extended-by-object-also.drawio.svg)

>[!NOTE]
>1. If our class doesn't extend any other class then only our class is direct Child class of Object. (see the diagram-1)
>2. If our class extend any other class then our class is indirect Child class of Object. (see the diagram-2)

Either directly or indirectly, Java won't provide support for Multiple Inheritance with respect to classes.

---
Q] Why Java won't provide support for Multiple Inheritance?

Answer →

There may be a chance of ambiguity problem. Hence, Java won't provide support for Multiple Inheritance.
![multiple-inheritance-generates-ambiguity-problem](multiple-inheritance-generates-ambiguity-problem.drawio.svg)

But interface can extend any no. of interfaces simultaneously. Hence, Java provides support for Multiple inheritance with respect to interfaces.
![multiple-inheritance-WRT-interface](multiple-inheritance-WRT-interface.drawio.svg)

Q] Why ambiguity problem won't be there in interfaces ?

Answer →

![why-multiple-inheritance-WRT-interface](why-multiple-inheritance-WRT-interface.drawio.svg)

Even though mutiple method declarations are available but implementation is unique and hence, there is no chance of ambiguity problem in interfaces.
>[!NOTE]
>Strictly speaking, through interfaces we won't get any inheritance.

## Cyclic Inheritance
- Cyclic Inheritance is not allowed in Java. of course it is not required.
![cyclic-inheritance](cyclic-inheritance.drawio.svg)