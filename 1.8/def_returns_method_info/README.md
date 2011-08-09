# `def` returns method information

**Author:** 7trans, Peter Vanbroekhoven

## What it does

Patches the ruby source (v1.8.2, may work for other versions) such that defining a method in a module or class using def returns an Struct::MI object. This object holds the name and module/class of the method and can be used as parameters to methods like Module#private, Module#module_function, ....

```
irb(main):001:0> def m1
irb(main):002:1> end
=> #<struct Struct::MI module=Object, name=:m1>
irb(main):003:0> private def m2
irb(main):004:1> end
=> Object
irb(main):005:0> private def Object.m3
irb(main):006:1> end
=> Object
irb(main):007:0> mth = def m4
irb(main):008:1> end
=> #<struct Struct::MI module=Object, name=:m4>
irb(main):010:0> mth.name
=> :m4
irb(main):012:0> mth.module
=> Object
irb(main):013:0> smth = def Object.m5
irb(main):014:1> end
=> #<struct Struct::MI module=#, name=:m5>
irb(main):015:0> smth.module
=> #<Class:Object>
```