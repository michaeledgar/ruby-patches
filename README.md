ruby-patches: Customize Your Ruby!
==================================

`ruby-patches` is an easy way to implement, through `rvm`, patches to your Rubies.
This allows for a centralized repository where patches to Ruby go before they get merged into Ruby, if ever.
It also allows for specific changes that you'd like to see in your personal ruby implementation.
All patches are welcome, from a bug fix to new syntax changes, or even whole new language features!


Examples
--------

Ever wish you had a literal syntax for an array of symbols, like `%w()`? Kind of like this:

~~~ ruby
symbols = %S[foo bar baz]
  => [:foo, :bar, :baz]
~~~

There's a [patch for that](https://github.com/michaeledgar/ruby-patches/tree/master/1.9/symbol_list_syntax/) (courtesy of [Aaron Patterson](http://tenderlovemaking.com)).

What about Ruby 1.9's label syntax, but for quoted symbols and interpolation? Like this:

~~~ ruby
string = 'hello'
  => "hello"

hash = { foo: 1, 'bar-baz': 2, "#{x}-world": 3 }
  => {:foo => 1, :"bar-baz" => 2, :"hello-world" => 3}
~~~

There's a [patch for that](https://github.com/michaeledgar/ruby-patches/tree/master/1.9/quoted_labels/)!

Want to try out [Refinements](http://timelessrepo.com/refinements-in-ruby), a feature proposed for Ruby 2.0? [There's a patch for that, too!](https://github.com/michaeledgar/ruby-patches/tree/master/1.9/refinements/) (courtesy of Shugo Maeda)


Installing
----------

Want an easy way to use these patches? Use [rvm](http://rvm.beginrescueend.com/):

    rvm install 1.9.2-head --patch 1.9/optimized_require/by_ruby_core.diff -n newrubyname
    rvm install 1.9.2-head --patch 1.9/optimized_require/by_ruby_core.diff,1.9/quoted_labels/quoted_labels.diff -n newrubyname

Be sure to patch the correct interpreter for a given patch!
A tiny shell wrapper is in the works, too, just to make some mistakes harder to make.

Contributing
------------

Any Ruby implementation is fine - if you have a JRuby patch, submit away!
Here's what you do:

1. Think of a name for your patch and fork this repository: `symbol_list_syntax`
2. Make a directory with that name under the correct implementation: `mkdir 1.9/symbol_list_syntax/`
3. Copy the patch, with picked_name.diff as the file name: `cp -r (...) 1.9/symbol_list_syntax/symbol_list_syntax.diff`
4. Add a README.md file to the directory, describing the patch.
5. Send a pull request.

While I don't have any patches for some implementations as yet, the directory structure
is already set up. Which might be disappointing at first glance.

Past Contributors
-----------------

Special thanks to everyone on this list for making all these patches possible!

* Michael Edgar
* Aaron Patterson
* Xavier Shay
* Shugo Maeda
* Masaya Tarui
* Kurtis Rainbolt-Greene

Licensing
---------

All submitted patches are placed under the [MIT License](https://github.com/michaeledgar/ruby-patches/tree/master/LICENSE.txt). All submitted README.md documents are placed under [CC SA-BY 3.0](http://creativecommons.org/licenses/by-sa/3.0/). You
should assume these patches could do horrible things! I'll be looking over any patches to try to eliminate
actually malicious code, but one should assume danger lurks with a manually-patched language implementation.

On that note, have fun!