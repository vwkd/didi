---
title: Variable
index: 5
---

## Introduction

- named constant value
- can't reassign, no computations
- has inferred type, no type annotations
- statically typed, can only be used where type can be used
- implementation uses simple substitution



## Declaration

```
"hello" = h;
1..10 = ten;
```

- at beginning of file
- not part of matching logic
- beware: must be statement ❗️
- beware: syntax is backwards from usual programming language ❗️



## Named match

- can also name match of variable
- beware: identifier of match can be same as of variable ❗️

```
"hello" = h;
h @ h
```