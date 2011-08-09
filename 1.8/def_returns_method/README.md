# `def` returns Method/UnboundMethod

**Author:** 7trans, Peter Vanbroekhoven, Nobuyoshi Nakada

## What it does

Patches the ruby source (v1.8.2, may work for other versions) such that defining a method in a module or class using def returns an UnboundMethod object, and defining a singleton method returns a Method. Thanks go to Nobuyoshi Nakada for helping with improving the patch.

```
irb(main):001:0> def a
irb(main):002:1> end
=> #<UnboundMethod: Object#a>
irb(main):003:0> class A
irb(main):004:1>   def m
irb(main):005:2>   end
irb(main):006:1> end
=> #<UnboundMethod: A#m>
irb(main):007:0> a = "hello"
=> "hello"
irb(main):008:0> def a.m
irb(main):009:1> end
=> #<Method: "hello".m>
irb(main):010:0> private def a
irb(main):011:1> end
=> Object
irb(main):012:0> self.class.private_instance_methods(false)
=> ["initialize", "irb_binding", "DelegateClass", "a"]
irb(main):013:0> alias b a
=> nil
irb(main):014:0> self.class.private_instance_methods(false)
=> ["b", "initialize", "irb_binding", "DelegateClass", "a"]
irb(main):015:0> m = self.class.instance_method(:a)
=> #<UnboundMethod: Object#a>
irb(main):016:0> public m
=> Object
irb(main):017:0> self.class.private_instance_methods(false)
=> ["b", "initialize", "irb_binding", "DelegateClass"]
irb(main):018:0> self.class.public_instance_methods(false)
=> ["a"]
irb(main):019:0> def a
irb(main):020:1> end
=> #<UnboundMethod: Object#a>
irb(main):021:0> private m
TypeError: method a in Object changed
        from (irb):21:in `private'
        from (irb):21
        from :0
irb(main):022:0> self.class.send(:undef_method, :a)
=> Object
irb(main):023:0> public m
TypeError: method a in Object disappeared
        from (irb):23:in `public'
        from (irb):23
        from :0
irb(main):024:0> m = String.instance_method(:each)
=> #<UnboundMethod: String#each>
irb(main):025:0> public m
TypeError: class mismatch - String for Object
        from (irb):25:in `public'
        from (irb):25
        from :0
```