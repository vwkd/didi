# Spec



## Intro

- code that defines string match
- code paths navigate the input string
- can think of going through the world of the input string
- no variables since doesn't operate on any other data than input string
- can think of input string as variable that is implicitly assumed since since is the only one 
- no flags/modifiers outside of code like in regex, everything is defined by the code itself



## Syntax

- whitespace and new lines are insignificant



## Execution

- a string eats up the input string
- starts from beginning to end of the input string
- if no code path works out until the very end then breaks with error of no match
- can think of not having navigated the world of the input string correctly
- must explicitly navigate to match something in middle, see later Block using `any(,)`
- replaces regex multiline flag `m`
- for readability it is recommended to use a separate line for each string

```
"hel"
"lo"
```

- a string is returned as match if it's a statement
- by default no match, needs to opt-in instead of opt-out
- implementation must return collection since with capture groups can always have multiple matches, e.g. array
- code fully defines amount of matches, single engine mode, not different flags and modifiers on outside

```
"hel"
"lo";
```

- replaces regex capture groups, non-capturing atomic groups
- can give match a name

```
"hel":"m1";
```

- replaces regex named capture groups
- implementation must return collection since can have multiple matches with same name, e.g. within repeated block



## Types

### String

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

- methods to transform sequence

```
1...map(x => x * 2)
```

<!-- todo: interfering dots... -->



## Variable

```
h = "hello"
```

```
ten = 1..10
```

- can declare variable to reuse code
- has type, can only be used in proper position
- declaration must be after any matching
<!-- todo: how to differentiate matching from definitions? -->



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
} (3)
```

- can give sequence for variable repetition
- note, to make optional use sequence that includes `0`
- can give optional second argument after sequence for greedy/ungreedy, defaults to greedy

```
{
  "hello"
} (1..3, greedy)
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
  any (,)
  "hello" ;
  any (,)
} (,)
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



## Logic

- negation

```
!
```

- replaces regex negated character class



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
