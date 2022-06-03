---
title: Execution
index: 3
---

## Intro

```
"hello";
" ";
"world";
```

- writes strings
- string doesn't need escaping (except quotes)
- a string value is compared to beginning of input string, if equals then eats up that beginning of input string
- can think of implicit comparisons against input string
- starts from beginning to end of the input string
- language creates code paths that can navigate the input string
- can think of going through the world of the input string
- if no code path works out until the very end then breaks with error of no match
- can think of not having navigated the world of the input string correctly
- recommends to use separate line for each string for readability



## Non-match

- statement
- only eats up input string
- no equivalent in regex since always matches the whole
- beware: no implicit matching without a capture group ❗️

```
"a";
```

```
// except whole match, i.e. empty
^a$
```



## Match

- expression
- non-named match by default
- like regex non-named capture group

```
"a"
```

```
^(a)$
```

- select exactly matches that wants
- beware: doesn't return whole ❗️

```
"a";
"b"
"c";
```

```
// minus whole match, i.e. only "b"
^a(b)c$
```

- implementation must return collection since with capture groups can always have multiple matches, e.g. array
- code fully defines amount of matches, not different flags and modifiers on outside, engine has only single mode of execution

```
"hel";
"lo"
```

- replaces regex capture groups, non-capturing atomic groups

### Named match

- identifier of match in output
- like regex named capture group

```
"a" @ m1
```

```
^(?<m1>a)$
```

- replaces regex named capture groups
- implementation must return collection since can have multiple matches with same name, e.g. within repeated block



## Repetition

- shorthand for writing same string value(s) multiple times
- single match by default
- needs to opt-in into repetition explicitly
- replaces regex multiline flag `m`

```
"a" * 3
```

```
^(a)(a)(a)$
```

- beware: must come before identifier if named match ❗️

### Varying repetition

- range or sequence to choose amount of repetition from
- defaults to repeat as much as possible, "greedy"
- range

```
"a" * 1..3
```

```
^(a){1,3}$
```

- shorthand ranges for either end
- similar to regex

```
"a" * 1..
```

```
^(a){1,}
```

```
"a" * ..3
```

```
^(a){,3}
```

```
"a" * ..
```

```
^(a){,}
```

- sequence

```
"a" * [1 3 5]
```

- no equivalent in regex
- can make non-greedy

```
"a" *< 1..3;
```

- beware: no other shorthand for `1..` ❗️
- replaces regex quantifiers `?`, `+`, `{3}`, `{3,}`, `{1,3}`
- beware: doesn't make sense to specify non-greedy on fixed repetition, but allows anyways to make parsing simpler, just ignores it, treats as if hadn't specified non-greedy ❗️

#### Anywhere

- use `any` character class and varying repetition
- must explicitly navigate input string to only match something in middle
- opt-in to anywhere instead of opt-out
- `any * ..` at the beginning to match at end

```
any * ..;
"a"
```

```
(a)$
```

- `any * ..` at the end to match at beginning

```
"a"
any * ..;
```

```
^(a)
```

- `any * ..` at both the beginning and end to match in middle

```
any * ..;
"a"
any * ..;
```

```
(a)
```

- uses block repetition and greedy default, i.e. `any * ..` eats as much of the input string as it can
- replaces regex `^` and `$`

### Optional

- range or sequence that contains zero

```
"a" * 0..1;
```

- replaces regex quantifier `*`



## Coercion

- coerces string to boolean
- compares string value to input string until end
- if equals then resolves to boolean `true` otherwise `false`
- doesn't eat up input string
- only used in condition of branching