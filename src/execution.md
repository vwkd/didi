---
title: Execution
index: 3
---
# Execution



## Intro

- code paths navigate the input string
- can think of going through the world of the input string
- a string value is compared to beginning of input string, if equals then eats up that beginning of input string
- starts from beginning to end of the input string
- if no code path works out until the very end then breaks with error of no match
- can think of not having navigated the world of the input string correctly
- must explicitly navigate input string to only match something in middle, see later Block using `any ..`
- replaces regex multiline flag `m`



## Syntax

- recommends to use separate line for each string for readability

```
"hel"
"lo"
```

- can think of implicit comparisons against input string



## Match

- a statement
- expression is no match, needs to opt-in instead of opt-out
- implementation must return collection since with capture groups can always have multiple matches, e.g. array
- code fully defines amount of matches, not different flags and modifiers on outside, engine has only single mode of execution

```
"hel"
"lo";
```

- replaces regex capture groups, non-capturing atomic groups
- can give match a name

```
"hel":"m1";
```

- replaces regex named capture groups
- implementation must return collection since can have multiple matches with same name, e.g. within repeated block
