# Block



## Grouping

- block only for grouping
- different from matching, doesn't overload
- unlike regex non-capturing group
- can use matching and repetition on block
- e.g. IPv4 address

```
^((?:\d{1,3}\.){3}\d{1,3})$
```

```
{
  {
    digit 1..3
    "."
  } 3
  digit 1..3
};
```



## Multiple matches

- repetition of block that contains repeated character classes

```
{
 any ..
 "a";
 any ..
} ..
```

```
(a)
```
