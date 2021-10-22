# Examples



## Basics

```
"a";
```

```
^(a)$
```

- literal inside quotes, doesn't need escaping
- non-named match
- like regex non-named capture group, there is no match without a capture group
- start and end characters by default

```
"a" : "m1";
```

```
^(?<m1>a)$
```

- named capture group



## Start and end

```
any(,)
"a";
```

```
(a)$
```

- note, `any(,)` is at the beginning when wants to match at end

```
"a";
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
 "a";
 any(,)
} (,)
```

```
(a)
```



### Non-capturing group

- IPv4 address

```
((?:\d{1,3}\.){3}\d{1,3})
```

```
{
  {
    digit(1,3)
    "."
  } (3)
  digit(1,3)
} ;
```
