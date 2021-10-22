# Capturing groups



## Followed by

```
^(foo(?=bar))$
```

```
"foo";
"bar"
```



## Ends in

```
^(foo(?=.*bar))$
```

```
"foo";
any(,)
"bar"
```



## Preceeded by

```
^((?<=foo)bar)$
```

```
"foo"
"bar";
```


## Beginns in

- invalid regex

```
^((?<=foo.*)bar)$
```

```
"foo"
any(,)
"bar";
```
