# Positive Lookahead



## Contains

```
^((?=foobar).+)$
```

```
hasFoobar ?
{
  any(,);
}

hasFoobar = {
  any(,)
  "foobar"
  any(,)
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
hasVariety ?
{
  any(12,);
}

hasVariety = {
  hasUppercase !
  hasLowercase !
  hasNumber !
}

hasUppercase = {
  any(,)
  Letter
  any(,)
}

hasLowercase = {
  any(,)
  letter
  any(,)
}

hasNumber = {
  any(,)
  digit
  any(,)
}
```
