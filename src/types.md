---
title: Types
index: 4
---
# Types



## String

```
"hello"
```

- no escaping necessary, except for quotes themselves
- case-sensitive
- can use either double quote, single quotes or backtick
- escape using backslash



## Number

```
1
```

- number
- only used in repetition argument



## Sequence

```
[1 2 3]
```

- set of numbers
- only used in repetition argument
- shorthand to create a range

```
1..3
```

- if start is `0` can leave out

```
..3
```

- if end is `infinity` can leave out

```
1..
```



## Boolean

```
true
```

- only used in branch condition
- automatically created from string value if it compares sucessfully to input string
- and operator

```
b1 & b2
```

- or operator

```
b1 | b2
```
