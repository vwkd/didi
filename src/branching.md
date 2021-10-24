---
title: Branching
index: 7
---
# Branching



## Introduction

- code paths
- replaces regex lookahead, lookbehind, conditional statement, or



## Alternate

- conditionally used string value
- only one code path is used
- uses first one that works, short-circuit
- beware: no "else" branch since only ever one can be taken because input string is consumed by it
- condition is a string value
- compared to whole input string until end
- if equals then following string value is used
- doesn't eat up input string

```
-"hi" ? "hello"
```

- recommends to use variable for condition to make it more readable

```
- "hi" = notHi

notHi ? "hello"
```

- recommends to use block for string value to make it more readable

```
- "hi" = notHi

notHi ?
{
  "hello"
}
```

- beware: a non-negated string literal value as condition makes little sense since can just match directly

```
"hello" ? "hello"
```

```
"hello"
```

- can do lookahead using block with contents of varying repetition as condition, see Example



## Constraints

- in condition can use "and"
- all code paths are used
- compared to whole input string until end
- if equals then following string value is used
- doesn't eat up input string
- doesn't allow value since duplication
<!-- todo: better syntax to make constraint within condition instead of code itself -->
- can do multiple lookaheads, see Example


```
{
  b1 !
  b2 !
}

- beware: doesn't make sense with literal strings, needs to use with overlapping character classes like `any ..`
