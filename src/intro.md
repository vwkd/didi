# Spec



## Intro

- code that defines string match
- code paths navigate the input string
- like being in the world of a string
- no variables since doesn't operate on any other data than input string
- can think of input string as variable that is implicitly assumed since since is the only one 
- no flags/modifiers outside of code like in regex, everything is defined by the code itself



## Syntax

- whitespace and new lines are insignificant



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
- replaces regex multiline flag `m`



## Match

- expression is matched only if it's declared as statement
- by default no match, needs to opt-in instead of opt-out
<!-- todo: should rather do opt-out like regex? -->

```
"hel"
"lo" ;
```

- can think of adding to results, doesn't "stop" the code path
- replaces regex capture groups, non-capturing atomic groups
- can give match a name

```
"hel" : "m1";
```

- replaces regex named capture groups
- named match must be implemented as a group, since can always return multiple matches, e.g. within repeated block



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

- can also match block

```
{
  "hel"
  "lo"
} ;
```

- return keyword can be on same or separate line
<!-- todo: does this really cover all grouping functionality of regex? -->
- without arguments is used exactly once
- can give argument for repetition

```
{
  "hello"
}(3)
```

- can give sequence for variable repetition
- note, to make optional use sequence that includes `0`
- can give optional second argument after sequence for greedy/ungreedy, defaults to greedy

```
{
  "hello"
}(1..3, greedy)
```

- replaces regex quantifiers `?`, `*`, `+`, `{3}`, `{3,}`, `{1,3}` 
- can declare named block at end of file after any matching expressions

```
date {
  digit(2) "." digit(2) "." digit(4)
}
```

- can reuse block by name in matching expression any number of times
- built-in blocks, e.g. `any`, `anyButNewline`, `whitespace`, `digit`, `letter`, etc.
- replaces regex character classes, recurse (sub)pattern
- block repetition allows to do multiple matches in input string

```
{
  any(,)
  "hello" ;
  any(,)
}(,)
```

- replaces regex global flag `g`



## Branch

- conditionally used block
- condition is compared with input string ahead without eating characters
- note, for a non-negated condition needs to repeat condition inside to continue branch, otherwise couldn't choose between using match or not

```
"hello" ?
{
  "hello" 
}
```

- block can start on same or separate line
- multiple branches using multiple `if`s, no "else" since can only ever take one branch since input string is consumed
<!-- todo: compute branches lazily as they are checked? -->
- replaces regex lookahead, lookbehind, conditional statement, or
- can still match whole block

```
"hello" ?
{
  "hello"
} ;
```




## Module

- can import blocks from third-party module
- promotes code reuse

```
use url, email from mod
```

<!-- todo: where to specify the modules? most portable from simple URL? -->

- can export block definitions

```
pub email {
  // definition...
}
```



## Comments

- comment in code

```
// a comment
```

- replaces regex comment group `(?#...)`
