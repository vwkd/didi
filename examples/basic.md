# Examples



## Basics

```
"a" return
```

```
^(a)$
```

- non-named capture group
- can't match without capture group
- start and end characters by default

```
"a" return m1
```

```
^(?<m1>a)$
```

- named capture group



## Start and end

```
any(,)
"a" return
```

```
(a)$
```

- note, `any(,)` is at the beginning when wants to match at end

```
"a" return
any(,)
```

```
^(a)
```

- note, `any(,)` is at the end when wants to match at beginning
- works because block repetition is greedy by default, i.e. `any(,)` eats as much of the input string as it can



## Multiple matches

```
{
 any(,)
 "a" return
 any(,)
}(,)
```

```
(a)
```



## Branching

```
if "a"
{
  "a" return
}
if "b"
{
  "b" return
}
```

```
^(a)|(b)$
```

- can also name the whole thing

```
{
  if "a" {
    "a"
  }

  if "b" {
    "b"
  }
} return
```

```
^(a|b)$
```



### Match everything enclosed

- IPv4 address

```
((?:\d{1,3}\.){3}\d{1,3})
```

```
{
  {
    digit(1,3)
    "."
  }(3)
  digit(1,3)
} return
```
