---
title: Variable
index: 5
---
# Variable



## Introduction

```
"hello" = h
```

- can declare variable to reuse string value
- can only use later, not before
- implementation uses simple substitution
- can not also repeat, needs to wrap in block and repeat that instead



## Named match

```
"hello" = h;
```

- can give match a name
- replaces regex named capture groups
- implementation must return collection since can have multiple matches with same name, e.g. within repeated block
- beware: can't name match without using a variable that could also be reused internally, fair tradeoff for not needing two ways to assign identifier since no need for encapsulation
