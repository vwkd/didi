---
title: Variable
index: 5
---
# Variable



## Introduction

```
"hello" = h
```

- a reusable string value
- declare at beginning of file
- without a `;` since isn't part of matching logic
- implementation uses simple substitution
- like a named constant



## Named match

```
"hello" = h;
```

- name of match in output
- declare within matching logic
- with a `;` since is match
- has nothing to do with variable, can not reuse
- beware: completely different from reusable variable, just "happens to use" same syntax
- can also name variables

```
h = h;
```

- beware: seems circular when same name, but two very different things
- can not repeat string value with name, needs to wrap it in block and repeat that instead
- replaces regex named capture groups
- implementation must return collection since can have multiple matches with same name, e.g. within repeated block
