# Branching



## Introduction

- conditionally used block
- condition compares input string ahead without eating characters
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
- can match conditionally used block as well

```
"hello" ?
{
  "hello"
};
```
