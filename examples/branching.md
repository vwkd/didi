---
title: Conditions
index: 4
---
# Conditions



## Simple

```
^(a)|(b)$
```

```
"a" ?
{
  "a";
}

"b" ?
{
  "b";
}
```

- can also name the whole thing

```
^(a|b)$
```

```
{
  "a" ?
  {
    "a"
  }

  "b" ?
  {
    "b"
  }
};
```
