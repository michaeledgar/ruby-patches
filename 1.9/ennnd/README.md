# en(n+)d keyword

**Author:** ko1? (Source: http://www.atdot.net/sp/raw/kn9iol)

## What it does

This patch adds a new form of the "end" keyword, en(n+)d. The number of n's
correspond to the number of blocks which are closed:

module Foo
  class Bar
    def initialize
      [1, 2, 3].each do |x|
        puts x
ennnnd

This could also be written as:

module Foo
  class Bar
    def initialize
      [1, 2, 3].each do |x|
        puts x
    ennd
ennd

Indentation does not matter - I've just used them here to show which blocks are
closed by which en(n+)d.