---
title: Introduction
index: 1
---
# Introduction



## Non-match

- non-match by default
- only eats up input string for subsequent matches
- no equivalent in regex, always matches the whole

```
"a"
```

```
// except whole match, i.e. empty
^a$
```

- by default single match not multiple
- by default start and end not anywhere



## Match

- non-named match using ";"
- opt-in for match instead of opt-out
- string doesn't need escaping (except quotes)
- like regex non-named capture group
- beware: no implicit matching without a capture group

```
"a";
```

```
^(a)$
```

- select exactly matches that wants
- doesn't return whole
- no equivalent in regex, always matches the whole

```
"a"
"b";
"c"
```

```
// minus whole match, i.e. only "b"
^a(b)c$
```



## Named match

- named match
- like regex named capture group

```
"a" @ m1;
```

```
^(?<m1>a)$
```



## Start and end

- opt-in to anywhere instead of opt-out
- `any ..` at both the beginning and end to match in middle

```
any ..
"a";
any ..
```

```
(a)
```

- `any ..` at the beginning to match at end

```
any ..
"a";
```

```
(a)$
```

- `any ..` at the end to match at beginning

```
"a";
any ..
```

```
^(a)
```

- uses block repetition and greedy default, i.e. `any ..` eats as much of the input string as it can



## Repetition

- explicit repetition

```
"a" 3;
```

```
^(a)(a)(a)$
```

- ranges

```
"a" 1..3;
```

```
^(a){1,3}$
```

- shorthand ranges for either end
- similar to regex
- but no shorthand for `1..`

```
"a" .. ;
```

```
^(a)*
```
