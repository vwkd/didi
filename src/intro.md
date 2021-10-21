# Spec



## Intro

- code that defines string match
- code paths navigate the input string
- like being in the world of a string

- no flags/modifiers outside of regex, everything is defined within the code
- no variables since doesn't operate on any other data than input string
- can think of input string as variable that is implicitly assumed since since is the only one 

- expressions are compared to input string
- nested expressions are chained
<!-- todo: good idea? -->
- can think of eating up the input string
- a match is the total string at the end of a code path
<!-- todo: capture groups? -->

<!-- todo: start, middle, end? -->

- replaces regex multiline flag



## Values

### String

- literal expression

```
"hello"
```

- for character classes see Functions
- no escaping necessary, except for quotes themselves
- case-sensitive by default, can make case insensitive
<!-- todo: how to do it case insensitively? methods on object? would be hard for blocks. Function? Would look weird. -->

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
- replaces regex character classes
- can define own function as well

```
function date {
  digit(2) "." digit(2) "." digit(4)
}
```



## Loop

- multiple matches

```
loop every "\n" {

}

- replaces regex global flag



## Branch

- a code path
- like `if...else if` in programming language
<!-- todo: lookaheads? don't return whole match by default, instead use variables `if a = "hello" { a + "world" }`? -->

```
if "hello" {
  "world" 
}

if "hi" {
  "world" 
}
```

- replaces regex `|`
<!-- todo: introduces repetition into every branch instead of being confined to capture group? -->



## Module

- can import functions from third-party module

```
import mod { url, email }
```



## Comments

```
// a comment
```
