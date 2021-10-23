# Positive Lookahead



## Contains

```
^((?=foobar).+)$
```

```
hasFoobar ?
{
  any ..;
}

{
  any ..
  "foobar"
  any ..
} = hasFoobar
```



## Password

- at least 12 characters
- at least 1 uppercase letter
- at least 1 lowercase letter
- at least 1 number

```
^((?=.*[A-Z])(?=.*[a-z])(?=.*[0-9]).{12,})$
```

```
hasVariety ?
{
  any 12.. ;
}

{
  hasUppercase !
  hasLowercase !
  hasNumber !
} = hasVariety

{
  any ..
  Letter
  any ..
} = hasUppercase

{
  any ..
  letter
  any ..
} = hasLowercase

{
  any ..
  digit
  any ..
} = hasNumber
```
