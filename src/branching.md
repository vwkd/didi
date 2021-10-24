---
title: Branching
index: 7
---
# Branching



## Introduction

- conditionally used string value
- creates code paths
- only one code path is used
- uses first one that works, short-circuit
- beware: no "else" branch since only ever one can be taken because input string is consumed by it
- replaces regex lookahead, lookbehind, conditional statement, or



## Condition

- boolean value
- there is little use in using a literal boolean value

```
true ? "hello"
```

- can use a string value as condition
- compared to input string until end
- if equals then resolves to boolean `true`
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

- can use `&` for multiple conditions that must all be true
- beware: doesn't make sense to use literal strings in multiple conditions since needs to have some overlapping values, e.g. `any ..`
- can create lookahead(s) using block(s) with character classes of varying repetition as condition(s), see Example
