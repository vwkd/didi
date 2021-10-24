---
title: Branching
index: 7
---
# Branching



## Introduction

- conditionally used string value
- creates a code path
- for multiple branches uses first one that works, short-circuit
- only ever one code path is used since since input string is consumed by it
- no "else" in favour of separate "if"s
- replaces regex lookahead, lookbehind, conditional statement, or, lookahead conditional, lookbehind conditional, etc.



## Condition

- boolean value
- use with string value and coercion
- beware: little use in using boolean value directly since doesn't depend on input string

```
- "hi" ? "hello"
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

- can use `&` for multiple conditions, must all be true
- beware: doesn't make sense to use literal strings in multiple conditions since needs to have some overlapping values, use character classes instead, e.g. `any ..`
- can create lookahead(s) using block(s) with character classes of varying repetition as condition(s), see Example
