# Intro



## Intro

- code paths navigate default string
- like single default variable, doesn't need to write since is the only data
- no variables since doesn't operate on any other data than default string
- start at beginning of default string
- writes strings to match
- can think of eating up the original string
- like in a world inside a string
- at end of a code path returns the match



## Return

- returns the match
- like a capture group
- note, can return multiple times in different code paths unlike return in other languages

```
"hello"
```

<!-- todo: capture group names -->



## If ... else if

- branching
- like or

```
if "hello" {
  
} else if "world" {
  
}
```

- no else since doesn't make sense, would be empty



## Functions

- reusable components

```
function helloOrWorld {
  // logic here...
}
```

- calls using two arguments for repetition

```
helloOrWorld(1,3)
```

- can leave of either argument, e.g. `fn(3,)` 3 or more times, `fn(,3)` zero times or at most 3 times
- built-in functions for character classes, e.g. `space`, `numbers`, `letters`, etc.
