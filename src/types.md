# Types



## String

```
"hello"
```

- no escaping necessary, except for quotes themselves
- case-sensitive by default
- methods that transform string

```
"hello".toUpperCase()
"hello world".toSnakeCase()
```

<!-- todo: how to make case insensitive? All combinations of case... Special block?
- replaces regex case insensitive flag `i`, localised inline modifiers `(?i:...)` -->



## Range

```
1..3
```

- only used in block argument
- if start is `0` can leave out

```
..3
```

- if end is `infinity` can leave out

```
1..
```

- methods to transform sequence

```
1...map(x => x * 2)
```

<!-- todo: interfering dots... -->
