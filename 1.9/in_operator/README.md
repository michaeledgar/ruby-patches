# Symbol List Syntax

**Author:** Michael Edgar  
**Date:** 7/9/2011

## What it does

This patch adds a simple syntax change to Ruby 1.9's grammar: the `in` operator, which
acts much like Python's. The following code is equivalent:

```
foo in bar
bar.include?(foo)
```

It is designed primarily to accommodate those who think of the potential element as the
focus of the "inclusion" predicate, and allows for a more natural expression of inclusion.

Read more about this potential syntax change in an epic Redmine thread:

http://redmine.ruby-lang.org/issues/show/3845