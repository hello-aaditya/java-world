- An array is an indexed collection of fixed no. of homogeneous data elements.
- The main advantage of array is- we can represent multiple values by using single variable so that readability of the code will be improved.
## Limitations of `Array`
1. Arrays are fixed in size that is- once we create an array there is no chance of increasing or decreasing the size based on our requirement. due to this, to use array's concept compulsory we should know the size in advance which may not possible always.
2. Array can hold only homogeneous data  type element. example- 
	![Array-Limitation](array-limitation.drawio.svg)

	we can solve this problem by using `Object` type arrays
	![Solution](object-type-array.drawio.svg)

3. Arrays concept is not implemented based on some standard data structure and hence ready-made method support is not available. for every requirement we have to write the code explicitly which increases complexity of programming.

To overcome above problems of arrays we should go for **Collections** concept.
1. Collections are growable in nature that is based on our requirement we can increase or decrease the size.
2. Collections can hold both homogeneous & heterogeneous objects.
3. Every collection class is implemented based on some standard data structure hence for every requirement ready-made method support is available. being a programmer we are responsible to use those methods and we are not responsible to implement those methods.
## Difference between Arrays & Collections

| #   | Arrays                                                                                                                                                                                                         | Collections                                                                                                                                                                                                                                                      |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | Arrays are fixed in size that is once we create an array we can't increase or decrease the size based on our requirement.                                                                                      | Collections are growable in nature that is based on our requirement we can increase or decrease the size.                                                                                                                                                        |
| 2   | With respect to memory, arrays are not recommended to use.                                                                                                                                                     | With respect to memory, Collections are recommneded to use.                                                                                                                                                                                                      |
| 3   | With respect to performance, arrays are recommended to use.                                                                                                                                                    | With respect to performance, Collections are not recommneded to use.                                                                                                                                                                                             |
| 4   | Arrays can hold only homogenous data type elements.                                                                                                                                                            | Collections can hold both homogenous & heterogeneous element.                                                                                                                                                                                                    |
| 5   | There is no underlying data-structure for arrays and hence ready-made method support is not available.<br>For every requirement we have to write the code explicitly which increase complexity of programming. | Every Collection class is implemented based on some standard data structure and hence for every requirement ready-made method support is available.<br>Being a programmer we can use this method directly and we are not responsible to implement those methods. |
| 6   | Arrays can hold both primitves and objects.                                                                                                                                                                    | Collections can hold only objects types but not primitives.                                                                                                                                                                                                      |
## Collection
> If we want to represent a group of individual object as a single entity then we should go for Collection.
## Collection Framework
> It contains several classes and interfaces which can be used to represent a group of individual object as a single entity.

| Java                 | C++                                |
| -------------------- | ---------------------------------- |
| Collection           | Container                          |
| Collection Framework | STL<br>(Standard Template Library) |

> 9 Key interfaces are present inside Collection Framework.