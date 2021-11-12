---
title: Conditions
index: 4
---
# Conditions



## Simple

```
"a" ? "a"
"b" ? "b"
```

```
^(a)|(b)$
```

- can also name it

```
^(?'aorb'a|b)$
```

```
{
  "a" ? "a";
  "b" ? "b";
} @ aorb
```
