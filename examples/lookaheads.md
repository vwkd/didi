# Positive Lookahead



## Contains

- condition is block with character classes of varying repetition

```
^((?=foobar).+)$
```

```
{
  any ..
  "foobar"
  any ..
} = hasFoobar

hasFoobar ?
{
  any .. ;
}
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

hasUppercase & hasLowercase & hasNumber = hasVariety

hasVariety ?
{
  any 12.. ;
}
```
