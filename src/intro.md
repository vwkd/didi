# Intro



## Intro

- code paths navigate default string
- like single default variable, doesn't need to write since is the only data
- no variables since doesn't operate on any other data than default string
- writes strings to match
- can think of eating up the original string
- like in a world inside a string
- at end of a code path returns the whole match
<!-- todo: capture groups? -->

```
"hello"
```



## Branch

- a code path
- eats up that string
- like or in RegEx
- like if..elseif
<!-- todo: lookaheads? don't return whole match by default, instead use variables `if a = "hello" { a + "world" }`? -->

```
if "hello" {
  "world" 
}

if "hi" {
  "world" 
}
```

<!-- todo: introduces repetition into every branch -->



## Functions

- reusable components

```
function helloOrWorld {
  "hello" {}
  "world" {}
}
```

- calls using two arguments for repetition

```
helloOrWorld(1,3)
```

- can leave of either argument, e.g. `fn(3,)` 3 or more times, `fn(,3)` zero times or at most 3 times
- built-in functions for character classes, e.g. `space`, `numbers`, `letters`, etc.
