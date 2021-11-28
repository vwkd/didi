---
title: Complex
index: 2
---

## Contains multiple

- e.g. password
- at least 12 characters
- at least 1 uppercase letter
- at least 1 lowercase letter
- at least 1 number

```
{
  any * ..;
  Letter;
  any * ..;
} = hasUppercase;

{
  any * ..;
  letter;
  any * ..;
} = hasLowercase;

{
  any * ..;
  digit;
  any * ..;
} = hasNumber;

hasUppercase & hasLowercase & hasNumber = hasVariety;

hasVariety ? any * 12..
```

```
^((?=.*[A-Z])(?=.*[a-z])(?=.*[0-9]).{12,})$
```