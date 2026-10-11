# Comparison Table of `Set` Implemented Classes

| #   | Property                  | `HashSet`                                                                                              | `LinkedhashSet`         | `TreeSet` |
| --- | ------------------------- | ------------------------------------------------------------------------------------------------------ | ----------------------- | --------- |
| 1   | Underlying Data-Structure | Hash-table                                                                                             | LinkedList + Hash-Table | Bal       |
| 2   | Duplicate Objects         | Not Allowed                                                                                            | Not Allowed             |           |
| 3   | Insertion Order           | Not Preserved                                                                                          | Preserved               |           |
| 4   | Sorting Order             | Not Applicable                                                                                         | Not Applicable          |           |
| 5   | Heterogeneous Objects     | Allowed                                                                                                | Allowed                 |           |
| 6   | `null` acceptance         | Allowed For empty `TreeSet` as first element `null` is allowed. nwards  nwards  rsion.  eeSet`  eeSet` |                         |           |
>[!Note]
For empty `TreeSet` as the first element is allowed but this rule is applicable until Java-1.6 version. From Java-1.7 Version onwards `null` is not allwed even as the first element.
