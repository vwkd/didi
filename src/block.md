---
title: Block
index: 6
---
# Block



## Introduction

- reusable group of string values
- by default is used exactly once just like without grouping it
- can repeat, see Arguments
<!-- todo: does this really cover all grouping functionality of regex? -->
- repetition allows for multiple matches in input string

```
{
  any ..
  "hello";
  any ..
} ..
```

- replaces regex global flag `g`
- separate syntax from capturing group, doesn't mix up like regex
- replaces non-capturing group



## Declaration

```
{
 "hel"
 "lo"
}
```

- can also match

```
{
  "hel"
  "lo"
};
```

- can also assign to variable for reuse

```
hello = {
  "hel"
  "lo"
}
```

- built-in blocks, e.g. `any`, `anyButNewline`, `whitespace`, `digit`, `letter`, etc.
- replaces regex character classes, recurse (sub)pattern



## Arguments

<!-- todo: allow it for string values in general? would also allow it for "hello", also clarify that purpose of block is logical grouping -->
- define repetition

```
{
  "hello"
} 3
```

- can give sequence for variable repetition
- note, to make optional use sequence that includes `0`
- defaults to greedy
- can give optional second argument after sequence for ungreedy

```
{
  "hello"
} 1..3 <
```

- replaces regex quantifiers `?`, `*`, `+`, `{3}`, `{3,}`, `{1,3}` 
