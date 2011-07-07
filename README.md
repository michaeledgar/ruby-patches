# ruby-patches: Customize Your Ruby!

Ever wish you had a literal syntax for an array of symbols, like `%w()`? Kind of like this:

```
syms = %S[foo bar baz]  #=> syms == [:foo, :bar, :baz]
```

There's a [patch for that](https://github.com/michaeledgar/ruby-patches/tree/master/1.9/symbol_list_syntax/) (courtesy of [Aaron Patterson](http://tenderlovemaking.com)).

What about Ruby 1.9's label syntax, but for quoted symbols and interpolation? Like this:

```
x = 'hello'
{foo: 1, 'bar-baz': 2, "#{x}-world": 3}
```

There's a [patch for that](https://github.com/michaeledgar/ruby-patches/tree/master/1.9/quoted_labels/)!

Want to try out [Refinements](http://timelessrepo.com/refinements-in-ruby), a feature proposed for Ruby 2.0? [There's a patch for that, too!](https://github.com/michaeledgar/ruby-patches/tree/master/1.9/refinements/) (courtesy of Shugo Maeda)

Want an easy way to use these patches? Use [rvm](http://rvm.beginrescueend.com/):

    rvm install 1.9.2-head --patch example/foo.diff
    rvm install 1.9.2-head --patch example/foo.diff,example/bar.diff

## The Point of ruby-patches

I'd just like a central place where patches to Ruby go before they get merged into respective
projects. A GitHub repository makes as much sense as anything else to that end. Any patch is
welcome, be it a bug fix that hasn't landed yet, a random new syntax change, whole new language
features - whatever you like!

## Submitting a Patch

Any Ruby implementation is fine - if you have a JRuby patch, submit away! Here's what you do:

1. Fork this repository.
2. Pick a descriptive but not onerous name for your patch.
3. Add a directory with that name under the correct target implementation
4. Add your patch to that directory, with picked_name.diff as the filename.
5. Add at least a minimal README.md file to the directory, saying what the patch does. If you want to take credit for your patch, leave it here!
6. Send a pull request!

While I don't have any patches for some implementations as yet, the directory structure
is already set up. Which might be disappointing at first glance.

## Disclaimer/Legal Stuff

All submitted patches are placed under the [MIT License](https://github.com/michaeledgar/ruby-patches/tree/master/LICENSE.txt). All submitted README.md documents are placed under [CC SA-BY 3.0](http://creativecommons.org/licenses/by-sa/3.0/). You
should assume these patches could do horrible things! I'll be looking over any patches to try to eliminate
actually malicious code, but one should assume danger lurks with a manually-patched language implementation.

On that note, have fun!