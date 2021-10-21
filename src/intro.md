# Intro



## Intro

- string is the world in which navigates
- start from beginning of string
- eats it by writing strings
- no variables since doesn't have data



## Return

- returns the match
- like a capture group
- note, can return multiple times in different code paths unlike return in other languages

```
"hello" return
```

- can name, like a named capture group

```
"hello" return mygroup
```



## If else

- branching
- like or

```
if "hello" {
  return
} else if "world" {
  return
}
```

- no comparison since there are no variables

<!-- todo: would allow different names for capture groups? makes sense to have different names depending on content? -->



## Functions

- reusable components

```
function helloOrWorld {
  // logic here...
}
```

- execute by just using name
- no arguments, since doesn't pass data around
