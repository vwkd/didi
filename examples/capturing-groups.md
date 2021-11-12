---
title: Capturing Groups
index: 3
---
# Capturing groups



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
any ..;
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

- invalid regex

```
"foo";
any ..;
"bar"
```

```
^((?<=foo.*)bar)$
```