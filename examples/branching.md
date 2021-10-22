# Branching



## Simple

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

```
^(a)|(b)$
```

- can also name the whole thing

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

```
^(a|b)$
```
