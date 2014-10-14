## Anonymous Functions

### Functions and Pattern Matching

```
list_concat = fn a, b -> a ++ b end

sum = fn a, b, c -> a + b + c end

pair_tuple_to_list = fn {a, b} -> [a, b] end
```

Elixir doesn't have assigment. Instead, it tries to match values and patterns.

### One Function, Multiple Bodies

### Functions Can Return Functions

```
fun1 = fn ->
         fn ->
           "Hello"
         end
       end
```

#### Functions Remember Their Original Environment

### The & Notation
```
&(&1 + &2) => fn p1, p2 -> p1 + p2
&byte_size(&1) => fn p1 -> byte_size(p1)
```

The & shortcut gives us a wonderful way to pass functions to other functions.

```
Enum.map [1,2,3,4], &(&1 + 1) => [2,3,4,5]
```