# Call Traces

## Task 1: contains# Call Traces

## Task 1: contains

`contains(values, target)` answers: is `target` in the list?

### Trace A: contains(&[7, 12, 3], 3) (found at the end)

Newest call on top. Calls pile up going down the page; answers flow back up.

```
+-----------------------------------------------+
| Call 3: contains(&[3], 3)                     |
| receives: [3], target 3                       |
| list not empty; first item 3 == target 3      |
| returns: true                                 |
+-----------------------------------------------+
        | returns true to Call 2
+-----------------------------------------------+
| Call 2: contains(&[12, 3], 3)                 |
| receives: [12, 3], target 3                   |
| first item 12 != 3, so ask about the rest     |
|   -> contains(&[3], 3) (Call 3)               |
| returns: true (whatever Call 3 returned)      |
+-----------------------------------------------+
        | returns true to Call 1
+-----------------------------------------------+
| Call 1: contains(&[7, 12, 3], 3)              |
| receives: [7, 12, 3], target 3                |
| first item 7 != 3, so ask about the rest      |
|   -> contains(&[12, 3], 3) (Call 2)           |
| returns: true (whatever Call 2 returned)      |
+-----------------------------------------------+
```

Total calls: 3. Final answer: **true**.

### Trace B: contains(&[7, 12, 3], 5) (not found)

```
+-----------------------------------------------+
| Call 4: contains(&[], 5)                      |
| receives: [] (empty), target 5                |
| BASE CASE: an empty list contains nothing     |
| returns: false                                |
+-----------------------------------------------+
        | returns false to Call 3
+-----------------------------------------------+
| Call 3: contains(&[3], 5)                     |
| receives: [3], target 5                       |
| first item 3 != 5, so ask about the rest      |
|   -> contains(&[], 5) (Call 4)                |
| returns: false (whatever Call 4 returned)    |
+-----------------------------------------------+
        | returns false to Call 2
+-----------------------------------------------+
| Call 2: contains(&[12, 3], 5)                 |
| receives: [12, 3], target 5                   |
| first item 12 != 5, so ask about the rest     |
|   -> contains(&[3], 5) (Call 3)               |
| returns: false (whatever Call 3 returned)     |
+-----------------------------------------------+
        | returns false to Call 1
+-----------------------------------------------+
| Call 1: contains(&[7, 12, 3], 5)              |
| receives: [7, 12, 3], target 5                |
| first item 7 != 5, so ask about the rest      |
|   -> contains(&[12, 3], 5) (Call 2)           |
| returns: false (whatever Call 2 returned)     |
+-----------------------------------------------+
```

Total calls: 4. Final answer: **false**.

### Observations
- Each call receives a shorter list than the one that made it (the slice after the first item), so the calls always reach the base case.
- In Trace A the "first item is the target" check stops the recursion early. In Trace B nothing matches, so the calls go all the way down to the empty list.

`contains(values, target)` answers: is `target` in the list?

### Trace A: contains(&[7, 12, 3], 3) (found at the end)

Newest call on top. Calls pile up going down the page; answers flow back up.

```
+-----------------------------------------------+
| Call 3: contains(&[3], 3)                     |
| receives: [3], target 3                       |
| list not empty; first item 3 == target 3      |
| returns: true                                 |
+-----------------------------------------------+
        | returns true to Call 2
+-----------------------------------------------+
| Call 2: contains(&[12, 3], 3)                 |
| receives: [12, 3], target 3                   |
| first item 12 != 3, so ask about the rest     |
|   -> contains(&[3], 3) (Call 3)               |
| returns: true (whatever Call 3 returned)      |
+-----------------------------------------------+
        | returns true to Call 1
+-----------------------------------------------+
| Call 1: contains(&[7, 12, 3], 3)              |
| receives: [7, 12, 3], target 3                |
| first item 7 != 3, so ask about the rest      |
|   -> contains(&[12, 3], 3) (Call 2)           |
| returns: true (whatever Call 2 returned)      |
+-----------------------------------------------+
```

Total calls: 3. Final answer: **true**.

### Trace B: contains(&[7, 12, 3], 5) (not found)

```
+-----------------------------------------------+
| Call 4: contains(&[], 5)                      |
| receives: [] (empty), target 5                |
| BASE CASE: an empty list contains nothing     |
| returns: false                                |
+-----------------------------------------------+
        | returns false to Call 3
+-----------------------------------------------+
| Call 3: contains(&[3], 5)                     |
| receives: [3], target 5                       |
| first item 3 != 5, so ask about the rest      |
|   -> contains(&[], 5) (Call 4)                |
| returns: false (whatever Call 4 returned)    |
+-----------------------------------------------+
        | returns false to Call 2
+-----------------------------------------------+
| Call 2: contains(&[12, 3], 5)                 |
| receives: [12, 3], target 5                   |
| first item 12 != 5, so ask about the rest     |
|   -> contains(&[3], 5) (Call 3)               |
| returns: false (whatever Call 3 returned)     |
+-----------------------------------------------+
        | returns false to Call 1
+-----------------------------------------------+
| Call 1: contains(&[7, 12, 3], 5)              |
| receives: [7, 12, 3], target 5                |
| first item 7 != 5, so ask about the rest      |
|   -> contains(&[12, 3], 5) (Call 2)           |
| returns: false (whatever Call 2 returned)     |
+-----------------------------------------------+
```

Total calls: 4. Final answer: **false**.

### Observations
- Each call receives a shorter list than the one that made it (the slice after the first item), so the calls always reach the base case.
- In Trace A the "first item is the target" check stops the recursion early. In Trace B nothing matches, so the calls go all the way down to the empty list.
