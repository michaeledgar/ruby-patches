# Any-Delimiter Quoted-Label Syntax

**Author:** Michael Edgar  

## What it does

This patch adds a syntax change to Ruby 1.9's grammar: quoted forms for hash-symbol-label
notation. The `{foo: bar} == {:foo => bar}` syntax is missing an analogue to quoted symbols,
and this patch adds it:

```
{'foo-bar': baz} == {:'foo-bar' => baz}
x = 'world'
{"hello-#{x}": baz} == {:"hello-#{x}" => baz}
```

Single quotes, as in the usual symbol syntax, do not permit interpolation. Double quotes do
permit interpolation. This patch also allows any other string delimiter:

```
{ %q@foo-bar@: baz } == { :'foo-bar' => baz }
{ %Q[hello-#{x}]: baz } == { :"hello-#{x}" => baz }
```

Have fun!