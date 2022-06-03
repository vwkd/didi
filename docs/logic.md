---
title: Logic
index: 8
---

## Introduction

- also works with variables and blocks



## Negation

```
! "hello";
```

- compares to input string with "not equal" instead of "equal"
- replaces regex negated character class `[^...]`
- can think of allowing all code paths except this one



## Case insensitivity

```
~ "hello";
```

- compares to input string case insensitively
- replaces regex case insensitive flag `i`, localised inline modifiers `(?i:...)`
- can think of allowing multiple code paths for every combination of uppercase and lowercase letters
