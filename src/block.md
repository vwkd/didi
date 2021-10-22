---
title: Block
index: 6
---
# Block



## Introduction

- reusable expression
- without arguments is used exactly once
- can give argument for repetition
<!-- todo: does this really cover all grouping functionality of regex? -->
- repetition allows to multiple matches in input string

```
{
  any (,)
  "hello" ;
  any (,)
} (,)
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

- can also match block

```
{
  "hel"
  "lo"
};
```



## Arguments

<!-- todo: find different way than argument, looks ugly -->
- defines repetition

```
{
  "hello"
}(3)
```

- can give sequence for variable repetition
- note, to make optional use sequence that includes `0`
- defaults to greedy
- can give optional second argument after sequence for ungreedy

```
{
  "hello"
} (1..3, ungreedy)
```

- replaces regex quantifiers `?`, `*`, `+`, `{3}`, `{3,}`, `{1,3}` 



## Variable

- can make block also a variable
- can reuse

```
date = {
  digit(2)
  "."
  digit(2)
  "."
  digit(4)
}
```

- can reuse block by name in matching expression any number of times
- built-in blocks, e.g. `any`, `anyButNewline`, `whitespace`, `digit`, `letter`, etc.
- replaces regex character classes, recurse (sub)pattern
