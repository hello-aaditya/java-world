# `throw` Keyword
![throw-keyword-visualization](./images/throw-keyword-visualization.drawio.svg)

Sometimes we can create exception object explicitly. we can hand-over to JVM manually. for this we have to use **`throw`** keyword.

![throwing-expcetion-manually](./images/throwing-expcetion-manually.drawio.svg)

Hence the main objective of `throw` keyword is to handover our created exception object to JVM manually.
The result of the following two program is exactly same.


| Without `throw`                                                                             | With `throw`                                                                                   |
| ------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| ![](./images/without-throw-keyword.drawio.svg)                                              | ![with-throw-keyword](./images/with-throw-keyword.drawio.svg)                                  |
| In this case, `main()` method is responsible to create exception object and handover to JVM | In this case, programmer is creating exception object explicitly and handover to JVM manually. |
Best use of `throw` keyword is for user-defined exceptions or customized exceptions.

**Case-1**: `throw e` if `e` refers null then we will get `NullPointerException`.
![exception-with-and-without-null](./images/exception-with-and-without-null.drawio.svg)

**Case-2**: After `throw` statement we are not allowed to write any statement directly otherwise we will get compile-time error saying- "Unreachable statement".
![with-unreachable-and-without-throw](./images/with-unreachable-and-without-throw.drawio1.svg)
**Case-3**: We can use `throw` keyword only for throwable types. if we are trying to use for normal java objects, we will get compile-time error saying- "Incompatible type".
![throw-class-object-vs-throwable-object](./images/throw-class-object-vs-throwable-object.drawio.svg)

