# Call Traces

## Task 1: contains

### Trace A: contains(&[7, 12, 3], 3)

```
+----------------------------------------------+
| Call 3: contains(&[3], 3)                    |
| receives: [3], target 3                      |
| first item 3 == 3                            |
| returns: true                                |
+----------------------------------------------+
        | true
+----------------------------------------------+
| Call 2: contains(&[12, 3], 3)                |
| receives: [12, 3], target 3                  |
| 12 != 3, asks the rest                       |
| returns: contains(&[3], 3) = true            |
+----------------------------------------------+
        | true
+----------------------------------------------+
| Call 1: contains(&[7, 12, 3], 3)             |
| receives: [7, 12, 3], target 3               |
| 7 != 3, asks the rest                        |
| returns: contains(&[12, 3], 3) = true        |
+----------------------------------------------+
```

Calls: 3. Answer: **true**.

### Trace B: contains(&[7, 12, 3], 5)

```
+----------------------------------------------+
| Call 4: contains(&[], 5)                     |
| receives: [], target 5                       |
| base case (empty list)                       |
| returns: false                               |
+----------------------------------------------+
        | false
+----------------------------------------------+
| Call 3: contains(&[3], 5)                    |
| receives: [3], target 5                      |
| 3 != 5, asks the rest                        |
| returns: contains(&[], 5) = false            |
+----------------------------------------------+
        | false
+----------------------------------------------+
| Call 2: contains(&[12, 3], 5)                |
| receives: [12, 3], target 5                  |
| 12 != 5, asks the rest                       |
| returns: contains(&[3], 5) = false           |
+----------------------------------------------+
        | false
+----------------------------------------------+
| Call 1: contains(&[7, 12, 3], 5)             |
| receives: [7, 12, 3], target 5               |
| 7 != 5, asks the rest                        |
| returns: contains(&[12, 3], 5) = false       |
+----------------------------------------------+
```

Calls: 4. Answer: **false**.

## Task 6: all_distinct

### Trace C: all_distinct(&[4, 9, 4])

```
+----------------------------------------------+
| Call 1: all_distinct(&[4, 9, 4])             |
| receives: [4, 9, 4]                          |
| asks: contains(&[9, 4], 4) -> true           |
| returns: false                               |
+----------------------------------------------+
```

Calls: 1. Answer: **false**.

### Trace D: all_distinct(&[1, 2, 3])

```
+----------------------------------------------+
| Call 3: all_distinct(&[3])                   |
| receives: [3]                                |
| base case (one item)                         |
| returns: true                                |
+----------------------------------------------+
        | true
+----------------------------------------------+
| Call 2: all_distinct(&[2, 3])                |
| receives: [2, 3]                             |
| asks: contains(&[3], 2) -> false             |
| returns: all_distinct(&[3]) = true           |
+----------------------------------------------+
        | true
+----------------------------------------------+
| Call 1: all_distinct(&[1, 2, 3])             |
| receives: [1, 2, 3]                          |
| asks: contains(&[2, 3], 1) -> false          |
| returns: all_distinct(&[2, 3]) = true        |
+----------------------------------------------+
```

Calls: 3. Answer: **true**.






