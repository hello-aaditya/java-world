# Stream (Java 8)
> if we want to process a group of objects from the collection then we should go for streams.

- A Stream helps us to process data in a functional way, so that programmers do not have to write repetitive code for data processing.
- A Stream closely work with **`Collection`**.
- A Stream **does not store data**.
- A Stream **does not modify the original collection** by itself.
- We can create as Stream object to the collection by using **`stream()`** method of Collection interface.
## Difference Between `Collection` and `Stream`

| if we want to represent a group of individual objects as a single entity then we should go for **Collection**. | if we want to process a group of objects from the collection then we should go for **Streams**. |
| -------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |

Example:
`Stream s = c.stream();`

```java
// consider there are 1 Million data stored inside List
List<String> cities = Arrays.asList(
"Agra", "Bengalore", "Chennai", "Hyderabad", "Ahemdabad", "Ajmer");

// 1. convert the collection to stream object
Stream<String> inputStream = cities.stream();
```
Stream is an interface present in `java.util.stream`.
Once we got the stream, by using that we can process objects of that collection.
Example:

