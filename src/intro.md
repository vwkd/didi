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



## Match

- expression is matched if it's given an identifier
- doesn't match by default, needs to opt-in instead of opt-out
- implementation must always return possibly multiple matches, e.g. array

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

- beware: identifier is not a variable, see Block for variable-like functionality
<!-- todo: name makes no sense if within repeated block since can match multiple times... -->
- replaces regex capture groups, non-capturing atomic groups
<!-- todo: does this really cover all grouping functionality of regex? -->



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

<!-- todo: allow user to define custom sequence, e.g. odd numbers, etc. would require full-blown programming language? -->



## Logic

- negation

```
!
```

- replaces regex negated character class



## Block

- reusable expression

```
{
 "hel"
 "lo"
}
```

- without arguments is used exactly once

```
digit
```

- can give argument for repetition

```
digit(3)
```

- can give sequence for variable repetition
- note, to make optional use sequence that includes `0`
- if sequence is used can give optional second argument for greedy/ungreedy, defaults to greedy

```
digit(1..3, greedy)
```

- like regex `?`, `*`, `+`, `{3}`, `{3,}`, `{1,3}` 
- built-in blocks, e.g. `any`, `whitespace`, `digit`, `letter`, etc.
- replaces regex character classes, recurse (sub)pattern
- like loop in programming language
- can define named block at end of file after any matching expressions

```
date {
  digit(2) "." digit(2) "." digit(4)
}
```

<!-- todo: multiple matches anywhere in string? can't just use block since requires knowledge of structure... can't just repeat whole thing because fixes start and end
- replaces regex global flag
-->



## Branch

- conditionally used block
- condition is compared with input string ahead without eating characters
- beware: no "else" since only ever one branch is taken for the consumed input string

```
if "hello"
{
  "hello" 
}
```

- block can start on same or separate line
- can also match

```
if "hello"
m1 = {
  "hello"
}
```

<!-- todo: needs to wrap in block to match the whole, e.g. `(a|b)`? -->
- replaces regex lookahead, lookbehind, conditional statement, or
- note, for a non-negated condition needs to repeat condition inside to continue branch, otherwise couldn't choose between using match or not



## Module

- can import blocks from third-party module
- promotes code reuse

```
import mod { url, email }
```



## Comments

- comment in code

```
// a comment
```

- replaces regex comment group `(?#...)`
