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
- case-sensitive by default
<!-- todo: how to make case insensitive? All combinations of case... Special block?
- replaces regex case insensitive flag `i`, localised inline modifiers `(?i:...)` -->



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
