# Rules for Abstract Methods
1. **An abstract method has no body — only the method name.**
2. **An abstract method must end with a semicolon `;`.**
3. **Abstract methods can only exist inside an abstract class or interface.**
4. **If a class has even one abstract method, the class must be abstract.**
5. **Child classes must implement all abstract methods, otherwise the child must also be abstract.**
6. **Abstract methods cannot be `private` because children need access to override them.**
7. **Abstract methods cannot be `final` because final methods cannot be overridden.**
8. **Abstract methods cannot be `static` because static methods cannot be overridden.**

# Rules for Abstract Classes
1. **An abstract class cannot be instantiated — you cannot create its object.**
2. **An abstract class can have both abstract and concrete methods.**
3. **An abstract class can have constructors.**
4. **An abstract class can have variables, including final, non-final, static, and instance variables.**
5. **An abstract class can have static methods — but they must be concrete.**
6. **An abstract class can extend another class (abstract or concrete).**
7. **An abstract class can implement interfaces.**
8. **Child classes must complete all abstract methods of the parent unless they are abstract themselves.**