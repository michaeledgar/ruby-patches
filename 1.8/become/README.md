# become: object replacement

**Author:** 7trans, Peter Vanbroekhoven

## What it does

Adds a become method to Object which allows to replace every reference to the object by another object. However there is a catch id-wise (see below). It does not work for Fixnums, Symbols, true, false or nil. It does not work well for Strings (see below) and possibly other builtin types when the object which was passed as parameter to replace! is subsequently modified. Example:

class A
  attr_accessor :val
  def initialize(val)
    @val = val
  end
end

a = A.new("hello")
b = a
c = A.new("bye")
p a, a.id # => # , 537712366
p b, b.id # => # , 537712366
p c, c.id # => #   , 537712346
a.become(c)
p a, a.id # => #   , 537712366
p b, b.id # => #   , 537712366
p c, c.id # => #   , 537712346
a.val = "the end"
p a #       => #
p b #       => #
p c #       => #

a = "hello"
b = a
c = "bye"
p a, a.id # => "hello" , 537712076
p b, b.id # => "hello" , 537712076
p c, c.id # => "bye"   , 537712066
a.become(c)
p a, a.id # => "bye"   , 537712076
p b, b.id # => "bye"   , 537712076
p c, c.id # => "bye"   , 537712066
a.become("the end")
p a #       => "the end"
p b #       => "the end"
p c #       => "bye"
