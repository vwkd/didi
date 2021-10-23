---
title: Block
index: 6
---
# Block



## Introduction

- grouping of string values
- separate syntax from capturing group, doesn't mix up like regex
- replaces non-capturing group
<!-- todo: does this really cover all grouping functionality of regex? -->



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

- can also repeat

```
{
  "hel"
  "lo"
} 3
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



## Multiple matches

- multiple matches in input string
- using repetition of block containg repeated built-in blocks

```
{
  any ..
  "hello";
  any ..
} ..
```

- replaces regex global flag `g`
