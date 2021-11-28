---
title: Basic
index: 1
---
<!-- todo: more examples -->

## Match

```
"hello world"
```

```
^(hello world)$
```



## Named match

```
"hello world" @ hw
```

```
^(?'hw'hello world)$
```



## Grouping

- e.g. IPv4 address

```
{
  {
    digit * 1..3;
    ".";
  } * 3;

  digit * 1..3;
}
```

```
^((?:\d{1,3}\.){3}\d{1,3})$
```



## Multiple matches

```
{
 any * ..;
 "a"
 any * ..;
} * ..;
```

```
(a)
```



## Followed by

```
"foo"
"bar";
```

```
^(foo(?=bar))$
```



## Ends in

```
"foo"
any * ..;
"bar";
```

```
^(foo(?=.*bar))$
```



## Preceeded by

```
"foo";
"bar"
```

```
^((?<=foo)bar)$
```



## Beginns in

<!-- todo: currently invalid regex?! -->

```
"foo";
any * ..;
"bar"
```

```
^((?<=foo.*)bar)$
```



## Contains

```
{
  any * ..;
  "foobar";
  any * ..;
} = hasFoobar;

hasFoobar ? any * ..
```

```
^((?=foobar).+)$
```



## Contains

<!-- todo: currently invalid regex?! -->

```
^(foo(?<=bar.*))$
```