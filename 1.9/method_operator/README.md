# Method Operator: \\

**Author:** 7trans, Peter Vanbroekhoven, Ported to 1.9 by Michael Edgar

## What it does

Patches the ruby source (v1.9) such that it allows to grab methods from an object using a compact syntax:
```
  \class # => #<Method: Object(Kernel)#class>
  1\+ # => #<Method: Fixnum#+>
  "hello"\` # => #<Method: String(Kernel)#`>
  "hi"\class.class # => Method
  "hi"\class\type\class # => #<Method: Method(Kernel)#class>
```