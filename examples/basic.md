# Examples



## Non-named match

- literal inside quotes, doesn't need escaping
- like regex non-named capture group, there is no match without a capture group
- start and end characters by default

```
"a";
```

```
^(a)$
```



## Named match

```
"a" @ m1;
```

```
^(?<m1>a)$
```



## Start and end

- `any ..` is at the beginning when wants to match at end

```
any ..
"a";
```

```
(a)$
```

- `any ..` is at the end when wants to match at beginning

```
"a";
any ..
```

```
^(a)
```

- works because block repetition is greedy by default, i.e. `any ..` eats as much of the input string as it can



## Multiple matches

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



## Non-capturing group

- IPv4 address

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
