---
title: Block
index: 6
---

## Introduction

- grouping of string values
- different from matching, doesn't overload like regex capturing group
- can use matching and repetition on block
- replaces non-capturing group



## Declaration

```
{
 "hel";
 "lo";
};
```

- block itself is value, must be statement or expression
- can also match

```
{
  "hel";
  "lo";
}
```

- can also repeat

```
{
  "hel";
  "lo";
} * 3;
```

- can also assign to variable in advance for reuse

```
{
  "hel";
  "lo";
} = hello;
```

- built-in blocks for character classes, e.g. `any`, `anyButNewline`, `whitespace`, `digit`, `letter`, etc.
- replaces regex character classes, recurse (sub)pattern



## Multiple matches

- multiple matches in input string
- using repetition of block containg repeated built-in blocks

```
{
  any * ..;
  "hello"
  any * ..;
} * ..;
```

- replaces regex global flag `g`
- can specify repetition precisely, not just once or any

```
{
  any * ..;
  "hello"
  any * ..;
} * 3;
```