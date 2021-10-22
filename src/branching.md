---
title: Branching
index: 7
---
# Branching



## Introduction

- alternative
- conditionally used block
- creates a code path
- only one code path is used
- uses first one that works, short-circuit
- beware: no "else" branch since only ever one can be taken because input string is consumed by it



## Condition

- a string value
- compared to whole input string until end
- if equals then following block is used
- doesn't eat up input string
- beware: for non-negated condition needs to repeat it within block since didn't yet eat up input string

```
"hello" ?
{
  "hel";
}
```

- block can start on same or separate line
- can use variable of block as condition as well, necessary for more complex matches, see Example
<!-- todo: maybe not use variable? block is confusing at two places with different meaning -->
- in the block that's used in condition, can use "and" on other blocks within it

```
{
  b1 !
  b2 !
}

- like two branches that both must work
- beware: doesn't make sense with literal strings, needs to use with overlapping character classes like `any(,)`
- replaces regex lookahead, lookbehind, conditional statement, or
