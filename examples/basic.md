# Examples



## Basics

```
m1 = "a"
```

```
^(?<m1>a)$
```

- named capture group, no non-named capture group, no match without capture group
- start and end characters
- beware: will for simplicity use regex `a` as synonym for `(?<m1>a)` although it doesn't exist, similarly to `(a)`



## Start and end

```
any(,)
m1 = "a"
```

```
(?<m1>a)$
```

- note, `any(,)` is at the beginning when wants to match at end

```
m1 = "a"
any(,)
```

```
^(?<m1>a)
```

- note, `any(,)` is at the end when wants to match at beginning
- works because character classes are greedy by default



## Multiple matches

```
{
 any(,)
 m1 = "a"
 any(,)
}(,)
```

```
(?<m1>a)
```

<!-- todo: name makes no sense if multiple? -->



## Branching

```
^(?<m1>a|b)$
```

```
m1 = {
  if "a" {
    "a"
  }

  if "b" {
    "b"
  }
}
```

- doesn't exist for missing start and/or end characters, or missing named capture group



### Match everything enclosed

- IPv4 address

```
/(?:\d{1,3}\.){3}\d{1,3}/
```

```
{
  digit(1,3)
  "."
}(3)
digit(1,3)
```

<!-- todo: missing identifier -->
