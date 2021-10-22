# Spec



## Intro

- code that defines string match
- code paths navigate the input string
- like being in the world of a string
- no variables since doesn't operate on any other data than input string
- can think of input string as variable that is implicitly assumed since since is the only one 
- no flags/modifiers outside of code like in regex, everything is defined by the code itself



## Expressions

- the total expression of a code path is compared to the input string
- eats up input string

```
"hello"
```

- multiple expressions in new lines are added together

```
"hel"
"lo"
```

- always matches against whole string 
- must explicitly start and end code with `any(,)` to match in middle
- like regex `^.*hello.*$`
- replaces regex multiline flag
<!-- todo: how to do non-capturing, eating up without creating a match?



## Match

- expression is returned as match if it's given an identifier
- beware: identifier is not a variable, see Functions for variable-like functionality

```
m1 = "hel"
"lo"
```

```
m2 = {
  "hel"
  "lo"
}
```

- replaces regex capture groups
<!-- todo: does this really cover all grouping functionality of regex? -->
- implementation must always return possibly multiple matches, e.g. array



## Values

### String

- literal expression
- no escaping necessary, except for quotes themselves
- for character classes see Functions

```
"hello"
```

- case-sensitive by default
<!-- todo: how to do it case insensitively? methods on object? would be hard for blocks. Function? Would look weird. -->
- replaces regex case insensitive flag `i`, localised inline modifiers `(?i:...)`

### Range

- `x..y`
- only used in function argument



## Logic

- negate `!`



## Functions

- reusable expressions
<!-- todo: difference between branch and expression? -->
- without arguments is exactly once

```
digit
```

- can give argument for repetition

```
digit(3)
```

- can give sequence for variable repetition
- optional second argument for greedy/ungreedy, defaults to greedy

```
digit(1..3, greedy)
```

<!-- todo: allow user to define custom sequence, e.g. odd numbers, etc. would require full-blown programming language? -->
- like regex `?`, `*`, `+`, `{3}`, `{3,}`, `{1,3}` 
- built-in functions, e.g. `any`, `whitespace`, `digit`, `letter`, etc.
- replaces regex character classes, recurse (sub)pattern
- can define custom function

```
date = {
  digit(2) "." digit(2) "." digit(4)
}
```

- can define anonymous custom function that immediately executes, AIIFE

```
{
  "he"
  "lo"
}
```

- custom function allows multiple matches
- replaces regex global flag



## Branch

- a code path
- condition is compared with input string ahead without eating characters
- beware: no "else" since only ever one branch is taken for the consumed input string

```
if "hello"
{
  "world" 
}
```

- replaces regex lookahead, lookbehind, conditional statement, or
- for a non-negated condition needs to repeat condition inside to continue branch, necessary otherwise couldn't choose between using match or not, can use function to reuse code

```
if "a"
{
  "a"
}
if "b"
{
  "b"
}
```

- block can start on same line, in separate line just for readability



## Module

- can import functions from third-party module

```
import mod { url, email }
```



## Comments

- comment in code

```
// a comment

```

- replaces regex comment group `(?#...)`



## Misc

