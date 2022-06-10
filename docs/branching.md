---
title: Branching
index: 7
---

## Introduction

- conditionally used string value
- creates a code path
- no "else" since is same as two consecutive "if"s since input string is consumed by code path that is used
- for multiple "if"s uses first one that works, short-circuit
- use nested "if"s to continue on a given code path instead of consecutive "if"s
- replaces regex lookahead, lookbehind, conditional statement, or, lookahead conditional, lookbehind conditional, etc.
- beware: engine needs to do two passes, first for condition, second for branch ❗️



## Condition

- boolean value
- use with string value and coercion
- beware: little use in using boolean value directly since doesn't depend on input string ❗️

```
! "hi" ? "hello";
```

- beware: a non-negated string literal value as condition makes little sense since can just match directly ❗️

```
"hello" ? "hello";
```

```
"hello";
```

```
"a" ? "a"
"b" ? "b"
```

```
^(a)|(b)$
```

- recommends to use variable for condition to make it more readable

```
! "hi" = notHi

notHi ? "hello";
```

- recommends to use block for string value to make it more readable

```
! "hi" = notHi

notHi ?
{
  "hello";
};
```



## Multiple conditions

- can use `&` for multiple conditions, must all be true
- beware: doesn't make sense to use literal strings in multiple conditions since needs to have some overlapping values, use character classes instead, e.g. `any * ..` ❗️
- can create lookahead using block with anywhere

```
{
  any * ..;
  "hello";
  any * ..;
} = hasHello;

hasHello ? any * ..
```

- beware: doesn't make sense to use block as condition whose contents are matches, but allows anyways to make parsing simpler, just ignores the matches, treats them as if they are no matches ❗️