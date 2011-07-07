# Symbol List Syntax

**Author:** Aaron Patterson  
**Date:** 7/6/2011

## What it does

This patch adds a simple syntax change to Ruby 1.9's grammar: a syntax for an array of symbols.

Much as you would use the following to create a list of strings:

```
words = %w(foo bar baz)  #=> ['foo', 'bar', 'baz']
```

With this patch, you can use the following syntax to create a list of symbols:

```
syms = %S(foo bar baz)  #=> [:foo, :bar, :baz]
```

The delimiter, of course, is up to you:

```
syms = %S[foo bar] + %S|baz qux|  #=> [:foo, :bar, :baz, :qux]
```